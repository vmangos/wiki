# character_stats Table

Cached lifetime statistics shown in the character sheet (kills, honor, quest count, etc.).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`max_health`](#f-max_health) | int(10) unsigned |  | NO | 0 |  |
| [`max_power1`](#f-max_power1) | int(10) unsigned |  | NO | 0 |  |
| [`max_power2`](#f-max_power2) | int(10) unsigned |  | NO | 0 |  |
| [`max_power3`](#f-max_power3) | int(10) unsigned |  | NO | 0 |  |
| [`max_power4`](#f-max_power4) | int(10) unsigned |  | NO | 0 |  |
| [`max_power5`](#f-max_power5) | int(10) unsigned |  | NO | 0 |  |
| [`max_power6`](#f-max_power6) | int(10) unsigned |  | NO | 0 |  |
| [`max_power7`](#f-max_power7) | int(10) unsigned |  | NO | 0 |  |
| [`strength`](#f-strength) | float |  | NO | 0 |  |
| [`agility`](#f-agility) | float |  | NO | 0 |  |
| [`stamina`](#f-stamina) | float |  | NO | 0 |  |
| [`intellect`](#f-intellect) | float |  | NO | 0 |  |
| [`spirit`](#f-spirit) | float |  | NO | 0 |  |
| [`armor`](#f-armor) | int(10) |  | NO | 0 |  |
| [`holy_res`](#f-holy_res) | int(10) |  | NO | 0 |  |
| [`fire_res`](#f-fire_res) | int(10) |  | NO | 0 |  |
| [`nature_res`](#f-nature_res) | int(10) |  | NO | 0 |  |
| [`frost_res`](#f-frost_res) | int(10) |  | NO | 0 |  |
| [`shadow_res`](#f-shadow_res) | int(10) |  | NO | 0 |  |
| [`arcane_res`](#f-arcane_res) | int(10) |  | NO | 0 |  |
| [`block_chance`](#f-block_chance) | float |  | NO | 0 |  |
| [`dodge_chance`](#f-dodge_chance) | float |  | NO | 0 |  |
| [`parry_chance`](#f-parry_chance) | float |  | NO | 0 |  |
| [`crit_chance`](#f-crit_chance) | float |  | NO | 0 |  |
| [`ranged_crit_chance`](#f-ranged_crit_chance) | float |  | NO | 0 |  |
| [`spell_crit_chance`](#f-spell_crit_chance) | float |  | NO | 0 |  |
| [`attack_power`](#f-attack_power) | int(10) unsigned |  | NO | 0 |  |
| [`ranged_attack_power`](#f-ranged_attack_power) | int(10) unsigned |  | NO | 0 |  |
| [`spell_damage`](#f-spell_damage) | int(10) unsigned |  | NO | 0 |  |
| [`spell_healing`](#f-spell_healing) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-max_health"></a>**`max_health`** - Cached maximum health.
- <a id="f-max_power1"></a>**`max_power1`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-max_power2"></a>**`max_power2`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-max_power3"></a>**`max_power3`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-max_power4"></a>**`max_power4`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-max_power5"></a>**`max_power5`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-max_power6"></a>**`max_power6`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-max_power7"></a>**`max_power7`** - Max power for power type `N` (1=mana, 2=rage, 3=focus, 4=energy, 5=happiness; power types 6 and 7 are unused in the 1.12 client).
- <a id="f-strength"></a>**`strength`** - Cached base attributes.
- <a id="f-agility"></a>**`agility`** - Cached base attributes.
- <a id="f-stamina"></a>**`stamina`** - Cached base attributes.
- <a id="f-intellect"></a>**`intellect`** - Cached base attributes.
- <a id="f-spirit"></a>**`spirit`** - Cached base attributes.
- <a id="f-armor"></a>**`armor`** - Total armor value.
- <a id="f-holy_res"></a>**`holy_res`** - Cached Holy resistance.
- <a id="f-fire_res"></a>**`fire_res`** - Cached Fire resistance.
- <a id="f-nature_res"></a>**`nature_res`** - Cached Nature resistance.
- <a id="f-frost_res"></a>**`frost_res`** - Cached Frost resistance.
- <a id="f-shadow_res"></a>**`shadow_res`** - Cached Shadow resistance.
- <a id="f-arcane_res"></a>**`arcane_res`** - Cached Arcane resistance.
- <a id="f-block_chance"></a>**`block_chance`** - Cached avoidance percentages.
- <a id="f-dodge_chance"></a>**`dodge_chance`** - Cached avoidance percentages.
- <a id="f-parry_chance"></a>**`parry_chance`** - Cached avoidance percentages.
- <a id="f-crit_chance"></a>**`crit_chance`** - Cached crit percentages.
- <a id="f-ranged_crit_chance"></a>**`ranged_crit_chance`** - Cached crit percentages.
- <a id="f-spell_crit_chance"></a>**`spell_crit_chance`** - Cached crit percentages.
- <a id="f-attack_power"></a>**`attack_power`** - Cached attack power.
- <a id="f-ranged_attack_power"></a>**`ranged_attack_power`** - Cached attack power.
- <a id="f-spell_damage"></a>**`spell_damage`** - Cached bonus spell damage/healing.
- <a id="f-spell_healing"></a>**`spell_healing`** - Cached bonus spell damage/healing.
