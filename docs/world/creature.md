# creature Table

Contains creature spawn data (placement, respawn, movement, and overrides).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`id`](#f-id) | mediumint(8) unsigned | MUL | NO | 0 |  |
| [`id2`](#f-id2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`id3`](#f-id3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`id4`](#f-id4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`id5`](#f-id5) | mediumint(8) unsigned |  | NO | 0 |  |
| [`map`](#f-map) | smallint(5) unsigned | MUL | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |
| [`spawntimesecsmin`](#f-spawntimesecsmin) | int(10) unsigned |  | NO | 120 |  |
| [`spawntimesecsmax`](#f-spawntimesecsmax) | int(10) unsigned |  | NO | 120 |  |
| [`wander_distance`](#f-wander_distance) | float |  | NO | 5 |  |
| [`health_percent`](#f-health_percent) | float |  | NO | 100 |  |
| [`mana_percent`](#f-mana_percent) | float unsigned |  | NO | 100 |  |
| [`movement_type`](#f-movement_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spawn_flags`](#f-spawn_flags) | int(10) unsigned |  | NO | 0 |  |
| [`visibility_mod`](#f-visibility_mod) | float |  | YES | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key, auto-increment. Unique spawn ID.
- <a id="f-id"></a><a id="f-id2"></a><a id="f-id3"></a><a id="f-id4"></a><a id="f-id5"></a>**`id` - `id5`** - Creature template IDs ([`creature_template`](creature_template.md).entry; random selection among them). If multiple, one is chosen at spawn.
- <a id="f-map"></a>**`map`** - Map ID (from [`map_template`](map_template.md).entry).
- <a id="f-position_x"></a><a id="f-position_y"></a><a id="f-position_z"></a>**`position_x/y/z`** - Spawn coordinates.
- <a id="f-orientation"></a>**`orientation`** - Facing direction (radians).
- <a id="f-spawntimesecsmax"></a><a id="f-spawntimesecsmin"></a>**`spawntimesecsmin` / `spawntimesecsmax`** - Min/max respawn time (seconds). A random value between them is used.
- <a id="f-wander_distance"></a>**`wander_distance`** - Maximum wandering radius if `movement_type` = 1.
- <a id="f-mana_percent"></a><a id="f-health_percent"></a>**`health_percent`** / **`mana_percent`** - Starting health/mana as percentage of template max.
- <a id="f-movement_type"></a>**`movement_type`** - Movement generator:
  - `0` - Idle (stationary)
  - `1` - Random movement within `wander_distance`
  - `2` - Waypoint movement (using path IDs)
- <a id="f-spawn_flags"></a>**`spawn_flags`** - Bitmask:
  - `1` - Active Object (AI updates even without players)
  - `2` - Disabled
  - `4` - Random respawn time (±10%)
  - `8` - Dynamic respawn time (if population >2500)
  - `16` - Force dynamic respawn for elite
  - `32` - Evade out of home area (ScriptedAI only)
  - `64` - Not visible (can be revealed by spell effect 46)
  - `128` - Dead (used for quests requiring revive)
- <a id="f-visibility_mod"></a>**`visibility_mod`** - Overrides default visibility distance (requires `spawn_flags` to include active).
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Content patch range (0 = 1.2, 10 = 1.12.1).

