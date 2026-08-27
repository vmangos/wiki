# creature_movement_special Table

Special movement paths (e.g., scripted escort or event paths) defined by creature entry or path ID.

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

- <a id="f-id"></a>**`id`** - Creature entry ([`creature_template`](creature_template.md).entry) or arbitrary path ID assigned from scripts/hardcoded events.
- <a id="f-point"></a>**`point`** - Primary Key. Sequence index within the special movement path.
- <a id="f-position_x"></a>**`position_x`** - Special waypoint X coordinate.
- <a id="f-position_y"></a>**`position_y`** - Special waypoint Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Special waypoint Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Facing.
- <a id="f-waittime"></a>**`waittime`** - Wait at point before continuing.
- <a id="f-wander_distance"></a>**`wander_distance`** - Random offset.
- <a id="f-script_id"></a>**`script_id`** - Script executed when reached.
- <a id="f-path_id"></a>**`path_id`** - Path identifier.
