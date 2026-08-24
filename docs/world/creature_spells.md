# creature_spells Table

Defines spell lists for creatures - up to 8 spells with probabilities, targets, delays, and repeat intervals.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(11) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | varchar(255) |  | NO | '' |  |
| `spellId_1` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_1` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_1` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_1` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_1` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_1` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_1` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_1` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_1` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_1` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_1` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_2` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_2` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_2` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_2` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_2` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_2` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_2` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_2` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_2` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_2` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_2` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_3` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_3` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_3` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_3` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_3` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_3` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_3` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_3` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_3` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_3` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_3` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_4` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_4` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_4` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_4` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_4` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_4` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_4` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_4` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_4` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_4` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_4` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_5` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_5` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_5` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_5` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_5` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_5` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_5` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_5` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_5` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_5` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_5` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_6` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_6` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_6` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_6` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_6` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_6` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_6` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_6` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_6` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_6` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_6` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_7` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_7` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_7` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_7` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_7` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_7` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_7` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_7` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_7` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_7` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_7` | mediumint(8) unsigned |  | NO | 0 |  |
| `spellId_8` | smallint(5) unsigned |  | NO | 0 |  |
| `probability_8` | tinyint(3) unsigned |  | NO | 100 |  |
| `castTarget_8` | tinyint(2) unsigned |  | NO | 1 |  |
| `targetParam1_8` | smallint(5) unsigned |  | NO | 0 |  |
| `targetParam2_8` | smallint(5) unsigned |  | NO | 0 |  |
| `castFlags_8` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMin_8` | smallint(5) unsigned |  | NO | 0 |  |
| `delayInitialMax_8` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMin_8` | smallint(5) unsigned |  | NO | 0 |  |
| `delayRepeatMax_8` | smallint(5) unsigned |  | NO | 0 |  |
| `scriptId_8` | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature template ID. (see [`creature_template`](creature_template.md).entry)
- <a id="f-name"></a>**`name`** - Descriptive name for the spell list.
- For each spell slot (1-8):
  - **`spellId_N`** - Spell ID to cast ([`spell_template`](spell_template.md).entry).
  - **`probability_N`** - Chance (0-100) to use this spell.
  - **`castTarget_N`** - Target selection type.
  - **`targetParam1/2_N`** - Target parameters.
  - **`castFlags_N`** - Cast flags.
  - **`delayInitialMin/Max_N`** - Initial cast delay range (seconds).
  - **`delayRepeatMin/Max_N`** - Repeat cast delay range (seconds).
  - **`scriptId_N`** - Script to execute on cast.
