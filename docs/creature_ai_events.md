# The creature_ai_events table

Defines events that will trigger a script for creatures using EventAI. This is a special AI type that allows you to script creatures in the database. It must be assigned to the creature template in the `ai_name` column to actually make the creature use EventAI. It is recommended that you use the [ScriptEditor](https://github.com/brotalnia/scripteditor) to create scripts, instead of editing the table manually.

## Structure

### 1. id - int(11) unsigned, primary key

An unique id for the AI event. The convention is to multiply the creature id by 100 and then increment by 1 for each new event used by the creature.

### 2. creature_id - int(11) unsigned

The creature template id to which this event belongs.

### 3. condition_id - mediumint(8) unsigned

A condition id from the [conditions](conditions.md) table. This is an optional field.

### 4. event_type - tinyint(5) unsigned

The type of event. This defines the meaning of the parameters. Please consult the [enum](https://github.com/vmangos/core/blob/development/src/game/AI/CreatureEventAI.h#L38) in header file.

### 5. event_inverse_phase_mask - int(11)

This is a mask defining in which phases the event will NOT trigger. You raise 2 to the power of the phase you want it not to trigger in. Masks are additive, you can combine them.

Example:

Value 1 (2 to the power of 0) - event wont trigger in phase 0

Value 2 (2 to the power of 1) - event wont trigger in phase 1

Value 3 (2 to the power of 0 + 2 to the power of 1) - event wont trigger in phases 0 and 1

Value 4 (2 to the power of 2) - event wont trigger in phase 2

### 6. event_chance - int(3) unsigned

The chance for this event to trigger the script, a value between 1 and 100.

### 7. event_flags - int(3) unsigned

These are flags that control when the event can trigger. Please consult the [enum](https://github.com/vmangos/core/blob/development/src/game/AI/CreatureEventAI.h#L81) in header file.

### 8. event_param1-4 - int(11)

These are parameters whose meaning is defined by the event type. Please consult the [structures](https://github.com/vmangos/core/blob/development/src/game/AI/CreatureEventAI.h#L112) in the header file.

### 9. action1-3_script - int(11) unsigned

This is a script id from the creature_ai_scripts table. Make sure you apply the "random action" flag if you want only one of the scripts to trigger, otherwise all that are not 0 will be executed.

### 10. comment - varchar(255)

This is a comment describing the event and the actions it triggers.

The convention is to use this format:

_Creature Name - Action Type on Event Type_

Example:

_Fire Elemental - Cast Spell Explosion on Death_