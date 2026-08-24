# world Table

World-wide persistent variables (e.g. next tick dates for weather/game events).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`map`](#f-map) | int(11) unsigned | PRI | NO | 0 |  |
| [`data`](#f-data) | longtext |  | YES |  |  |

---

## Field Breakdown

- <a id="f-map"></a>**`map`** - Primary Key. Map id.
- <a id="f-data"></a>**`data`** - Serialized map-wide persistent state (weather timers etc.).
