# conditions Table

Provides a flexible conditional logic system used by scripts, gossip, quests, teleports, etc. This table is heavily referenced. It is recommended to use the [ScriptEditor](https://github.com/brotalnia/scripteditor) when working with conditions.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`condition_entry`](#f-condition_entry) | mediumint(8) unsigned | PRI | NO |  | auto_increment |
| [`type`](#f-type) | tinyint(3) | MUL | NO | 0 |  |
| [`value1`](#f-value1) | int(11) |  | NO | 0 |  |
| [`value2`](#f-value2) | int(11) |  | NO | 0 |  |
| [`value3`](#f-value3) | int(11) |  | NO | 0 |  |
| [`value4`](#f-value4) | int(11) |  | NO | 0 |  |
| [`flags`](#f-flags) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-condition_entry"></a>**`condition_entry`** - Primary Key, auto-increment. Referenced by other tables.
- <a id="f-type"></a>**`type`** - Condition type (see the [Condition Types](#condition-types) list below).
- <a id="f-value1"></a><a id="f-value2"></a><a id="f-value3"></a><a id="f-value4"></a>**`value1` - `value4`** - Parameters whose meaning depends on `type`.
- <a id="f-flags"></a>**`flags`** - Modifiers:
  - `1` = reverse result (NOT)
  - `2` = swap targets

---

## Condition Types {#condition-types}

| Type | Name | Description | Requirement | Parameters |
| :---: | :--- | :--- | :--- | :--- |
| -3 | `CONDITION_NOT` | Opposite of a condition (deprecated - use flags). | None | `value1` = condition_id |
| -2 | `CONDITION_OR` | True if at least one condition is true. | None | `value1`, `value2` = condition_id; optional `value3`, `value4` |
| -1 | `CONDITION_AND` | True only if all conditions are true. | None | Same as OR |
| 0 | `CONDITION_NONE` | Always true (internal). | None | - |
| 1 | `CONDITION_AURA` | Unit has an aura from this spell. | Unit target | `value1` = spell_id, `value2` = effindex |
| 2 | `CONDITION_ITEM` | Player has item in inventory. | Player target | `value1` = item_id, `value2` = count |
| 3 | `CONDITION_ITEM_EQUIPPED` | Player has item equipped. | Player target | `value1` = item_id |
| 4 | `CONDITION_AREAID` | Player is in a zone/area. | WorldObject | `value1` = area_id |
| 5 | `CONDITION_REPUTATION_RANK_MIN` | Player's reputation >= min rank. | Player | `value1` = faction_id, `value2` = min_rank |
| 6 | `CONDITION_TEAM` | Player is in a team. | Player | `value1` = 469 (Alliance) or 67 (Horde) |
| 7 | `CONDITION_SKILL` | Player's skill >= value. | Player | `value1` = skill_id, `value2` = skill_value |
| 8 | `CONDITION_QUESTREWARDED` | Quest already completed. | Player | `value1` = quest_id |
| 9 | `CONDITION_QUESTTAKEN` | Quest accepted (0 any, 1 incomplete, 2 complete). | Player | `value1` = quest_id, `value2` = 0/1/2 |
| 10 | `CONDITION_AD_COMMISSION_AURA` | Has Argent Dawn commission aura. | Player | - |
| 11 | `CONDITION_SAVED_VARIABLE` | Check global saved variable. | None | `value1` = index, `value2` = data, `value3` = 0 (==), 1 (>=), 2 (<=) |
| 12 | `CONDITION_ACTIVE_GAME_EVENT` | Event is active. | None | `value1` = event_id |
| 13 | `CONDITION_CANT_PATH_TO_VICTIM` | Creature cannot path to victim. | Creature | - |
| 14 | `CONDITION_RACE_CLASS` | Player's race/class match mask. | Player | `value1` = race_mask, `value2` = class_mask |
| 15 | `CONDITION_LEVEL` | Target's level condition. | Unit | `value1` = level, `value2` = 0 (==), 1 (>=), 2 (<=) |
| 16 | `CONDITION_SOURCE_ENTRY` | Source's entry matches. | WorldObject | `value1` = entry, `value2` - `value4` = entry (optional) |
| 17 | `CONDITION_SPELL` | Player has learned spell. | Player | `value1` = spell_id, `value2` = 0 (has), 1 (hasn't) |
| 18 | `CONDITION_INSTANCE_SCRIPT` | Instance script internal condition. | Map | `value1` = map_id, `value2` = instance_condition_id |
| 19 | `CONDITION_QUESTAVAILABLE` | Player can accept quest. | Player | `value1` = quest_id |
| 20 | `CONDITION_NEARBY_CREATURE` | Creature with given ID nearby. | WorldObject | `value1` = creature_id, `value2` = search_radius, `value3` = dead (optional), `value4` = not_self (optional) |
| 21 | `CONDITION_NEARBY_GAMEOBJECT` | Gameobject with given ID nearby. | WorldObject | `value1` = gobject_id, `value2` = search_radius |
| 22 | `CONDITION_QUEST_NONE` | Player has not taken/rewarded quest. | Player | `value1` = quest_id |
| 23 | `CONDITION_ITEM_WITH_BANK` | Player has item in inventory/bank. | Player | `value1` = item_id, `value2` = count |
| 24 | `CONDITION_WOW_PATCH` | Current patch condition. | None | `value1` = patch (0-10), `value2` = 0 (==), 1 (>=), 2 (<=) |
| 25 | `CONDITION_ESCORT` | Escort alive state & distance. | Source & Target | `value1` = flags (see code), `value2` = distance (optional) |
| 26 | `CONDITION_ACTIVE_HOLIDAY` | Holiday active (use event instead). | None | `value1` = holiday_id |
| 27 | `CONDITION_GENDER` | Target gender. | WorldObject | `value1` = 0 (male), 1 (female), 2 (none) |
| 28 | `CONDITION_IS_PLAYER` | Target is a player or player-owned. | WorldObject | `value1` = 0 (player only), 1 (player owned too) |
| 29 | `CONDITION_SKILL_BELOW` | Skill less than value (or not known). | Player | `value1` = skill_id, `value2` = skill_value (if 1, true if not known) |
| 30 | `CONDITION_REPUTATION_RANK_MAX` | Reputation <= max rank. | Player | `value1` = faction_id, `value2` = max_rank |
| 31 | `CONDITION_HAS_FLAG` | Source has a flag set. | WorldObject | `value1` = field_id (UpdateFields.h), `value2` = flag |
| 32 | `CONDITION_LAST_WAYPOINT` | Creature's last waypoint condition. | Creature | `value1` = waypointId, `value2` = 0 (==), 1 (>=), 2 (<=) |
| 33 | `CONDITION_MAP_ID` | Current map ID. | Map | `value1` = map_id |
| 34 | `CONDITION_INSTANCE_DATA` | Instance script data comparison. | Map | `value1` = index, `value2` = data, `value3` = 0/1/2 |
| 35 | `CONDITION_MAP_EVENT_DATA` | Scripted map event data comparison. | Map | `value1` = event_id, `value2` = index, `value3` = data, `value4` = 0/1/2 |
| 36 | `CONDITION_MAP_EVENT_ACTIVE` | Map event is active. | Map | `value1` = event_id |
| 37 | `CONDITION_LINE_OF_SIGHT` | Source and target have LOS. | Source & Target | - |
| 38 | `CONDITION_DISTANCE_TO_TARGET` | Distance between source and target. | Source & Target | `value1` = distance, `value2` = 0 (==), 1 (>=), 2 (<=) |
| 39 | `CONDITION_IS_MOVING` | Target is moving. | WorldObject | - |
| 40 | `CONDITION_HAS_PET` | Target has a pet. | Unit | - |
| 41 | `CONDITION_HEALTH_PERCENT` | Health percent condition. | Unit | `value1` = percent, `value2` = 0/1/2 |
| 42 | `CONDITION_MANA_PERCENT` | Mana percent condition. | Unit | same |
| 43 | `CONDITION_IS_IN_COMBAT` | Target is in combat. | Unit | - |
| 44 | `CONDITION_REACTION` | Target's reaction to source matches criteria. | Source & Target | `value1` = reaction rank (see `ReputationRank`), `value2` = 0 (==), 1 (>=), 2 (<=) |
| 45 | `CONDITION_IS_IN_GROUP` | Player is in a group. | Player | - |
| 46 | `CONDITION_IS_ALIVE` | Target is alive. | Unit | - |
| 47 | `CONDITION_MAP_EVENT_TARGETS` | All extra targets satisfy condition. | Map | `value1` = event_id, `value2` = condition_id |
| 48 | `CONDITION_OBJECT_IS_SPAWNED` | Gameobject is spawned. | GameObject | - |
| 49 | `CONDITION_OBJECT_LOOT_STATE` | Loot state of GO. | GameObject | `value1` = loot_state (see enum) |
| 50 | `CONDITION_OBJECT_FIT_CONDITION` | GO with this guid satisfies condition. | Map | `value1` = guid, `value2` = condition_id |
| 51 | `CONDITION_PVP_RANK` | Honor rank condition. | Player | `value1` = rank, `value2` = 0/1/2 |
| 52 | `CONDITION_DB_GUID` | Source object's db guid matches. | WorldObject | `value1` - `value4` = guid (optional) |
| 53 | `CONDITION_LOCAL_TIME` | Current time within range. | None | `value1` = start_hour, `value2` = start_minutes, `value3` = end_hour, `value4` = end_minutes |
| 54 | `CONDITION_DISTANCE_TO_POSITION` | Target within distance of coordinates. | WorldObject | `value1` = x, `value2` = y, `value3` = z, `value4` = distance |
| 55 | `CONDITION_OBJECT_GO_STATE` | Gameobject state check. | GameObject | `value1` = go_state (see `GOState`) |
| 56 | `CONDITION_NEARBY_PLAYER` | Player nearby. | Unit | `value1` = 0 (any), 1 (hostile), 2 (friendly), `value2` = search_radius |
| 57 | `CONDITION_CREATURE_GROUP_MEMBER` | Creature is part of a group. | Creature | `value1` = leader_guid (optional) |
| 58 | `CONDITION_CREATURE_GROUP_DEAD` | Creature's group is dead. | Creature | - |
| 59 | `CONDITION_AREA_EXPLORED` | Player has explored the area. | Player | `value1` = area_id |

*Referenced by: [`gossip_menu`](gossip_menu.md), [`gossip_menu_option`](gossip_menu_option.md), [`areatrigger_teleport`](areatrigger_teleport.md), [`creature_ai_events`](creature_ai_events.md), [`quest_template`](quest_template.md), [`npc_vendor`](npc_vendor.md), [`spell_area`](spell_area.md), `*_loot_template`, [`script_escort_data`](script_escort_data.md).*
