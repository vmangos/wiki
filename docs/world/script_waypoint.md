# script_waypoint Table

Defines waypoint paths for scripted creatures (escorts, etc.).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`pointid`](#f-pointid) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`location_x`](#f-location_x) | float |  | NO | 0 |  |
| [`location_y`](#f-location_y) | float |  | NO | 0 |  |
| [`location_z`](#f-location_z) | float |  | NO | 0 |  |
| [`waittime`](#f-waittime) | int(10) unsigned |  | NO | 0 |  |
| [`point_comment`](#f-point_comment) | text |  | YES |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature entry being escorted/pathed. (see [`creature_template`](creature_template.md).entry)
- <a id="f-pointid"></a>**`pointid`** - Primary Key. Waypoint order.
- <a id="f-location_x"></a>**`location_x`** - World coordinates of the waypoint.
- <a id="f-location_y"></a>**`location_y`** - Waypoint Y coordinate.
- <a id="f-location_z"></a>**`location_z`** - Waypoint Z coordinate.
- <a id="f-waittime"></a>**`waittime`** - Delay at the waypoint (ms).
- <a id="f-point_comment"></a>**`point_comment`** - Description.
- Waypoint rows load unless the referenced creature entry does not exist in [`creature_template`](creature_template.md)
  (those are skipped with a DB error); if the creature has no matching `script_name`, the core only logs
  that the waypoints are useless.
