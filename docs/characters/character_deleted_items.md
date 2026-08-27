# character_deleted_items Table

Items deleted from a character, kept for restoration purposes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  | auto_increment |
| [`player_guid`](#f-player_guid) | int(11) unsigned | MUL | NO | 0 |  |
| [`item_id`](#f-item_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`stack_count`](#f-stack_count) | mediumint(8) unsigned |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Row id.
- <a id="f-player_guid"></a>**`player_guid`** - Owner who deleted the item.
- <a id="f-item_id"></a>**`item_id`** - Item template entry that was destroyed.
- <a id="f-stack_count"></a>**`stack_count`** - How many items of that entry were deleted.
