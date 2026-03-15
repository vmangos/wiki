# The conditions table

Contains conditions that can be checked in scripts and other systems. It is recommended to use the [Script Editor](https://github.com/brotalnia/scripteditor) when working with conditions.

| Name            | Type                  | Comment                                              |
|-----------------|-----------------------|------------------------------------------------------|
| condition_entry | unsigned mediumint(8) | Primary key.                                         |
| type            | tinyint(3)            | The type of condition. See the types below.          |
| value1          | unsigned mediumint(8) | A value whose meaning depends on the condition type. |
| value2          | unsigned mediumint(8) | A value whose meaning depends on the condition type. |
| value3          | unsigned mediumint(8) | A value whose meaning depends on the condition type. |
| value4          | unsigned mediumint(8) | A value whose meaning depends on the condition type. |
| flags           | unsigned tinyint(3)   | 1 = reverse result 2 = swap targets                  |

A list of all conditions follows below.

### -3: CONDITION_NOT

Returns the opposite of the provided condition. This condition is deprecated. Use the reverse result flag.

Requirement: None

Value1: condition_id

### -2: CONDITION_OR

Returns true if at least one of the provided conditions is true.

Requirement: None

Value1: condition_id

Value2: condition_id

Value3: condition_id (optional)

Value4: condition_id (optional)

### -1: CONDITION_AND

Returns true only if all the provided conditions are true.

Requirement: None

Value1: condition_id

Value2: condition_id

Value3: condition_id (optional)

Value4: condition_id (optional)

### 0: CONDITION_NONE

Always returns true. For internal use only.

Requirement: None

### 1: CONDITION_AURA

Checks if the unit has an aura from this spell.

Requirement: Unit Target

Value1: spell_id

Value2: effindex

### 2: CONDITION_ITEM

Checks if the player has an item in his inventory.

Requirement: Player Target

Value1: item_id

Value2: count

### 3: CONDITION_ITEM_EQUIPPED

Checks if the player has equipped an item.

Requirement: Player Target

Value1: item_id

### 4: CONDITION_AREAID

Checks if the player is in a specific zone or area.

Requirement: WorldObject Target or Source

Value1: area_id

### 5: CONDITION_REPUTATION_RANK_MIN

Checks if the player's reputation with a given faction is equal or greater than.

Requirement: Player Target

Value1: faction_id

Value2: min_rank

### 6: CONDITION_TEAM

Checks if the player is a member of the specified team.

Requirement: Player Target

Value1: player_team (469 - Alliance 67 - Horde)

### 7: CONDITION_SKILL

Checks if the player's skill is equal or greater than.

Requirement: Player Target

Value1: skill_id

Value2: skill_value

### 8: CONDITION_QUESTREWARDED

Checks if the player has already completed a quest.

Requirement: Player Target

Value1: quest_id

### 9: CONDITION_QUESTTAKEN

Checks if the player has accepted a quest.

Requirement: Player Target

Value1: quest_id     

Value2: 0,1,2 for condition true while quest active (0 any state, 1 if quest incomplete, 2 if quest completed).

### 10: CONDITION_AD_COMMISSION_AURA

Returns true if the player has an argent dawn commission aura.

Requirement: Player Target

### 11: CONDITION_SAVED_VARIABLE

Checks a global saved variable.

Requirement: None

Value1: index

Value2: data

Value3: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 12: CONDITION_ACTIVE_GAME_EVENT

Checks if a given game event is currently active.

Requirement: None

Value1: event_id

### 13: CONDITION_CANT_PATH_TO_VICTIM

Returns true if the creature is chasing a victim but is unable to find a path to it.

Requirement: Creature Source

### 14: CONDITION_RACE_CLASS

Checks if the player's race and class matches the given mask.

Requirement: Player Target

Value1: race_mask

Value2: class_mask

### 15: CONDITION_LEVEL

Checks the target's level.

Requirement: Unit Target

Value1: level

Value2: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 16: CONDITION_SOURCE_ENTRY

Check's if the source's entry id matches the one specified.

Requirement: WorldObject Source

Value1: entry

### 17: CONDITION_SPELL

Checks if the player has learned the given spell.

Requirement: Player Target

Value1: spell_id

Value2: 0, 1 (0: has spell, 1: hasn't spell)

### 18: CONDITION_INSTANCE_SCRIPT

Calls the instance script to check an internal condition.

Requirement: Map

Value1: map_id

Value2: instance_condition_id (instance script specific enum)

### 19: CONDITION_QUESTAVAILABLE

Checks if the player is able to accept a quest.

Requirement: Player Target

Value1: quest_id

### 20: CONDITION_NEARBY_CREATURE

Checks if there is a creature nearby with the given id.

Requirement: WorldObject Target

Value1: creature_id

Value2: search_radius

### 21: CONDITION_NEARBY_GAMEOBJECT

Checks if there is a gameobject nearby with the given id.

Requirement: WorldObject Target

Value1: gobject_id

Value2: search_radius

### 22: CONDITION_QUEST_NONE

Returns true if the player has not taken the given quest and has not been rewared for it before.

Requirement: Player Target

Value1: quest_id

### 23: CONDITION_ITEM_WITH_BANK

Checks if the player has an item in his inventory or bank.

Requirement: Player Target

Value1: item_id

Value2: count

### 24: CONDITION_WOW_PATCH

Checks the current content patch. (progression system)

Requirement: None

Value1: patch (0-10)

Value2: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 25: CONDITION_ESCORT

Checks the alive state of the source and target, and the distance between them. Used for escorts.

Requirement: None (optionally Creature Source, Player Target)

Value1: flags (see enum eEscortConditionFlags)

Value2: distance (optional)

### 26: CONDITION_ACTIVE_HOLIDAY

Checks if a given holiday is active. Recommended to use CONDITION_ACTIVE_GAME_EVENT instead.

Requirement: None

Value1: holiday_id

### 27: CONDITION_GENDER

Checks the target's gender.

Requirement: WorldObject Target

Value1: gender (0=male, 1=female, 2=none) (see enum Gender)

### 28: CONDITION_IS_PLAYER

Checks if the target is a player or belongs to a player.

Requirement: WorldObject Target

Value1: 0=player only, 1=player owned too

### 29: CONDITION_SKILL_BELOW

Returns true if player knows the skill id and skill is less than (and not equal to) skill_value (for skill_value > 1)

Requirement: Player Target

Value1: skill_id

Value2: skill_value (if 1, then true if player does not know skill_id)

### 30: CONDITION_REPUTATION_RANK_MAX

Returns true if the player's reputation with a given faction is below or equal to the specified rank.

Requirement: Player Target

Value1: faction_id

Value2: max_rank

### 31: CONDITION_HAS_FLAG

Returns true if the source has a specific flag turned on.

Requirement: WorldObject Source

Value1: field_id (see UpdateFields.h)

Value2: flag

### 32: CONDITION_LAST_WAYPOINT

Checks the source creature's last reached waypoint.

Requirement: Creature Source

Value1: waypointId

Value2: 0 : ==, 1: >= 2 <=

### 33: CONDITION_MAP_ID

Checks the current map id.

Requirement: Map

Value1: map_id

### 34: CONDITION_INSTANCE_DATA

Gets data from the instance script and checks the returned value.

Requirement: Map

Value1: index

Value2: data

Value3: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 35: CONDITION_MAP_EVENT_DATA

Gets data from a scripted map event and checks the returned value.

Requirement: Map

Value1: event_id

Value2: index

Value3: data

Value4: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 36: CONDITION_MAP_EVENT_ACTIVE

Returns true if a scripted map event with this id is currently active.

Requirement: Map

Value1: event_id

### 37: CONDITION_LINE_OF_SIGHT

Returns true if the source and target are in line of sight of one another.

Requirement: WorldObject Source, WorldObject Target

### 38: CONDITION_DISTANCE

Checks the distance between the provided source and target.

Requirement: WorldObject Source, WorldObject Target

Value1: distance

Value2: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 39: CONDITION_IS_MOVING

Returns true if the target is currently moving.

Requirement: WorldObject Target

### 40: CONDITION_HAS_PET 

Returns true if the target has a pet.

Requirement: Unit Target

### 41: CONDITION_HEALTH_PERCENT

Checks the target's current health percent.

Requirement: Unit Target

Value1: hp_percent

Value2: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 42: CONDITION_MANA_PERCENT

Checks the target's current mana percent.

Requirement: Unit Target

Value1: mana_percent

Value2: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)

### 43: CONDITION_IS_IN_COMBAT

Checks if the target is currently in combat.

Requirement: Unit Target

### 44: CONDITION_IS_HOSTILE_TO

Returns true if the target is hostile to the source.

Requirement: WorldObject Source, WorldObject Target

### 45: CONDITION_IS_IN_GROUP

Returns true if the player is in a group.

Requirement: Player Target

### 46: CONDITION_IS_ALIVE

Returns true if the target is alive.

Requirement: Unit Target

### 47: CONDITION_MAP_EVENT_TARGETS

Returns true if all extra targets that are part of a scripted map event satisfy the provided condition id.

Requirement: Map

Value1: event_id

Value2: condition_id

### 48: CONDITION_OBJECT_IS_SPAWNED

Returns true if the gameobject is currently spawned.

Requirement: GameObject Target

### 49: CONDITION_OBJECT_LOOT_STATE

Checks the current loot state of a GameObject.

Requirement: GameObject Target

Value1: loot_state (see enum LootState)

### 50: "CONDITION_OBJECT_FIT_CONDITION

Returns true if a gameobject with this guid exists and it satisfies the provided condition id.

Requirement: Map

Value1: guid

Value2: condition_id

### 51: CONDITION_PVP_RANK 

Checks the player's honor rank.

Requirement: Player Target

Value1: rank

Value2: 0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)