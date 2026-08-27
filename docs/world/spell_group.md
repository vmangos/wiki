# spell_group Table

Groups spells together for stack rules and exclusive categories.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`group_id`](#f-group_id) | int(11) unsigned | PRI | NO | 0 |  |
| [`group_spell_id`](#f-group_spell_id) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell_id`](#f-spell_id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned |  | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-group_id"></a>**`group_id`** - Primary Key. Group ID. (see [`spell_group_stack_rules`](spell_group_stack_rules.md).group_id)
- <a id="f-group_spell_id"></a>**`group_spell_id`** - Primary Key. Companion group spell id; ordered by the core but otherwise unused by the current core.
- <a id="f-spell_id"></a>**`spell_id`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
  Note: the core also supports a *negative* value meaning "reference another group" (`SpellMgr.cpp`),
  but the column is `smallint unsigned`, so such rows cannot currently be stored.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
