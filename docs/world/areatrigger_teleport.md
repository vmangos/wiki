# areatrigger_teleport Table

Defines where area triggers (like dungeon portals) teleport players, and the conditions required to use them.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | varchar(64) |  | NO | '' |  |
| [`message`](#f-message) | varchar(128) |  | NO | '' |  |
| [`required_level`](#f-required_level) | tinyint(3) unsigned |  | NO | 0 |  |
| [`required_condition`](#f-required_condition) | mediumint(8) unsigned |  | NO | 0 |  |
| [`target_map`](#f-target_map) | smallint(5) unsigned |  | NO | 0 |  |
| [`target_position_x`](#f-target_position_x) | float |  | NO | 0 |  |
| [`target_position_y`](#f-target_position_y) | float |  | NO | 0 |  |
| [`target_position_z`](#f-target_position_z) | float |  | NO | 0 |  |
| [`target_orientation`](#f-target_orientation) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Areatrigger ID from [`areatrigger_template`](areatrigger_template.md).entry.
- <a id="f-patch"></a>**`patch`** - Primary Key. Content patch in which this version is active. The core loads the row with the highest patch value not exceeding the current patch. Patches start at 0 (1.2.4) and go to 10 (1.12.1).
- <a id="f-name"></a>**`name`** - Name of the destination. Not used by the core - purely descriptive.
- <a id="f-message"></a>**`message`** - Message sent to the client when the criteria are not met (e.g., "You are not high enough level"). This text is stored in `Areatrigger.db2` in modern clients.
- <a id="f-required_level"></a>**`required_level`** - Minimum character level required.
- <a id="f-required_condition"></a>**`required_condition`** - Condition ID from the [`conditions`](conditions.md) table that must be satisfied.
- <a id="f-target_map"></a>**`target_map`** - Destination map ID. (see [`map_template`](map_template.md).entry)
- <a id="f-target_position_x"></a>**`target_position_x`** - Teleport destination coordinates inside `target_map`.
- <a id="f-target_position_y"></a>**`target_position_y`** - Destination Y coordinate.
- <a id="f-target_position_z"></a>**`target_position_z`** - Destination Z coordinate.
- <a id="f-target_orientation"></a>**`target_orientation`** - Facing direction upon arrival.
