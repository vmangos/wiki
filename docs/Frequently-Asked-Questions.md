### How do I run my own server with the code?

Please read the [Compiling on Windows](Compiling-on-Windows.md) or [Compiling on Linux](Compiling-on-Linux.md) guides first.

### I get an error immediately upon starting my server.

Make sure you are not missing any of the dependency DLLs you used to build the binaries.

### My server shuts itself down almost immediately.

Make sure that MySQL is running and that you are not missing any migrations. The migrations are in the "sql" folder and you have to apply them all before starting the server.

### My server crashes after it gets to Starting Map System.

Make sure you are not missing the maps and vmaps required to run the server. If you compiled for x86, then you must also make sure that map preloading is turned off in the config file, or the server will hit the 32‑bit memory limit upon attempting to load them all.

### There is a lot of spam in my console.

Open the "mangosd.conf" file with Notepad and change the _LogLevel_ setting to 0.

### How do I change the content patch?

Open the "mangosd.conf" file with Notepad and change the _WowPatch_ setting.

### How do I play with a different client build like 1.10?

In order to change the targeted client build, you must edit the value of the _SUPPORTED_CLIENT_BUILD_ define in _Progression.h_ before compiling the core.

### I get stuck when trying to connect to my server.

Make sure the server has finished loading. If you can't type in the mangosd console then it's still loading. If you are trying to connect from another computer, then you have to change the realm's IP address to the real IP of the host machine. This can be done in the `realmd` database, inside the `realmlist` table.

### I can't enter the Ahn'Qiraj raid.

This happens because the gate opening event has not been completed on your server. Go to the `variables` table in the world database and set variable 30050 to 12.

### I am trying to start a game event, but it is disabled.

You need to use _.event enable_ before _.event start_ when the event is disabled in the database. Alternatively you can just remove the disabled flag from the event in the `game_event` table.
