# cinematic_waypoints Table

Defines camera positions at specific times during intro cinematics. Used to load nearby creatures and objects even if no players are in the area.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`cinematic`](#f-cinematic) | int(11) unsigned |  | YES | 0 |  |
| [`timer`](#f-timer) | int(11) unsigned |  | YES | 0 |  |
| [`position_x`](#f-position_x) | float |  | YES |  |  |
| [`position_y`](#f-position_y) | float |  | YES |  |  |
| [`position_z`](#f-position_z) | float |  | YES |  |  |
| [`comment`](#f-comment) | varchar(255) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-cinematic"></a>**`cinematic`** - Cinematic ID (from `CinematicSequences.dbc`).
- <a id="f-timer"></a>**`timer`** - Time in milliseconds.
- <a id="f-position_x"></a>**`position_x`** - Waypoint X coordinate.
- <a id="f-position_y"></a>**`position_y`** - Waypoint Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Waypoint Z coordinate.
- <a id="f-comment"></a>**`comment`** - Description (not used by core).
