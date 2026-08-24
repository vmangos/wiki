# Getting it Working (Linux)

Once you've compiled the server core, there are still a number of steps you must go through before being able to start your server.

**Important:** Before running any of the commands below, it is recommended to start a **bash session** to ensure compatibility.
Enter bash by typing:
```bash
bash
```
If you are already in bash, you can skip this. When you are done, you can exit the bash session at any time by typing `exit`.

## 1. Extracting data from the client

The server requires a large amount of data from the client in order to operate. That includes DBC, Map, VMap and MMap files. To extract all that data you need extractors. You can compile them yourself by selecting the `_USE_EXTRACTORS_` option when configuring in CMake. Alternatively you can download the required files from the internet.

### Extracting data from client on Linux

1. **Locate your WoW 1.12.1 client folder**
   Verify it's build **5875** (bottom-left corner of the login screen).
   Assume your client is installed at `/home/yourname/games/World of Warcraft` - adjust the path accordingly.

2. **Set your WoW path** (edit once)

   ```bash
   WOW_PATH='/home/yourname/games/World of Warcraft'
   ```
   Change it to your actual path.

3. **Run extraction (separate commands - run in order)**

   Create the target data directory:
   ```bash
   mkdir -p ~/vmangos/data/5875
   cd ~/vmangos/data
   ```

   Extract maps and DBC:
   ```bash
   ~/vmangos/bin/Extractors/MapExtractor -i "$WOW_PATH" -o ~/vmangos/data -e 7
   ```

   Move the DBC folder into the version-specific subdirectory:
   ```bash
   mv ~/vmangos/data/dbc ~/vmangos/data/5875/dbc
   ```

   Extract raw vmap data:
   ```bash
   ~/vmangos/bin/Extractors/VMapExtractor -d "$WOW_PATH/Data"
   ```

   Build final vmaps:
   ```bash
   ~/vmangos/bin/Extractors/VMapAssembler
   ```

   Generate movement maps (adjust thread count automatically):
   ```bash
   ~/vmangos/bin/Extractors/MoveMapGenerator --threads "$(nproc)" --silent --configInputPath ~/vmangos/bin/Extractors/config.json --offMeshInput ~/vmangos/bin/Extractors/offmesh.txt
   ```

   Clean up unused folders:
   ```bash
   rm -rf ~/vmangos/data/{Buildings,Cameras}
   ```

4. **Final structure**

   ```
   ~/vmangos/data/
   ├── 5875/dbc/
   ├── maps/
   ├── vmaps/
   └── mmaps/
   ```

---

## 2. Setting up the database

The server requires a MariaDB (or MySQL) database to store all account, character, and world data.

### Set username and password for DB (to reuse in following steps)

We'll use the default `mangos`/`mangos` expected by the server configuration files. If you change them, remember to update the configs later.

```bash
read -p "Database user [mangos]: " DB_USER; DB_USER=${DB_USER:-mangos}
read -sp "Database password [mangos]: " DB_PASS; echo; DB_PASS=${DB_PASS:-mangos}
```

### Create databases and user

```bash
mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS realmd DEFAULT CHARSET utf8 COLLATE utf8_general_ci; CREATE DATABASE IF NOT EXISTS mangos DEFAULT CHARSET utf8 COLLATE utf8_general_ci; CREATE DATABASE IF NOT EXISTS characters DEFAULT CHARSET utf8 COLLATE utf8_general_ci; CREATE DATABASE IF NOT EXISTS logs DEFAULT CHARSET utf8 COLLATE utf8_general_ci; CREATE USER IF NOT EXISTS '${DB_USER}'@'localhost' IDENTIFIED BY '${DB_PASS}'; GRANT ALL PRIVILEGES ON realmd.* TO '${DB_USER}'@'localhost'; GRANT ALL PRIVILEGES ON mangos.* TO '${DB_USER}'@'localhost'; GRANT ALL PRIVILEGES ON characters.* TO '${DB_USER}'@'localhost'; GRANT ALL PRIVILEGES ON logs.* TO '${DB_USER}'@'localhost'; FLUSH PRIVILEGES;"
```
*You will be prompted for the MySQL root password.*

### Importing the database

You have two options: import a fully updated database (recommended) or import the latest release and then apply migrations separately.

#### Option A: Import the latest database with migrations pre-applied (fast)

```bash
ZIP_URL=$(curl -s https://api.github.com/repos/vmangos/core/releases/tags/db_latest | grep -o '"name": "db-[0-9a-f]*\.zip"' | sed 's/"name": "\([^"]*\)"/\1/' | head -n1 | sed 's|^|https://github.com/vmangos/core/releases/download/db_latest/|') && wget -qO /tmp/db-latest.zip "$ZIP_URL" && 7z x /tmp/db-latest.zip -o/tmp/ -y && mysql -u"${DB_USER}" -p"${DB_PASS}" --max-allowed-packet=256M realmd < /tmp/mysql-dump/logon.sql && mysql -u"${DB_USER}" -p"${DB_PASS}" --max-allowed-packet=256M characters < /tmp/mysql-dump/characters.sql && mysql -u"${DB_USER}" -p"${DB_PASS}" --max-allowed-packet=256M mangos < /tmp/mysql-dump/mangos.sql && mysql -u"${DB_USER}" -p"${DB_PASS}" --max-allowed-packet=256M logs < /tmp/mysql-dump/logs.sql
```

After this, you can skip to **Step 3**.

#### Option B: Import the latest database release and apply migrations separately

