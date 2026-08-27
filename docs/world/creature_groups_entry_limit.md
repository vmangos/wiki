# creature_groups_entry_limit Table

Restricts the number of creatures of a specific template ID that can be part of a group.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`leader_guid`](#f-leader_guid) | int(11) unsigned | PRI | NO |  |  |
| [`creature_id`](#f-creature_id) | int(11) unsigned | PRI | NO |  |  |
| [`min_count`](#f-min_count) | int(11) unsigned |  | NO | 0 |  |
| [`max_count`](#f-max_count) | int(11) unsigned |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-leader_guid"></a>**`leader_guid`** - Primary Key. Group leader GUID. (see [`creature`](creature.md).guid)
- <a id="f-creature_id"></a>**`creature_id`** - Primary Key. Creature template ID. (see [`creature_template`](creature_template.md).entry)
- <a id="f-min_count"></a>**`min_count`** - Minimum number of this creature type required.
- <a id="f-max_count"></a>**`max_count`** - Maximum number of this creature type allowed.
