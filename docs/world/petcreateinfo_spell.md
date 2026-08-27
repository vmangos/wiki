# petcreateinfo_spell Table

Defines spells that a pet knows when created (by creature entry).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`spell1`](#f-spell1) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell2`](#f-spell2) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell3`](#f-spell3) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell4`](#f-spell4) | smallint(5) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Pet creature template entry. (see [`creature_template`](creature_template.md).entry)
- <a id="f-spell1"></a>**`spell1`** - Spells known by the pet type at spawn (per build). (see [`spell_template`](spell_template.md).entry)
- <a id="f-spell2"></a>**`spell2`** - Spells known by the pet type at spawn (per build).
- <a id="f-spell3"></a>**`spell3`** - Spells known by the pet type at spawn (per build).
- <a id="f-spell4"></a>**`spell4`** - Spells known by the pet type at spawn (per build).
- <a id="f-patch_min"></a>**`patch_min`** - Progression window for this spell set.
- <a id="f-patch_max"></a>**`patch_max`** - Progression window for this spell set.