1. **Get the latest world database file**

   ```bash
   LATEST_DB=$(curl -s https://api.github.com/repos/brotalnia/database/contents/ | grep -o '"name": "world_full_[^"]*\.7z"' | sed 's/"name": "\(.*\)"/\1/' | while read f; do date_part=$(echo "$f" | sed 's/world_full_\(.*\)\.7z/\1/'); echo "$(date -d "$(echo "$date_part" | sed 's/_/ /g')" +%s 2>/dev/null) $f"; done | sort -n | tail -n1 | cut -d' ' -f2-) && wget -qO "/tmp/$LATEST_DB" "https://github.com/brotalnia/database/raw/master/$LATEST_DB"
   ```

2. **Extract the database**

   ```bash
   7z x "/tmp/$LATEST_DB" -o/tmp/ -y
   ```

3. **Import the base world database**

   ```bash
   mysql -u"${DB_USER}" -p"${DB_PASS}" mangos < "/tmp/$(basename "$LATEST_DB" .7z).sql"
   ```

4. **Run the VMaNGOS migration merge script**

   ```bash
   cd ~/vmangos/core/sql/migrations && ./merge.sh
   ```
   This generates combined update files like `world_db_updates.sql`, `logs_db_updates.sql`, etc., in the same directory.

5. **Import the core SQL files (logs, logon, characters)**

   ```bash
   mysql -u"${DB_USER}" -p"${DB_PASS}" logs < ~/vmangos/core/sql/logs.sql
   mysql -u"${DB_USER}" -p"${DB_PASS}" realmd < ~/vmangos/core/sql/logon.sql
   mysql -u"${DB_USER}" -p"${DB_PASS}" characters < ~/vmangos/core/sql/characters.sql
   ```

6. **Import the merged migration files**

   ```bash
   mysql -u"${DB_USER}" -p"${DB_PASS}" mangos < ~/vmangos/core/sql/migrations/world_db_updates.sql
   mysql -u"${DB_USER}" -p"${DB_PASS}" logs < ~/vmangos/core/sql/migrations/logs_db_updates.sql
   mysql -u"${DB_USER}" -p"${DB_PASS}" realmd < ~/vmangos/core/sql/migrations/logon_db_updates.sql
   mysql -u"${DB_USER}" -p"${DB_PASS}" characters < ~/vmangos/core/sql/migrations/characters_db_updates.sql
   ```

---

## 3. Editing the configuration files

Copy the distributed configuration templates and adjust them.

```bash
mkdir -p ~/vmangos/logs
cp ~/vmangos/etc/mangosd.conf.dist ~/vmangos/etc/mangosd.conf
cp ~/vmangos/etc/realmd.conf.dist ~/vmangos/etc/realmd.conf
```

Set the data and logs directories (using `sed` or a text editor):

```bash
sed -i "s|^DataDir.*|DataDir = \"../data\"|" ~/vmangos/etc/mangosd.conf
sed -i "s|^LogsDir.*|LogsDir = \"../logs\"|" ~/vmangos/etc/mangosd.conf
sed -i "s|^LogsDir.*|LogsDir = \"../logs\"|" ~/vmangos/etc/realmd.conf
```

**Important:** Now open `~/vmangos/etc/mangosd.conf` and `~/vmangos/etc/realmd.conf` in a text editor (e.g., `nano`, `vim`) and verify the database connection strings. The default entries look like:

```
LoginDatabase.Info    = "127.0.0.1;3306;mangos;mangos;realmd"
WorldDatabase.Info    = "127.0.0.1;3306;mangos;mangos;mangos"
CharacterDatabase.Info = "127.0.0.1;3306;mangos;mangos;characters"
LogsDatabase.Info      = "127.0.0.1;3306;mangos;mangos;logs"
```

If you used a different MySQL username or password during database setup, replace the `mangos;mangos` part accordingly.

---

## 4. Add your realm to the database

Insert a record for your realm into the [`realmlist`](realmd/realmlist.md) table of the `realmd` database:

```bash
mysql -u"${DB_USER}" -p"${DB_PASS}" -e "USE realmd; INSERT INTO realmlist (id, name, address, port, icon, realmflags, timezone, allowedSecurityLevel, population, gamebuild_min, gamebuild_max, flag) VALUES (1, 'VMaNGOS', '127.0.0.1', 8085, 1, 0, 1, 0, 0, 5875, 5875, 0);"
```

Change `'VMaNGOS'` and `'127.0.0.1'` to your desired realm name and public IP if needed.

---

## 5. Starting your server

Make sure your MySQL server is running.

### Start manually in two terminals

**Terminal 1 - Realm server**
```bash
cd ~/vmangos/bin && ./realmd
```

**Terminal 2 - World server**
```bash
cd ~/vmangos/bin && ./mangosd
```

### Optional: Keep servers running with `screen`

```bash
screen -dmS realmd bash -c "cd ~/vmangos/bin && ./realmd"
screen -dmS mangosd bash -c "cd ~/vmangos/bin && ./mangosd"
```
Reattach with `screen -r realmd` or `screen -r mangosd`.

### Optional: Keep servers running with `tmux`

```bash
tmux new -d -s realmd 'cd ~/vmangos/bin && ./realmd'
tmux new -d -s mangosd 'cd ~/vmangos/bin && ./mangosd'
```
Reattach with `tmux a -t realmd` or `tmux a -t mangosd`.

---

## 6. Creating an admin account

Once `mangosd` is running, type the following commands in its console:

```
account create admin admin
account set gmlevel admin 6
```

This creates an account with username `admin` and password `admin`, and grants it full administrator privileges.

---

## 7. Connecting with the client

1. In your World of Warcraft 1.12.1 folder, open the `realmlist.wtf` file with a text editor.
2. Replace its content with:
   ```
   set realmlist 127.0.0.1
   ```
   (If your server is on a different machine, use that machine's IP address.)
3. Save the file.

Launch the game and login with the account you just created.
