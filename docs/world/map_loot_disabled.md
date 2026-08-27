# map_loot_disabled Table

Disables loot from specific maps (e.g., to prevent abuse).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`map_id`](#f-map_id) | int(11) | PRI | NO | 0 |  |
| [`comment`](#f-comment) | varchar(255) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-map_id"></a>**`map_id`** - Primary Key. Map ID.
- <a id="f-comment"></a>**`comment`** - Reason for disabling loot.
