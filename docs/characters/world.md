# world Table

Persistent per-map script state (the `data` blob holds map-script instance data, e.g. boss/encounter variables
written by `InstanceData`).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`map`](#f-map) | int(11) unsigned | PRI | NO | 0 |  |
| [`data`](#f-data) | longtext |  | YES |  |  |

---

## Field Breakdown

- <a id="f-map"></a>**`map`** - Primary Key. Map id.
- <a id="f-data"></a>**`data`** - Serialized map-wide persistent state (map-script `InstanceData` save blob).
