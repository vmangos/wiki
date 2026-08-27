# creature_classlevelstats Table

Base statistics for creatures by class and level - health, mana, damage, armor, and primary attributes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO |  |  |
| [`level`](#f-level) | tinyint(3) unsigned | PRI | NO |  |  |
| [`melee_damage`](#f-melee_damage) | float |  | NO | 0 |  |
| [`ranged_damage`](#f-ranged_damage) | float |  | NO | 0 |  |
| [`attack_power`](#f-attack_power) | int(11) |  | NO | 0 |  |
| [`ranged_attack_power`](#f-ranged_attack_power) | int(11) |  | NO | 0 |  |
| [`health`](#f-health) | int(11) |  | NO | 0 |  |
| [`base_health`](#f-base_health) | int(11) |  | NO | 0 |  |
| [`mana`](#f-mana) | int(11) |  | NO | 0 |  |
| [`base_mana`](#f-base_mana) | int(11) |  | NO | 0 |  |
| [`strength`](#f-strength) | int(11) |  | NO | 0 |  |
| [`agility`](#f-agility) | int(11) |  | NO | 0 |  |
| [`stamina`](#f-stamina) | int(11) |  | NO | 0 |  |
| [`intellect`](#f-intellect) | int(11) |  | NO | 0 |  |
| [`spirit`](#f-spirit) | int(11) |  | NO | 0 |  |
| [`armor`](#f-armor) | int(11) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-class"></a>**`class`** (tinyint(3) unsigned) - Primary Key. Creature class (e.g., warrior, mage). (see class IDs (`ChrClasses.dbc`))
- <a id="f-level"></a>**`level`** (tinyint(3) unsigned) - Primary Key. Creature level; rows load per class up to
  the highest `level_max` found in [`creature_template`](creature_template.md) for that class (`ObjectMgr.cpp`).
  Level 0 rows are rejected.
- <a id="f-melee_damage"></a><a id="f-ranged_damage"></a>**`melee_damage`** / **`ranged_damage`** - Base damage values (modified by stats).
- <a id="f-attack_power"></a><a id="f-ranged_attack_power"></a>**`attack_power`** / **`ranged_attack_power`** - Base attack power.
- <a id="f-base_health"></a><a id="f-health"></a>**`health`** / **`base_health`** - Total and base health.
- <a id="f-base_mana"></a><a id="f-mana"></a>**`mana`** / **`base_mana`** - Total and base mana.
- <a id="f-agility"></a><a id="f-intellect"></a><a id="f-stamina"></a><a id="f-strength"></a><a id="f-spirit"></a>**`strength`**, **`agility`**, **`stamina`**, **`intellect`**, **`spirit`** - Primary attributes.
- <a id="f-armor"></a>**`armor`** - Base armor value.
