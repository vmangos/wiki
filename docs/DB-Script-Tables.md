# DB Script Tables

The generic script system provides a unified way to execute scripted actions (e.g., NPC speech, spell casts, movement, quest completion) from various database tables. Many tables share the same schema and are used in different contexts. It is recommended to use the [ScriptEditor](https://github.com/brotalnia/scripteditor) when creating scripts.

---

## Tables Using the Generic Script Schema

The following tables all use the same column structure described below:

- [`areatrigger_scripts`](world/areatrigger_scripts.md) - Triggered when a player enters an area trigger
- [`creature_ai_scripts`](world/creature_ai_scripts.md) - Used by EventAI (though `delay` is ignored)
- [`creature_movement_scripts`](world/creature_movement_scripts.md) - Executed when a creature reaches a waypoint
- [`creature_spells_scripts`](world/creature_spells_scripts.md) - Triggered by creature spell casts
- [`event_scripts`](world/event_scripts.md) - Started by in-game events (object use, spell effects, waypoints, ...)
- [`gameobject_scripts`](world/gameobject_scripts.md) - Triggered by game object activation
- [`generic_scripts`](world/generic_scripts.md) - Used by various core systems
- [`gossip_scripts`](world/gossip_scripts.md) - Executed when a gossip option is selected
- [`quest_end_scripts`](world/quest_end_scripts.md) - Executed when a quest is completed (handed in)
- [`quest_start_scripts`](world/quest_start_scripts.md) - Executed when a quest is accepted
- [`spell_scripts`](world/spell_scripts.md) - Executed when a spell is cast

> **Note:** [`creature_ai_scripts`](world/creature_ai_scripts.md) uses the same schema but does **not** support delays - scripts execute instantly. For delays, use the `START_SCRIPT` command (39) to launch a generic script.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| `id` | int(10) unsigned |  | NO | 0 |  |
| `delay` | int(10) unsigned |  | NO | 0 |  |
| `priority` | tinyint(3) unsigned |  | NO | 0 |  |
| `command` | tinyint(3) unsigned |  | NO | 0 |  |
| `datalong` | int(10) unsigned |  | NO | 0 |  |
| `datalong2` | int(10) unsigned |  | NO | 0 |  |
| `datalong3` | int(10) unsigned |  | NO | 0 |  |
| `datalong4` | int(10) unsigned |  | NO | 0 |  |
| `target_param1` | int(10) unsigned |  | NO | 0 |  |
| `target_param2` | int(10) unsigned |  | NO | 0 |  |
| `target_type` | tinyint(3) unsigned |  | NO | 0 |  |
| `data_flags` | tinyint(3) unsigned |  | NO | 0 |  |
| `dataint` | int(11) |  | NO | 0 |  |
| `dataint2` | int(11) |  | NO | 0 |  |
| `dataint3` | int(11) |  | NO | 0 |  |
| `dataint4` | int(11) |  | NO | 0 |  |
| `x` | float |  | NO | 0 |  |
| `y` | float |  | NO | 0 |  |
| `z` | float |  | NO | 0 |  |
| `o` | float |  | NO | 0 |  |
| `condition_id` | mediumint(8) unsigned |  | NO | 0 |  |
| `comments` | varchar(255) |  | NO |  |  |

---

## Field Breakdown

### Script Identification

| Field | Description |
|-------|-------------|
| `id` | Script ID that links to the parent table (e.g., [`quest_template`](world/quest_template.md).CompleteScript, [`gameobject`](world/gameobject.md).script_id, etc.). All rows with the same `id` belong to the same script. Often the ID is arbitrary, but some tables have conventions (e.g., multiplying a creature ID by 100). |
| `delay` | **Seconds** to wait before executing this command after the script starts. Multiple commands with the same `id` can have different delays to create sequences. For [`creature_ai_scripts`](world/creature_ai_scripts.md), this field is **ignored** (commands run instantly). |
| `priority` | Execution order when multiple commands have the same delay. Lower values execute first. |

### Command Parameters

| Field | Description |
|-------|-------------|
| `command` | Script command type (0-93). Determines how `datalong`, `datalong2-4`, and `dataint` fields are interpreted. See the [Complete Command Reference](#complete-command-reference) below. |
| `datalong` | Command-specific unsigned integer parameter 1. Meaning depends on `command` (e.g., chat_type, field_id, creature_entry). |
| `datalong2` | Command-specific unsigned integer parameter 2 (e.g., value, despawn_delay, spell_id). |
| `datalong3` | Command-specific unsigned integer parameter 3 (e.g., mode, movement_options). |
| `datalong4` | Command-specific unsigned integer parameter 4 (e.g., flags, unique_distance). |

### Target Selection

| Field | Description |
|-------|-------------|
| `target_param1` | First target identifier. Meaning depends on `target_type` (e.g., creature entry, gameobject guid). |
| `target_param2` | Second target identifier (e.g., search radius in yards). |
| `target_type` | Target selection method. See the [Target Types](#target-types) section below. The action is performed on the **source** (e.g., the NPC or object that triggered the script) unless the `data_flags` flag to swap is used. The target is an additional parameter used by the command. |
| `data_flags` | Special flags modifying target/source behavior. See [Data Flags](#data-flags) below. |

### Data Parameters

| Field | Description |
|-------|-------------|
| `dataint` | Signed integer parameter; meaning depends on `command`: e.g. broadcast_text ids for TALK (0), equipment slots for SET_EQUIPMENT (19), chances for START_SCRIPT (39)/CREATURE_SPELLS (55). |
| `dataint2` | Additional signed integer parameter. For the TALK command (0), provides alternative text IDs for random selection. |
| `dataint3` | Additional signed integer parameter (third alternative text ID). |
| `dataint4` | Additional signed integer parameter (fourth alternative text ID). |

### Positional Parameters

| Field | Description |
|-------|-------------|
| `x` | X coordinate for movement, teleportation, or summoning commands. |
| `y` | Y coordinate for movement, teleportation, or summoning commands. |
| `z` | Z coordinate for movement, teleportation, or summoning commands. |
| `o` | Orientation (radians) for movement, teleportation, or summoning commands. |

### Other Fields

| Field | Description |
|-------|-------------|
| `condition_id` | Optional condition ID from [`conditions`](world/conditions.md).condition_entry. The script step only executes if the condition evaluates to true. |
| `comments` | Human-readable description for documentation purposes. Convention: `Script Name: Source Name - Action Type` (e.g., `In Dreams: Tirion Fordring - Start Waypoints`). |

---

## Complete Command Reference

The meaning of `datalong`, `datalong2-4`, and `dataint` fields depends entirely on the `command` value. The `ScriptInfo` union in `ScriptCommands.h` defines these mappings.

| Cmd | Name | datalong | datalong2 | datalong3 | datalong4 | dataint | dataint2 | dataint3 | dataint4 |
|:---:|------|----------|-----------|-----------|-----------|---------|----------|----------|----------|
| 0 | TALK | chat_type | unused | unused | unused | broadcast_text_id | alt_text_id2 | alt_text_id3 | alt_text_id4 |
| 1 | EMOTE | emote_id1 | emote_id2 | emote_id3 | emote_id4 | is_targeted | unused | unused | unused |
| 2 | FIELD_SET | field_id | value | unused | unused | unused | unused | unused | unused |
| 3 | MOVE_TO | coordinates_type | travel_time | movement_options | flags | path_id | unused | unused | unused |
| 4 | MODIFY_FLAGS | field_id | bitmask | mode | unused | unused | unused | unused | unused |
| 5 | INTERRUPT_CASTS | with_delayed | spell_id | unused | unused | unused | unused | unused | unused |
| 6 | TELEPORT_TO | map_id | teleport_options | unused | unused | unused | unused | unused | unused |
| 7 | QUEST_EXPLORED | quest_id | distance | group | unused | unused | unused | unused | unused |
| 8 | KILL_CREDIT | creature_entry | is_group_credit | unused | unused | unused | unused | unused | unused |
| 9 | RESPAWN_GAMEOBJECT | db_guid | despawn_delay | unused | unused | unused | unused | unused | unused |
| 10 | TEMP_SUMMON_CREATURE | creature_entry | despawn_delay | unique_limit | unique_distance | summon_flags | generic_script_id | attack_target | despawn_type |
| 11 | OPEN_DOOR | db_guid | reset_delay | unused | unused | unused | unused | unused | unused |
| 12 | CLOSE_DOOR | db_guid | reset_delay | unused | unused | unused | unused | unused | unused |
| 13 | ACTIVATE_OBJECT | unused | unused | unused | unused | unused | unused | unused | unused |
| 14 | REMOVE_AURA | spell_id | unused | unused | unused | unused | unused | unused | unused |
| 15 | CAST_SPELL | spell_id | flags | unused | unused | unused | unused | unused | unused |
| 16 | PLAY_SOUND | sound_id | flags | unused | unused | unused | unused | unused | unused |
| 17 | CREATE_ITEM | item_id | amount | unused | unused | unused | unused | unused | unused |
| 18 | DESPAWN_CREATURE | despawn_delay | respawn_delay | unused | unused | unused | unused | unused | unused |
| 19 | SET_EQUIPMENT | reset_default | unused | unused | unused | main-hand_id | off-hand_id | ranged_id | unused |
| 20 | MOVEMENT | movement_type | bool_param | int_param | clear | unused | unused | unused | unused |
| 21 | SET_ACTIVEOBJECT | activate | unused | unused | unused | unused | unused | unused | unused |
| 22 | SET_FACTION | faction_id | flags | unused | unused | unused | unused | unused | unused |
| 23 | MORPH_TO_ENTRY_OR_MODEL | creature_or_model | is_display_id | unused | unused | unused | unused | unused | unused |
| 24 | MOUNT_TO_ENTRY_OR_MODEL | creature_or_model | is_display_id | permanent | unused | unused | unused | unused | unused |
| 25 | SET_RUN | run | unused | unused | unused | unused | unused | unused | unused |
| 26 | ATTACK_START | unused | unused | unused | unused | unused | unused | unused | unused |
| 27 | UPDATE_ENTRY | creature_entry | unused | unused | unused | unused | unused | unused | unused |
| 28 | STAND_STATE | stand_state | unused | unused | unused | unused | unused | unused | unused |
| 29 | MODIFY_THREAT | target | unused | unused | unused | unused | unused | unused | unused |
| 30 | SEND_TAXI_PATH | taxi_path_id | unused | unused | unused | unused | unused | unused | unused |
| 31 | TERMINATE_SCRIPT | creature_entry | search_radius | flags | unused | unused | unused | unused | unused |
| 32 | TERMINATE_CONDITION | condition_id | fail_quest | flags | unused | unused | unused | unused | unused |
| 33 | ENTER_EVADE_MODE | unused | unused | unused | unused | unused | unused | unused | unused |
| 34 | SET_HOME_POSITION | mode | unused | unused | unused | unused | unused | unused | unused |
| 35 | TURN_TO | facing_logic | unused | unused | unused | unused | unused | unused | unused |
| 36 | MEETINGSTONE | area_id | unused | unused | unused | unused | unused | unused | unused |
| 37 | SET_INST_DATA | field | data | type | unused | unused | unused | unused | unused |
| 38 | SET_INST_DATA64 | field | data | type | unused | unused | unused | unused | unused |
| 39 | START_SCRIPT | script_id1 | script_id2 | script_id3 | script_id4 | chance1 | chance2 | chance3 | chance4 |
| 40 | REMOVE_ITEM | item_id | amount | unused | unused | unused | unused | unused | unused |
| 41 | REMOVE_OBJECT | unused | unused | unused | unused | unused | unused | unused | unused |
| 42 | SET_MELEE_ATTACK | enabled | unused | unused | unused | unused | unused | unused | unused |
| 43 | SET_COMBAT_MOVEMENT | enabled | unused | unused | unused | unused | unused | unused | unused |
| 44 | SET_PHASE | phase | mode | unused | unused | unused | unused | unused | unused |
| 45 | SET_PHASE_RANDOM | phase1 | phase2 | phase3 | phase4 | unused | unused | unused | unused |
| 46 | SET_PHASE_RANGE | phase_min | phase_max | unused | unused | unused | unused | unused | unused |
| 47 | FLEE | seek_assistance | unused | unused | unused | unused | unused | unused | unused |
| 48 | DEAL_DAMAGE | damage | is_percent | unused | unused | unused | unused | unused | unused |
| 49 | ZONE_COMBAT_PULSE | initial_pulse | unused | unused | unused | unused | unused | unused | unused |
| 50 | CALL_FOR_HELP | unused | unused | unused | unused | unused | unused | unused | unused |
| 51 | SET_SHEATH | sheath_state | unused | unused | unused | unused | unused | unused | unused |
| 52 | INVINCIBILITY | health | is_percent | unused | unused | unused | unused | unused | unused |
| 53 | GAME_EVENT | event_id | start | overwrite | unused | unused | unused | unused | unused |
| 54 | SET_SERVER_VARIABLE | index | value | unused | unused | unused | unused | unused | unused |
| 55 | CREATURE_SPELLS | spell_list_id1 | spell_list_id2 | spell_list_id3 | spell_list_id4 | chance1 | chance2 | chance3 | chance4 |
| 56 | REMOVE_GUARDIANS | creature_entry | unused | unused | unused | unused | unused | unused | unused |
| 57 | ADD_SPELL_COOLDOWN | spell_id | cooldown | unused | unused | unused | unused | unused | unused |
| 58 | REMOVE_SPELL_COOLDOWN | spell_id | unused | unused | unused | unused | unused | unused | unused |
| 59 | SET_REACT_STATE | state | unused | unused | unused | unused | unused | unused | unused |
| 60 | START_WAYPOINTS | wp_source | start_point | initial_delay | can_repeat | overwrite_guid | overwrite_entry | unused | unused |
| 61 | START_MAP_EVENT | event_id | time_limit | unused | unused | success_condition | success_script | failure_condition | failure_script |
| 62 | END_MAP_EVENT | event_id | success | unused | unused | unused | unused | unused | unused |
| 63 | ADD_MAP_EVENT_TARGET | event_id | unused | unused | unused | success_condition | success_script | failure_condition | failure_script |
| 64 | REMOVE_MAP_EVENT_TARGET | event_id | condition_id | targets | unused | unused | unused | unused | unused |
| 65 | SET_MAP_EVENT_DATA | event_id | index | data | type | unused | unused | unused | unused |
| 66 | SEND_MAP_EVENT | event_id | data | targets | unused | unused | unused | unused | unused |
| 67 | SET_DEFAULT_MOVEMENT | movement_type | always_replace | param1 | unused | unused | unused | unused | unused |
| 68 | START_SCRIPT_FOR_ALL | script_id | object_type | object_entry | search_radius | unused | unused | unused | unused |
| 69 | EDIT_MAP_EVENT | event_id | unused | unused | unused | success_condition | success_script | failure_condition | failure_script |
| 70 | FAIL_QUEST | quest_id | unused | unused | unused | unused | unused | unused | unused |
| 71 | RESPAWN_CREATURE | even_if_alive | unused | unused | unused | unused | unused | unused | unused |
| 72 | ASSIST_UNIT | unused | unused | unused | unused | unused | unused | unused | unused |
| 73 | COMBAT_STOP | unused | unused | unused | unused | unused | unused | unused | unused |
| 74 | ADD_AURA | spell_id | flags | unused | unused | unused | unused | unused | unused |
| 75 | ADD_THREAT | unused | unused | unused | unused | unused | unused | unused | unused |
| 76 | SUMMON_OBJECT | gameobject_entry | respawn_time | unused | unused | unused | unused | unused | unused |
| 77 | SET_FLY | enabled | unused | unused | unused | unused | unused | unused | unused |
| 78 | JOIN_CREATURE_GROUP | options | unused | unused | unused | unused | unused | unused | unused |
| 79 | LEAVE_CREATURE_GROUP | unused | unused | unused | unused | unused | unused | unused | unused |
| 80 | SET_GO_STATE | state | unused | unused | unused | unused | unused | unused | unused |
| 81 | DESPAWN_GAMEOBJECT | go_guid | respawn_delay | unused | unused | unused | unused | unused | unused |
| 82 | LOAD_GAMEOBJECT_SPAWN | go_guid | unused | unused | unused | unused | unused | unused | unused |
| 83 | QUEST_CREDIT | unused | unused | unused | unused | unused | unused | unused | unused |
| 84 | SET_GOSSIP_MENU | gossip_menu_id | unused | unused | unused | unused | unused | unused | unused |
| 85 | SEND_SCRIPT_EVENT | event_id | event_data | unused | unused | unused | unused | unused | unused |
| 86 | SET_PVP | enabled | unused | unused | unused | unused | unused | unused | unused |
| 87 | RESET_DOOR_OR_BUTTON | unused | unused | unused | unused | unused | unused | unused | unused |
| 88 | SET_COMMAND_STATE | command_state | unused | unused | unused | unused | unused | unused | unused |
| 89 | PLAY_CUSTOM_ANIM | anim_id | unused | unused | unused | unused | unused | unused | unused |
| 90 | START_SCRIPT_ON_GROUP | script_id1 | script_id2 | script_id3 | script_id4 | chance1 | chance2 | chance3 | chance4 |
| 91 | LOAD_CREATURE_SPAWN | db_guid | with_group | unused | unused | unused | unused | unused | unused |
| 92 | START_SCRIPT_ON_ZONE | script_id | zone_id | with_pets | unused | unused | unused | unused | unused |
| 93 | FOLLOW_ESCORT | do_follow | unused | unused | unused | unused | unused | unused | unused |

> **Note:** Command value `9999` (`SCRIPT_COMMAND_DISABLED`) marks a script action that was disabled during loading and will not execute.

---

## Target Types

The `target_type` field defines how the target(s) for the script command are selected. The action is performed on the **source** (the script-triggering object) unless `data_flags` includes a swap flag.

| Value | Name | Description | target_param1 | target_param2 |
| :---: | :--- | :--- | :--- | :--- |
| 0 | TARGET_T_PROVIDED_TARGET | The object provided to the command. | unused | unused |
| 1 | TARGET_T_HOSTILE | Current target (highest aggro). | unused | unused |
| 2 | TARGET_T_HOSTILE_SECOND_AGGRO | Second highest on aggro (used for cleaves etc.). | select_flags | unused |
| 3 | TARGET_T_HOSTILE_LAST_AGGRO | Last on aggro list. | select_flags | unused |
| 4 | TARGET_T_HOSTILE_RANDOM | Random target from the threat list. | select_flags | unused |
| 5 | TARGET_T_HOSTILE_RANDOM_NOT_TOP | Random target except the top threat. | select_flags | unused |
| 6 | TARGET_T_HOSTILE_NEAREST | Nearest hostile unit on the threat list. | select_flags | unused |
| 7 | TARGET_T_HOSTILE_FARTHEST | Farthest hostile unit on the threat list. | select_flags | unused |
| 8 | TARGET_T_OWNER_OR_SELF | Self, or owner if pet or charmed. | unused | unused |
| 9 | TARGET_T_OWNER | The owner of the source. | unused | unused |
| 10 | TARGET_T_NEAREST_CREATURE_WITH_ENTRY | Nearest nearby creature with this entry. | creature_entry | search_radius |
| 11 | TARGET_T_CREATURE_WITH_GUID | The creature with this database guid. | db_guid | unused |
| 12 | TARGET_T_CREATURE_FROM_INSTANCE_DATA | Creature whose guid is stored in instance data. | instance_data_field | unused |
| 13 | TARGET_T_NEAREST_GAMEOBJECT_WITH_ENTRY | Nearest nearby gameobject with this entry. | gameobject_entry | search_radius |
| 14 | TARGET_T_GAMEOBJECT_WITH_GUID | The gameobject with this database guid. | db_guid | unused |
| 15 | TARGET_T_GAMEOBJECT_FROM_INSTANCE_DATA | Gameobject whose guid is stored in instance data. | instance_data_field | unused |
| 16 | TARGET_T_FRIENDLY | Random friendly unit. | search_radius | exclude_target (bool) |
| 17 | TARGET_T_FRIENDLY_INJURED | Friendly unit missing the most health. | search_radius | hp_percent |
| 18 | TARGET_T_FRIENDLY_INJURED_EXCEPT | Same as above but not the provided target. | search_radius | hp_percent |
| 19 | TARGET_T_FRIENDLY_MISSING_BUFF | Friendly unit without the given aura. | search_radius | spell_id |
| 20 | TARGET_T_FRIENDLY_MISSING_BUFF_EXCEPT | Same as above but not the provided target. | search_radius | spell_id |
| 21 | TARGET_T_FRIENDLY_CC | Friendly unit under crowd control. | search_radius | unused |
| 22 | TARGET_T_MAP_EVENT_SOURCE | Source of a scripted map event. | event_id | unused |
| 23 | TARGET_T_MAP_EVENT_TARGET | Target of a scripted map event. | event_id | unused |
| 24 | TARGET_T_MAP_EVENT_EXTRA_TARGET | Additional worldobject target of a map event. | event_id | creature_entry or gameobject_entry |
| 25 | TARGET_T_NEAREST_PLAYER | Nearest player within range. | search_radius | unused |
| 26 | TARGET_T_NEAREST_HOSTILE_PLAYER | Nearest hostile player within range. | search_radius | unused |
| 27 | TARGET_T_NEAREST_FRIENDLY_PLAYER | Nearest friendly player within range. | search_radius | unused |
| 28 | TARGET_T_RANDOM_CREATURE_WITH_ENTRY | Random nearby creature with this entry (not self). | creature_entry | search_radius |
| 29 | TARGET_T_RANDOM_GAMEOBJECT_WITH_ENTRY | Random nearby gameobject with this entry. | gameobject_entry | search_radius |

---

## Data Flags

The `data_flags` field modifies how sources and targets are handled.

| Flag | Name | Description |
| :---: | :--- | :--- |
| 0x01 | SF_GENERAL_SWAP_INITIAL_TARGETS | Swap the initial source and target before execution. |
| 0x02 | SF_GENERAL_SWAP_FINAL_TARGETS | Swap the final source and target after execution (for subsequent commands). |
| 0x04 | SF_GENERAL_TARGET_SELF | Force the target to be the source itself. |
| 0x08 | SF_GENERAL_ABORT_ON_FAILURE | If the command fails (e.g., target not found), abort the entire script. |
| 0x10 | SF_GENERAL_SKIP_MISSING_TARGETS | If the target is missing, skip this command but continue the script. |

---

## Dependencies

Many fields reference other tables:

- `dataint` - `dataint4` (when command = 0 TALK) → [`broadcast_text`](world/broadcast_text.md).entry
- `datalong` (when commands = 15 CAST_SPELL, 74 ADD_AURA) → [`spell_template`](world/spell_template.md).entry
- `datalong` (when command = 16 PLAY_SOUND) → [`sound_entries`](world/sound_entries.md).id
- `datalong` (when commands = 17 CREATE_ITEM, 40 REMOVE_ITEM) → [`item_template`](world/item_template.md).entry
- `datalong` (when commands = 10 TEMP_SUMMON_CREATURE, 56 REMOVE_GUARDIANS) → [`creature_template`](world/creature_template.md).entry
- `datalong` (when commands = 76 SUMMON_OBJECT, 81 DESPAWN_GAMEOBJECT) → [`gameobject_template`](world/gameobject_template.md).entry
- `condition_id` → [`conditions`](world/conditions.md).condition_entry
- `x`, `y`, `z`, `o` → World coordinates (must be within valid map limits)

---

## Examples

### 1. NPC says a random greeting when a quest is completed

| Field | Value |
|-------|-------|
| `id` | 1000 |
| `delay` | 0 |
| `command` | 0 (TALK) |
| `datalong` (chat_type) | 0 (say) |
| `dataint` | 12345 (broadcast_text ID) |
| `dataint2` | 12346 (alternative) |
| `dataint3` | 12347 (alternative) |
| `target_type` | 0 (provided target) |
| `comments` | "In Dreams: Tirion Fordring - Quest completion greeting" |

### 2. Summon a creature, then despawn it after 60 seconds

| Field | Value |
|-------|-------|
| `id` | 1001 |
| `delay` | 0 |
| `command` | 10 (TEMP_SUMMON_CREATURE) |
| `datalong` | 12345 (creature entry) |
| `datalong2` | 60000 (despawn delay in ms = 60 seconds) |
| `x` | 100.0 |
| `y` | 200.0 |
| `z` | 50.0 |
| `target_type` | 0 (provided target) |
| `comments` | "Spawn escort NPC" |

### 3. Start a generic script with 50% chance after 2 seconds

| Field | Value |
|-------|-------|
| `id` | 1002 |
| `delay` | 2 |
| `command` | 39 (START_SCRIPT) |
| `datalong` | 5000 (script ID) |
| `dataint` | 50 (chance) |
| `target_type` | 0 (provided target) |
| `comments` | "50% chance to trigger script 5000" |
