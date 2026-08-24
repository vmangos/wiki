# item_loot Table

Loot rolled inside an openable item, persisted until looted.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`owner_guid`](#f-owner_guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`item_id`](#f-item_id) | int(11) unsigned | PRI | NO | 0 |  |
| [`amount`](#f-amount) | int(11) unsigned |  | NO | 0 |  |
| [`property`](#f-property) | int(11) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. [`item_instance`](item_instance.md).guid owning this rolled loot.
- <a id="f-owner_guid"></a>**`owner_guid`** - Player allowed to loot it.
- <a id="f-item_id"></a>**`item_id`** - Part of the primary key. Contained item entry.
- <a id="f-amount"></a>**`amount`** - Stack count of the contained item.
- <a id="f-property"></a>**`property`** - Random property id of the contained item.
