# pet_levelstats Table

Base stats for pets by creature entry and level.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO |  |  |
| [`level`](#f-level) | tinyint(3) unsigned | PRI | NO |  |  |
| [`health`](#f-health) | smallint(5) unsigned |  | NO | 0 |  |
| [`mana`](#f-mana) | smallint(5) unsigned |  | NO | 0 |  |
| [`armor`](#f-armor) | int(10) unsigned |  | NO | 0 |  |
| [`dmg_min`](#f-dmg_min) | float |  | NO | 0 |  |
| [`dmg_max`](#f-dmg_max) | float |  | NO | 0 |  |
| [`strength`](#f-strength) | smallint(5) unsigned |  | NO | 0 |  |
| [`agility`](#f-agility) | smallint(5) unsigned |  | NO | 0 |  |
| [`stamina`](#f-stamina) | smallint(5) unsigned |  | NO | 0 |  |
| [`intellect`](#f-intellect) | smallint(5) unsigned |  | NO | 0 |  |
| [`spirit`](#f-spirit) | smallint(5) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature entry (pet family). (see [`creature_template`](creature_template.md).entry)
- <a id="f-level"></a>**`level`** - Primary Key. Pet level.
- <a id="f-health"></a><a id="f-mana"></a>**`health` / `mana`** - Base health/mana.
- <a id="f-armor"></a>**`armor`** - Base armor.
- <a id="f-dmg_max"></a><a id="f-dmg_min"></a>**`dmg_min` / `dmg_max`** - Base damage range.
- <a id="f-agility"></a><a id="f-intellect"></a><a id="f-stamina"></a><a id="f-strength"></a><a id="f-spirit"></a>**`strength`**, **`agility`**, **`stamina`**, **`intellect`**, **`spirit`** - Primary attributes.
