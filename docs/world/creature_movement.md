# creature_movement Table

Defines waypoint movement paths for specific creature spawns (GUID-based).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(10) unsigned | PRI | NO |  |  |
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

- <a id="f-id"></a>**`id`** - Primary Key. Creature GUID (from [`creature`](creature.md).guid).
- <a id="f-point"></a>**`point`** - Primary Key. Sequence number of the waypoint for this spawn guid.
- <a id="f-position_x"></a>**`position_x`** - Waypoint X coordinate.
- <a id="f-position_y"></a>**`position_y`** - Waypoint Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Waypoint Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Facing direction at the waypoint.
- <a id="f-waittime"></a>**`waittime`** - Pause at this point (ms).
- <a id="f-wander_distance"></a>**`wander_distance`** - Random deviation allowed from the point.
- <a id="f-script_id"></a>**`script_id`** - Movement script fired on arrival. (see Script system.)
- <a id="f-path_id"></a>**`path_id`** - Alternative path identifier.
