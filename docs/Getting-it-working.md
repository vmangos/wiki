Once you've compiled the server core, there are still a number of steps you must go through before being able to start your server.

## 1. Copying the dependencies

The first thing to do after compiling the core is to copy over the dependencies you used to build it. Go to _C:\ACE_wrappers\lib_ and copy _ACE.dll_ to the main server folder.

Now you need to do the same for TBB. Since we didn't need to build TBB ourselves, it comes with multiple versions of the dlls for every platform and version of Visual Studio. Go to _C:\tbb\bin_ and then into either _ia32_ if you compiled for x86, or into _intel64_ if you targeted x64 instead. Inside there you will see a folder for every version of Visual Studio. You need the 2015 dlls, which are inside the _vc14_ folder. Copy all dll files from there and paste them in the main server folder like you did with ACE.

## 2. Extracting data from the client

The server requires a large amount of data from the client in order to operate. That includes DBC, Map, VMap and MMap files. To extract all that data you need extractors. You can compile them yourself by selecting the _USE_EXTRACTORS_ option when configuring in CMake. Alternatively you can download all the required files from the internet.

Now that you have the extractors, place them together with the dependency dlls into your World of Warcraft 1.12.1 game folder. There is a separate extractor for everything. You must run them in the following older, and wait for each one to complete before starting the next extractor.

- _mapextractor.exe_

This is will extract the dbc and map files.

- _vmapextractor.exe_

This will extract the raw visual map files.

- _vmap_assembler.exe_

This will convert the vmaps into a usable format.

- _MoveMapGen.exe_

This will generate movement maps, so that creatures can navigate all the map geometry properly. This is an optional step and it takes a very long time to complete. Be prepared to wait several hours for it to finish. If you choose to skip generating movement maps, mobs will chase their target in a straight line and things like fear movement will not work. If you get an error saying the "mmaps" folder does not exist when running the extractor, just create it yourself.

Once you've extracted everything, move the "dbc", "maps", "vmaps" and "mmaps" folders over to your server directory. The "Buildings" folder is not needed and can be deleted safely.

Note that the dbc path must also include the build number of the client from which the files were extracted. If you are unsure what is the exact build, you can see it in the lower left corner of the login screen. The build number of the 1.12.1 client is 5875.

## 3. Setting up the database

The server requires a MySQL database from which to read and save all account, character and world data. Either download the official [MySQL Installer](https://dev.mysql.com/downloads/mysql/5.5.html) or use something like [XAMPP](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/5.6.12/) which provides a ready to use package of both MySQL and Apache. The recommended versions are either 5.5 or 5.6. Version 5.7 can also work, but some users have reported issues with it.

Once you've installed a MySQL server and created a user with full permissions which the emulator can use, you need to setup the following databases:

- _logs_

This is where log data is stored. To create it use the _logs.sql_ file.

- _realmd_

This is the login server database. Account data is stored here. To create it use the _logon.sql_ file.

- _characters_

This is where all data about characters is stored. To create it use the _characters.sql_ file.

- _mangos_

This is the world database. It contains all game content like items, creatures, texts, etc. To create and populate the world database, you must get the latest world db release from the [database repository](https://github.com/brotalnia/database).

After creating all the databases, you must apply any updates since the last major database release. These updates are referred to as migrations. You will find them in _sql\migrations_ inside the repository. For your convenience, there is a batch script that can be used to merge all migrations into a single file for each database. The world database is updated most often, so you are guaranteed to find an sql file that has to be applied to it. If you fail to apply any updates, the server will print the id of the migrations you are missing and refuse to start.

Once you are done with that, you'll need to define your realms in the database. To do this, go to the `realmd` database and add a new entry inside the `realmlist` table with the address and chosen name of your realm. You can leave all other columns with their default values if you plan on having only one realm. In order to host multiple realms, you'll need to assign a different port for each one. The port in the database entry of the realm must match the port in that realm's config file.

## 4. Editing the config files.

The final step in getting your server running is to make sure everything is correct in the configuration files. There is one for the world server _(mangosd.conf)_, and one for the login server _(realmd.conf)_. Those are simple text files that you can edit in notepad. There are plenty of settings you can change in there, and there is usually a short documentation for each one, but the most important thing you have to check in order to get things running is the MySQL connection string.

It looks like this:
> LoginDatabase.Info              = "127.0.0.1;3306;root;root;realmd"
>
> WorldDatabase.Info              = "127.0.0.1;3306;root;root;mangos"
>
> CharacterDatabase.Info          = "127.0.0.1;3306;root;root;characters"
>
> LogsDatabase.Info               = "127.0.0.1;3306;root;root;logs"

There is a separate connection string for each database. The first part of the string is the IP address of the MySQL server. You can leave that at _127.0.0.1_ if MySQL is running on the same computer as the emulator. The next part is the port, you don't need to touch this. The last 3 values are what you'll need to check. Those are the MySQL user, password, and specific database name. Make sure they are correct.

## 5. Starting your server

Now that everything is configured, make sure MySQL is running, and simply run _realmd.exe_ and _mangosd.exe_ to start your very own vanilla wow server. Once it is done loading you will hear a beep and you may connect to your server.