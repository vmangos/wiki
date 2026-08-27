# spell_area Table

Defines spells that apply auras when entering a specific area, based on quests, race, gender, etc.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`spell`](#f-spell) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`area`](#f-area) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`quest_start`](#f-quest_start) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`quest_start_active`](#f-quest_start_active) | tinyint(1) unsigned | PRI | NO | 0 |  |
| [`quest_end`](#f-quest_end) | mediumint(8) unsigned |  | NO | 0 |  |
| [`aura_spell`](#f-aura_spell) | smallint(6) | PRI | NO | 0 |  |
| [`racemask`](#f-racemask) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`gender`](#f-gender) | tinyint(1) unsigned | PRI | NO | 2 |  |
| [`autocast`](#f-autocast) | tinyint(1) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-spell"></a>**`spell`** - Primary Key. Spell that applies the aura (→ [`spell_template`](spell_template.md).entry).
- <a id="f-area"></a>**`area`** - Primary Key. Zone/area ID. (see `AreaTable.dbc`)
- <a id="f-quest_start"></a>**`quest_start`** - Primary Key. Quest that must be active (from [`quest_template`](quest_template.md).entry).
- <a id="f-quest_start_active"></a>**`quest_start_active`** - Primary Key. If `1`, quest must be active; if `0`, quest must be complete.
- <a id="f-quest_end"></a>**`quest_end`** - Quest that ends the aura (from [`quest_template`](quest_template.md).entry).
- <a id="f-aura_spell"></a>**`aura_spell`** - Primary Key. Aura requirement: positive = aura must be present, negative = aura must be absent.
- <a id="f-racemask"></a>**`racemask`** - Primary Key. Race mask.
- <a id="f-gender"></a>**`gender`** - Primary Key. `0` male, `1` female, `2` both.
- <a id="f-autocast"></a>**`autocast`** - If `1`, spell is auto-applied on entering the area; if `0`, it is only allowed to be cast there.
