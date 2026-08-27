# group_instance Table

Which instances a group is bound to.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`leader_guid`](#f-leader_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`instance`](#f-instance) | int(11) unsigned | PRI | NO | 0 |  |
| [`permanent`](#f-permanent) | tinyint(1) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-leader_guid"></a>**`leader_guid`** - Primary Key. Group leader owning the bind.
- <a id="f-instance"></a>**`instance`** - Primary Key. Save id ([`instance`](instance.md).id).
- <a id="f-permanent"></a>**`permanent`** - 1 = persistent dungeon/raid bind.
