Once you've compiled the server core, there are still a number of steps you must go through before being able to start your server.

## 1. Extracting data from the client

The server requires a large amount of data from the client in order to operate. That includes DBC, Map, VMap and MMap files. To extract all that data you need extractors. You can compile them yourself by selecting the `_USE_EXTRACTORS_` option when configuring in CMake. Alternatively you can download all the required files from the internet.

### Extracting data from client on Windows

1. **Locate your WoW 1.12.1 client folder**  
   Verify it's build **5875** (bottom‑left corner of the login screen).

2. **Copy the extractors and dependencies**  
   Place these files in your World of Warcraft 1.12.1 game folder:  
   - `mapextractor.exe`  
   - `vmapextractor.exe`  
   - `vmap_assembler.exe`  
   - `MoveMapGen.exe`  
   - Any required DLLs from the build output.

3. **Run the extractors by double‑clicking (in order)**  
   Open the WoW folder in File Explorer and double‑click each one:

   1. **`mapextractor.exe`** – extracts DBC and map files.
   2. **`vmapextractor.exe`** – extracts raw visual map files.
   3. **`vmap_assembler.exe`** – converts the vmaps into a usable format.
   4. **`MoveMapGen.exe`** – generates movement maps (optional, but recommended for proper creature navigation).  
      *This step takes a long time – from 30 minutes to several hours. If you skip it, mobs will chase targets in a straight line and fear movement will not work. If you get an error about a missing "mmaps" folder, just create it manually.*

