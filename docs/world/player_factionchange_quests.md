# player_factionchange_quests Table

Maps quests between Alliance and Horde equivalents.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`alliance_id`](#f-alliance_id) | int(8) | PRI | NO |  |  |
| [`horde_id`](#f-horde_id) | int(8) | PRI | NO |  |  |
| [`comment`](#f-comment) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-alliance_id"></a>**`alliance_id`** - Primary Key. Alliance quest ID.; references [`quest_template`](quest_template.md).entry
- <a id="f-horde_id"></a>**`horde_id`** - Primary Key. Horde quest ID.; references [`quest_template`](quest_template.md).entry
- <a id="f-comment"></a>**`comment`** - Description.
