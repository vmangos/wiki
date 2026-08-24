# playercreateinfo Table

Defines starting location for each race/class combination.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`race`](#f-race) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`map`](#f-map) | smallint(5) unsigned |  | NO | 0 |  |
| [`zone`](#f-zone) | mediumint(8) unsigned |  | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |
| [`orientation`](#f-orientation) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-race"></a>**`race`** - Part of the primary key. Race-class pair this starting definition belongs to.
- <a id="f-class"></a>**`class`** - Part of the primary key. Race-class pair this starting definition belongs to.
- <a id="f-map"></a>**`map`** - Starting map and zone ids.
- <a id="f-zone"></a>**`zone`** - Starting map and zone ids. (see `AreaTable.dbc`)
- <a id="f-position_x"></a>**`position_x`** - Starting position X coordinate.
- <a id="f-position_y"></a>**`position_y`** - Starting position Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Starting position Z coordinate.
- <a id="f-orientation"></a>**`orientation`** - Facing direction.
