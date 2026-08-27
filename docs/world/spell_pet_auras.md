# spell_pet_auras Table

Defines auras that are applied to specific pet types when a spell is cast.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`spell`](#f-spell) | smallint(5) unsigned | PRI | NO |  |  |
| [`pet`](#f-pet) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`aura`](#f-aura) | mediumint(8) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-spell"></a>**`spell`** - Primary Key. Spell ID.; references [`spell_template`](spell_template.md).entry
- <a id="f-pet"></a>**`pet`** - Primary Key. Pet entry (creature template). (see [`creature_template`](creature_template.md).entry)
- <a id="f-aura"></a>**`aura`** - Aura spell ID.; references [`spell_template`](spell_template.md).entry
