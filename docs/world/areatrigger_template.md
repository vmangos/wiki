# areatrigger_template Table

Defines the location, size, and shape of all area triggers. These are invisible boxes that cause effects when a player enters them. Note: Areariggers are triggered by the client; the server only verifies the player's position. To add new triggers, you must also edit `AreaTrigger.dbc` in the client. Rows in the DBC must be ordered by map ID; otherwise, client-side triggers may break.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(4) unsigned | PRI | NO |  |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO |  |  |
| [`name`](#f-name) | varchar(128) |  | YES | '' |  |
| [`map_id`](#f-map_id) | smallint(3) unsigned |  | NO | 0 |  |
| [`x`](#f-x) | float |  | NO | 0 |  |
| [`y`](#f-y) | float |  | NO | 0 |  |
| [`z`](#f-z) | float |  | NO | 0 |  |
| [`radius`](#f-radius) | float |  | NO | 0 |  |
| [`box_x`](#f-box_x) | float |  | NO | 0 |  |
| [`box_y`](#f-box_y) | float |  | NO | 0 |  |
| [`box_z`](#f-box_z) | float |  | NO | 0 |  |
| [`box_orientation`](#f-box_orientation) | float |  | NO | 0 |  |
| [`cooldown`](#f-cooldown) | int(10) unsigned |  | NO | 0 |  |
| [`condition_id`](#f-condition_id) | int(10) unsigned |  | NO | 0 |  |
| [`script_id`](#f-script_id) | int(10) unsigned |  | NO | 0 |  |
| [`script_name`](#f-script_name) | varchar(64) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Unique area trigger ID.
- <a id="f-build"></a>**`build`** - Primary Key. Client build version. The core loads the version with the highest build not exceeding the current client build.
- <a id="f-name"></a>**`name`** - Descriptive name (not used by core).
- <a id="f-map_id"></a>**`map_id`** - Map ID where the trigger is located. (see [`map_template`](map_template.md).entry)
- <a id="f-x"></a><a id="f-y"></a><a id="f-z"></a>**`x`, `y`, `z`** - Center point of the trigger volume.
- <a id="f-radius"></a>**`radius`** - For spherical triggers: radius in yards.
- <a id="f-box_x"></a><a id="f-box_y"></a><a id="f-box_z"></a>**`box_x`, `box_y`, `box_z`** - For box-shaped triggers: half-extents on each axis. Most often used when `radius` is not specified.
- <a id="f-box_orientation"></a>**`box_orientation`** - Rotation of the box (in radians).
- <a id="f-cooldown"></a>**`cooldown`** - Time (seconds) before the trigger can fire again.
- <a id="f-condition_id"></a>**`condition_id`** - Condition that must be met for the trigger to activate. (see [`conditions`](conditions.md).condition_entry)
- <a id="f-script_id"></a>**`script_id`** - Script event ID.
- <a id="f-script_name"></a>**`script_name`** - C++ script name for custom logic.
*Referenced by: the other `areatrigger_*` tables.*
