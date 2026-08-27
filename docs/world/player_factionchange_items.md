# player_factionchange_items Table

Maps items between Alliance and Horde equivalents (faction-specific items).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`alliance_id`](#f-alliance_id) | int(8) | PRI | NO |  |  |
| [`horde_id`](#f-horde_id) | int(8) | PRI | NO |  |  |
| [`comment`](#f-comment) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-alliance_id"></a>**`alliance_id`** - Primary Key. Alliance item ID.; references [`item_template`](item_template.md).entry
- <a id="f-horde_id"></a>**`horde_id`** - Primary Key. Horde item ID.; references [`item_template`](item_template.md).entry
- <a id="f-comment"></a>**`comment`** - Description.
