# pet_spell_data Table

Spell data for pets - up to 4 spells per pet entry.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(10) unsigned | PRI | NO |  |  |
| [`build`](#f-build) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`spell_id1`](#f-spell_id1) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell_id2`](#f-spell_id2) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell_id3`](#f-spell_id3) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell_id4`](#f-spell_id4) | smallint(5) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Part of the primary key. Pet creature entry the set applies to. (see [`creature_template`](creature_template.md).entry)
- <a id="f-build"></a>**`build`** - Primary Key. Client build version.
- <a id="f-spell_id1"></a>**`spell_id1`** - Spells in this pet spell slot set. (see [`spell_template`](spell_template.md).entry)
- <a id="f-spell_id2"></a>**`spell_id2`** - Spells in this pet spell slot set.
- <a id="f-spell_id3"></a>**`spell_id3`** - Spells in this pet spell slot set.
- <a id="f-spell_id4"></a>**`spell_id4`** - Spells in this pet spell slot set.
