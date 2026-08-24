# gameobject Table

Static world spawns of game objects (chests, doors, quest objects, etc.).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  | auto_increment |
| [`id`](#f-id) | mediumint(8) unsigned | MUL | NO | 0 |  |
| [`map`](#f-map) | smallint(5) unsigned | MUL | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |
| [`rotation0`](#f-rotation0) | float |  | NO | 0 |  |
| [`rotation1`](#f-rotation1) | float |  | NO | 0 |  |
| [`rotation2`](#f-rotation2) | float |  | NO | 0 |  |
| [`rotation3`](#f-rotation3) | float |  | NO | 0 |  |
| [`spawntimesecsmin`](#f-spawntimesecsmin) | int(11) |  | NO | 0 |  |
| [`spawntimesecsmax`](#f-spawntimesecsmax) | int(11) |  | NO | 0 |  |
| [`animprogress`](#f-animprogress) | tinyint(3) unsigned |  | NO | 0 |  |
| [`state`](#f-state) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spawn_flags`](#f-spawn_flags) | int(10) unsigned |  | NO | 0 |  |
| [`visibility_mod`](#f-visibility_mod) | float |  | YES | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key, auto-increment. Unique spawn ID.
- <a id="f-id"></a>**`id`** - Game object template ID ([`gameobject_template`](gameobject_template.md).entry).
- <a id="f-map"></a>**`map`** - Map ID.
- <a id="f-position_x"></a><a id="f-position_y"></a><a id="f-position_z"></a>**`position_x/y/z`** - Spawn coordinates.
- <a id="f-orientation"></a>**`orientation`** - Facing direction.
- <a id="f-rotation0"></a><a id="f-rotation1"></a><a id="f-rotation2"></a><a id="f-rotation3"></a>**`rotation0-3`** - Quaternion rotation.
- <a id="f-spawntimesecsmin"></a><a id="f-spawntimesecsmax"></a>**`spawntimesecsmin/max`** - Respawn time range (seconds).
- <a id="f-animprogress"></a>**`animprogress`** - Animation progress (0-255).
- <a id="f-state"></a>**`state`** - Initial state (e.g., open/closed).
- <a id="f-spawn_flags"></a>**`spawn_flags`** - Spawn behavior flags.
- <a id="f-visibility_mod"></a>**`visibility_mod`** - Visibility modifier.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
