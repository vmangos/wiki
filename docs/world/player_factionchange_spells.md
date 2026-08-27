# player_factionchange_spells Table

Maps spells between Alliance and Horde equivalents (faction-specific spells).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`alliance_id`](#f-alliance_id) | smallint(5) unsigned | PRI | NO |  |  |
| [`horde_id`](#f-horde_id) | smallint(5) unsigned | PRI | NO |  |  |
| [`comment`](#f-comment) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-alliance_id"></a>**`alliance_id`** - Primary Key. Alliance spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-horde_id"></a>**`horde_id`** - Primary Key. Horde spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-comment"></a>**`comment`** - Description.
