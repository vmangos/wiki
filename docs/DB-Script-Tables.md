# The DB Script tables

These tables contain script actions that are triggered from many different places depending on the table. It is recommended that you use the [ScriptEditor](https://github.com/brotalnia/scripteditor) to create scripts, instead of editing the table manually.

## Structure

### 1. id - int(10) unsigned

The id of the script. This is an arbitrary number you can choose. Sometimes there are conventions based on the table its in.

### 2. delay - int(10) unsigned

A delay in seconds after which this action will be executed.

### 3. priority - tinyint(3) unsigned

This field defines the order in which actions with the same delay will be executed. Lower values take precedence.

### 4. command - tinyint(3) unsigned

The type of the script command. This defines the meaning of the parameters. Please consult the [enum](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L35) in the header file.

### 5. datalong1-4 - mediumint(8)

These are unsigned integer fields whose meaning depends on the command type. Please consult the [structures](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L532) in the header file.

### 6. target_param1-2 - int(10) unsigned

These are targeting parameters whose meaning depends on the target type. Please consult the [enum](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L1129) in the header file.

### 7. target_type - tinyint(3) unsigned

These is the type of target used by the script action. Note that scripts execute on the source, and the target is only used as an additional parameter for actions that need a target, so if you want to execute the action on the target you have to apply the swap targets flag. Please consult the [enum](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L1129) in header file.

### 8. data_flags - tinyint(3)

These are flags which can be used to swap the source and target or return an error on failure or other things. Please consult the [enum](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L514) in the header file.

### 9. dataint1-4 - int(11)

These are signed integer fields whose meaning depends on the command type. Please consult the [structures](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L532) in the header file.

### 10. x,y,z,o - float

These are floating point fields whose meaning depends on the command type. Please consult the [structures](https://github.com/vmangos/core/blob/development/src/game/Maps/ScriptCommands.h#L532) in the header file.

### 11. condition_id - mediumint(8) unsigned

A condition id from the [conditions](conditions.md) table. This is an optional field.

### 12. comments - varchar(255)

This is a comment describing the event and the actions it triggers.

The convention is to use this format:

_Script Name: Source Name - Action Type_

Example:

_In Dreams: Tirion Fordring - Start Waypoints_