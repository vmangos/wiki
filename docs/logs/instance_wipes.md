# instance_wipes Table

Logged wipes on boss encounters (duration, attempts).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`mapId`](#f-mapId) | int(10) unsigned | PRI | NO |  |  |
| [`creatureEntry`](#f-creatureEntry) | int(10) unsigned | PRI | NO |  |  |
| [`count`](#f-count) | int(10) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-mapId"></a>**`mapId`** - Primary Key. Instance map.
- <a id="f-creatureEntry"></a>**`creatureEntry`** - Primary Key. Boss/encounter creature entry (from [`creature_template`](../world/creature_template.md).entry).
- <a id="f-count"></a>**`count`** - Wipe count against this encounter.
