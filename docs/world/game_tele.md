# game_tele Table

Defines teleport locations for the `.tele` command (GM teleport).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO |  | auto_increment |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |
| [`map`](#f-map) | smallint(5) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(100) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key, auto-increment.
- <a id="f-position_x"></a>**`position_x`** - Destination X coordinate.
- <a id="f-position_y"></a>**`position_y`** - Destination Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Destination Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Facing direction.
- <a id="f-map"></a>**`map`** - Destination map id.
- <a id="f-name"></a>**`name`** - Teleport shortcut name usable with `.tele <name>`.