4. **Move extracted folders to your server**  
   Copy the following folders from your WoW folder: `maps`, `vmaps`, `mmaps` (if created), `dbc`  
   Paste them into your server data directory (e.g., `C:\vmangos\data\`).

5. **Organize DBC for build 5875**  
   Rename or move the `dbc` folder so it becomes `5875\dbc` inside your data directory.  
   Example final path: `C:\vmangos\data\5875\dbc\`  
   *The build number of the 1.12.1 client is 5875.*

6. **Cleanup**  
   Delete the `Buildings\` and `Cameras\` folders (if present) from your WoW folder.

---

## 2. Setting up the database

The server requires a MySQL database to store all account, character, and world data.

### Installing MySQL on Windows

- Download the official [MySQL Installer (5.5 or 5.6)](https://dev.mysql.com/downloads/mysql/5.5.html) or use [XAMPP](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/5.6.12/) which provides a ready‑to‑use package of MySQL and Apache.  
  *Version 5.7 may work but some users have reported issues.*

### Creating the databases and a dedicated user

You need to create four databases and a database user that the server will use to connect. The default username and password expected by the server configuration files are **`mangos` / `mangos`**. If you prefer different credentials, remember to update the configuration files later.

#### If you are using a GUI tool (MySQL Workbench, phpMyAdmin, HeidiSQL, etc.):
- Create the following databases:
  - `realmd`
  - `mangos`
  - `characters`
  - `logs`
  
  (For collation put `utf8_general_ci`.)

  - Create a user `mangos` with password `mangos` and grant it all privileges on all four databases above.

#### If you are using the MySQL command line:
Run the following SQL commands (you can copy and paste them into the mysql prompt after connecting as root):

```sql
CREATE DATABASE IF NOT EXISTS realmd DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
CREATE DATABASE IF NOT EXISTS mangos DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
CREATE DATABASE IF NOT EXISTS characters DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
CREATE DATABASE IF NOT EXISTS logs DEFAULT CHARSET utf8 COLLATE utf8_general_ci;

CREATE USER IF NOT EXISTS 'mangos'@'localhost' IDENTIFIED BY 'mangos';
GRANT ALL PRIVILEGES ON realmd.* TO 'mangos'@'localhost';
GRANT ALL PRIVILEGES ON mangos.* TO 'mangos'@'localhost';
GRANT ALL PRIVILEGES ON characters.* TO 'mangos'@'localhost';
GRANT ALL PRIVILEGES ON logs.* TO 'mangos'@'localhost';
FLUSH PRIVILEGES;
```

After running these commands, you will have the required databases and a user `mangos` with password `mangos`.

### Importing the database structure and content

You need four SQL files:

- `logs.sql` – creates the `logs` database tables. *(Located in your core's `sql` folder)*
- `logon.sql` – creates the `realmd` database tables. *(Located in your core's `sql` folder)*
- `characters.sql` – creates the `characters` database tables. *(Located in your core's `sql` folder)*
- The world database – you must obtain the latest world database release from the [database repository](https://github.com/brotalnia/database). Download the most recent `.7z` file (e.g., `world_full_YYYY_MM_DD.7z`) and extract it to get a `.sql` file.

You can find the first three SQL files in the `sql` directory of your source (e.g., `C:\vmangos\core\sql\`).

Import these files using a GUI tool or the MySQL command line.

#### Using the command line

Run these commands from a Command Prompt (adjust file paths to your actual locations). You will be prompted for the `mangos` user's password each time (default is `mangos`).

```bash
mysql -u mangos -p mangos < "C:\path\to\world_full_YYYY_MM_DD.sql"
mysql -u mangos -p logs < "C:\path\to\logs.sql"
mysql -u mangos -p realmd < "C:\path\to\logon.sql"
mysql -u mangos -p characters < "C:\path\to\characters.sql"
```

#### Using a GUI client

- In GUI mysql client, choose the option to import from a SQL file.  
- For each `.sql` file, select the target database and run the import.

### Applying database migrations

After the initial import, you must apply any pending updates (migrations). These are located in `sql\migrations` inside your core repository. For your convenience, there is a batch script that can merge all migrations into a single file for each database. Run the `merge.bat` script to generate combined update files, then import them using the same method as above or import them using a MySQL GUI client:

```bash
mysql -u mangos -p mangos < world_db_updates.sql
mysql -u mangos -p logs < logs_db_updates.sql
mysql -u mangos -p realmd < logon_db_updates.sql
mysql -u mangos -p characters < characters_db_updates.sql
```

If you skip this step, the server will refuse to start and will tell you which migration IDs are missing.

### Defining your realm

Insert a record for your realm into the `realmlist` table of the `realmd` database. You can do this via a query in your GUI MySQL client or via the command line.

**Using the command line:**

```bash
mysql -u mangos -p -e "USE realmd; INSERT INTO realmlist (id, name, address, port, icon, realmflags, timezone, allowedSecurityLevel, population, gamebuild_min, gamebuild_max, flag) VALUES (1, 'My VMaNGOS Realm', '127.0.0.1', 8085, 1, 0, 1, 0, 0, 5875, 5875, 0);"
```

**Using a GUI client:**  
Open the `realmd` database, find the `realmlist` table, and add a new row with your desired values.

Adjust the `name` and `address` if you plan to host it on a different machine or IP. The port (`8085`) must match the port in the world server configuration file.

---

## 3. Editing the configuration files

The final step before starting the server is to configure the two configuration files: `mangosd.conf` (world server) and `realmd.conf` (login server). They are simple text files located in your server's `etc` directory (or alongside the executables, depending on your build).

1. **Rename the default config files**  
   Change the name of `mangosd.conf.dist` to `mangosd.conf` and `realmd.conf.dist` to `realmd.conf`.

2. **Edit the database connection strings**  
   Open both files in Notepad or any text editor and locate the lines that begin with `LoginDatabase.Info`, `WorldDatabase.Info`, `CharacterDatabase.Info`, and `LogsDatabase.Info`. The default entries usually look like:

   ```
   LoginDatabase.Info              = "127.0.0.1;3306;mangos;mangos;realmd"
   WorldDatabase.Info              = "127.0.0.1;3306;mangos;mangos;mangos"
   CharacterDatabase.Info          = "127.0.0.1;3306;mangos;mangos;characters"
   LogsDatabase.Info               = "127.0.0.1;3306;mangos;mangos;logs"
   ```

   If you used a different MySQL username or password during database setup, replace the `mangos;mangos` part accordingly. Leave the IP (`127.0.0.1`) and port (`3306`) as they are if MySQL runs on the same machine.

3. **Check the `DataDir` setting in `mangosd.conf`**  
   Make sure it points to the folder where you placed the `maps`, `vmaps`, `mmaps`, and `5875/dbc` directories. For example:

   ```
   DataDir = "C:/vmangos/data"
   ```

4. **Set the logs directory (optional)**  
   You can specify where log files should be written, for example:

   ```
   LogsDir = "C:/vmangos/logs"
   ```

   Create that folder if it doesn't exist.

5. **Save both files**.

---

## 4. Starting your server

Now that everything is configured, make sure your MySQL server is running.

- **Start the login server**  
  Double‑click `realmd.exe` (or run it from a command prompt).

- **Start the world server**  
  Double‑click `mangosd.exe`. It will take a while to load all data. When you hear a beep, the server is ready.

### Creating an admin account

Once `mangosd` is running, type the following commands in its console window:

```
account create admin admin
account set gmlevel admin 6
```

This creates an account with username `admin` and password `admin`, and grants it Game Master level 6 (full administrator).

---

## 5. Connecting with the client

1. In your World of Warcraft 1.12.1 folder, open `realmlist.wtf` with a text editor.
2. Replace its content with:
   ```
   set realmlist 127.0.0.1
   ```
3. Save the file.

Launch the game and login  with the account you just created.
