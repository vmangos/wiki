# character_homebind Table

Home bind position (hearthstone destination) per character.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`map`](#f-map) | int(11) unsigned |  | NO | 0 |  |
| [`zone`](#f-zone) | int(11) unsigned |  | NO | 0 |  |
| [`position_x`](#f-position_x) | float |  | NO | 0 |  |
| [`position_y`](#f-position_y) | float |  | NO | 0 |  |
| [`position_z`](#f-position_z) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-map"></a>**`map`** - Map of the home bind (hearthstone destination).
- <a id="f-zone"></a>**`zone`** - Zone id of the bind area.
- <a id="f-position_x"></a>**`position_x`** - Bind coordinates inside `map`.
- <a id="f-position_y"></a>**`position_y`** - Home bind Y coordinate.
- <a id="f-position_z"></a>**`position_z`** - Home bind Z coordinate.
