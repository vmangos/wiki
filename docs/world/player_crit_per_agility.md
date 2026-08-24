# player_crit_per_agility Table

Defines how much melee/ranged critical strike chance (in percent) each class gains per point of agility, scaled by level. Used in the player critical chance calculation.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO |  |  |
| [`level`](#f-level) | tinyint(3) unsigned | PRI | NO |  |  |
| [`rate`](#f-rate) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-class"></a>**`class`** - Part of the composite primary key. Class ID (`1`=Warrior, `2`=Paladin, `3`=Hunter, `4`=Rogue, `5`=Priest, `6`=Death Knight (unused), `7`=Shaman, `8`=Mage, `9`=Warlock, `11`=Druid). (see class IDs (see `ChrClasses.dbc`))
- <a id="f-level"></a>**`level`** - Part of the composite primary key. Player level this rate applies to. Rows with `level` = 0 or above the maximum level are skipped with a DB error.
- <a id="f-rate"></a>**`rate`** - Critical strike chance gained per agility point at this level (percent). Must be positive; invalid values are reported as DB errors.
*Related table: [`player_dodge_per_agility`](player_dodge_per_agility.md)
