# skill_line_ability Table

Defines abilities learned from skill lines (e.g., from professions).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | smallint(5) unsigned | PRI | NO |  |  |
| [`build`](#f-build) | smallint(4) unsigned | PRI | NO |  |  |
| [`skill_id`](#f-skill_id) | int(10) unsigned |  | NO | 0 |  |
| [`spell_id`](#f-spell_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`race_mask`](#f-race_mask) | int(10) unsigned |  | NO | 0 |  |
| [`class_mask`](#f-class_mask) | int(10) unsigned |  | NO | 0 |  |
| [`req_skill_value`](#f-req_skill_value) | int(10) unsigned |  | NO | 0 |  |
| [`superseded_by_spell`](#f-superseded_by_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`learn_on_get_skill`](#f-learn_on_get_skill) | int(10) unsigned |  | NO | 0 |  |
| [`max_value`](#f-max_value) | int(10) unsigned |  | NO | 0 |  |
| [`min_value`](#f-min_value) | int(10) unsigned |  | NO | 0 |  |
| [`req_train_points`](#f-req_train_points) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Ability entry.
- <a id="f-build"></a>**`build`** - Primary Key. Client build.
- <a id="f-skill_id"></a>**`skill_id`** - Skill line ID. (see Skill line definitions.)
- <a id="f-spell_id"></a>**`spell_id`** - Spell granted. (see [`spell_template`](spell_template.md).entry)
- <a id="f-class_mask"></a><a id="f-race_mask"></a>**`race_mask` / `class_mask`** - Race/class restrictions.
- <a id="f-req_skill_value"></a>**`req_skill_value`** - Required skill level.
- <a id="f-superseded_by_spell"></a>**`superseded_by_spell`** - Spell that replaces this one.
- <a id="f-learn_on_get_skill"></a>**`learn_on_get_skill`** - Auto-learn when skill is gained.
- <a id="f-max_value"></a><a id="f-min_value"></a>**`max_value` / `min_value`** - Skill value range.
- <a id="f-req_train_points"></a>**`req_train_points`** - Training points required.
