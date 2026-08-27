# spell_proc_event Table

Defines proc event conditions for spells (e.g., on hit, on crit, on spellcast).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`SchoolMask`](#f-SchoolMask) | tinyint(4) unsigned |  | NO | 0 |  |
| [`SpellFamilyName`](#f-SpellFamilyName) | smallint(5) unsigned |  | NO | 0 |  |
| [`SpellFamilyMask0`](#f-SpellFamilyMask0) | bigint(40) unsigned |  | NO | 0 |  |
| [`SpellFamilyMask1`](#f-SpellFamilyMask1) | bigint(40) unsigned |  | NO | 0 |  |
| [`SpellFamilyMask2`](#f-SpellFamilyMask2) | bigint(40) unsigned |  | NO | 0 |  |
| [`procFlags`](#f-procFlags) | int(10) unsigned |  | NO | 0 |  |
| [`procEx`](#f-procEx) | int(10) unsigned |  | NO | 0 |  |
| [`ppmRate`](#f-ppmRate) | float |  | NO | 0 |  |
| [`CustomChance`](#f-CustomChance) | float |  | NO | 0 |  |
| [`Cooldown`](#f-Cooldown) | int(10) unsigned |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned | PRI | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned | PRI | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-SchoolMask"></a>**`SchoolMask`** - School mask.
- <a id="f-SpellFamilyName"></a>**`SpellFamilyName`** - Family name.
- <a id="f-SpellFamilyMask0"></a><a id="f-SpellFamilyMask1"></a><a id="f-SpellFamilyMask2"></a>**`SpellFamilyMask0-2`** - Family flags.
- <a id="f-procFlags"></a>**`procFlags`** - Proc flags (e.g., on hit, on crit).
- <a id="f-procEx"></a>**`procEx`** - Extra proc condition bits.
- <a id="f-ppmRate"></a>**`ppmRate`** - Procs per minute rate.
- <a id="f-CustomChance"></a>**`CustomChance`** - Custom proc chance.
- <a id="f-Cooldown"></a>**`Cooldown`** - Cooldown between procs (ms).
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
