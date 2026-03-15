# The command table

This table allows you to override the default required account level for in game chat commands. You can also provide help text to be displayed upon usage of the command with invalid parameters.

## Structure

### 1. name - varchar(50)

The full command name, including the categories.

### 2. security - tinyint(3) unsigned

The minimum rank to use the command. Ranks go from 0 for normal player, to 7 for console only.

### 3. help - longtext

Usage information.

### 4. flags - tinyint(3) unsigned

```
COMMAND_FLAGS_ONLY_ON_SELF      = 0x1, // cannot be used on other players
COMMAND_FLAGS_CRITICAL          = 0x2, // usage is recorded in the critical log
```
