# creature_movement_template Table

Template-level waypoint paths that can be reused by any creature spawn (by entry).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO |  |  |
| [`point`](#f-point) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |
| [`waittime`](#f-waittime) | int(10) unsigned |  | NO | 0 |  |
| [`wander_distance`](#f-wander_distance) | float unsigned |  | NO | 0 |  |
| [`script_id`](#f-script_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`path_id`](#f-path_id) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Part of the primary key. Creature entry sharing this waypoint path. (see [`creature_template`](creature_template.md).entry)
- <a id="f-point"></a>**`point`** - Part of the primary key. Waypoint sequence number along the path.
- <a id="f-position_x"></a>**`position_x`** - Waypoint coordinates.
- <a id="f-position_y"></a>**`position_y`** - Waypoint Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Waypoint Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Facing at arrival (100 = face movement direction).
- <a id="f-waittime"></a>**`waittime`** - Wait in ms before walking to next point.
- <a id="f-wander_distance"></a>**`wander_distance`** - Wander radius while waiting at this point.
- <a id="f-script_id"></a>**`script_id`** - [`creature_movement_scripts`](creature_movement_scripts.md).id fired on arrival.
- <a id="f-path_id"></a>**`path_id`** - Sub-path from [`creature_movement_special`](creature_movement_special.md) followed instead of the direct move to this point.
