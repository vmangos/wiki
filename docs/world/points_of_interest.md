# points_of_interest Table

Defines map points of interest (POI) shown on the world map.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`x`](#f-x) | float |  | NO | 0 |  |
| [`y`](#f-y) | float |  | NO | 0 |  |
| [`icon`](#f-icon) | mediumint(8) unsigned |  | NO | 0 |  |
| [`flags`](#f-flags) | mediumint(8) unsigned |  | NO | 0 |  |
| [`data`](#f-data) | mediumint(8) unsigned |  | NO | 0 |  |
| [`icon_name`](#f-icon_name) | text |  | NO |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. POI ID.
- <a id="f-x"></a><a id="f-y"></a>**`x` / `y`** - Map coordinates.
- <a id="f-icon"></a>**`icon`** - Icon ID. (see POI icon definitions.)
- <a id="f-flags"></a>**`flags`** - POI flags.
- <a id="f-data"></a>**`data`** - Additional data.
- <a id="f-icon_name"></a>**`icon_name`** - Name/description.
