# spell_group_stack_rules Table

Defines stacking rules for spell groups.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`group_id`](#f-group_id) | int(11) unsigned | PRI | NO | 0 |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO | 0 |  |
| [`stack_rule`](#f-stack_rule) | tinyint(3) |  | NO | 1 |  |

---

## Field Breakdown

- <a id="f-group_id"></a>**`group_id`** - Primary Key. Group ID. (see [`spell_group`](spell_group.md).group_id)
- <a id="f-build"></a>**`build`** - Primary Key. Client build.
- <a id="f-stack_rule"></a>**`stack_rule`** - Stack rule (`enum SpellGroupStackRule`, `SpellMgr.h`): `0` default (no group handling), `1` exclusive, `3` powerful chain (the less powerful spell of the group is removed); `2` is unimplemented.
