# spell_chain Table

Defines spell ranks and their chain relationships (e.g., rank 1, rank 2, etc.).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`spell_id`](#f-spell_id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`prev_spell`](#f-prev_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`first_spell`](#f-first_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`rank`](#f-rank) | tinyint(4) |  | NO | 0 |  |
| [`req_spell`](#f-req_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) | PRI | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) | PRI | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-spell_id"></a>**`spell_id`** - Primary Key. Spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-prev_spell"></a>**`prev_spell`** - Previous rank spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-first_spell"></a>**`first_spell`** - First rank spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-rank"></a>**`rank`** - Rank number.
- <a id="f-req_spell"></a>**`req_spell`** - Required spell to learn this rank.; references [`spell_template`](spell_template.md).entry
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
