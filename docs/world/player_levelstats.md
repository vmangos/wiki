# player_levelstats Table

Defines base primary attributes (strength, agility, stamina, intellect, spirit) for each race/class/level combination.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`race`](#f-race) | tinyint(3) unsigned | PRI | NO |  |  |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO |  |  |
| [`level`](#f-level) | tinyint(3) unsigned | PRI | NO |  |  |
| [`str`](#f-str) | tinyint(3) unsigned |  | NO |  |  |
| [`agi`](#f-agi) | tinyint(3) unsigned |  | NO |  |  |
| [`sta`](#f-sta) | tinyint(3) unsigned |  | NO |  |  |
| [`inte`](#f-inte) | tinyint(3) unsigned |  | NO |  |  |
| [`spi`](#f-spi) | tinyint(3) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-race"></a>**`race`** - Primary Key. Race ID.; references Player race/class combination.
- <a id="f-class"></a>**`class`** - Primary Key. Class ID.; references Player race/class combination.
- <a id="f-level"></a>**`level`** - Primary Key. Character level.
- <a id="f-str"></a>**`str`** - Base strength.
- <a id="f-agi"></a>**`agi`** - Base agility.
- <a id="f-sta"></a>**`sta`** - Base stamina.
- <a id="f-inte"></a>**`inte`** - Base intellect.
- <a id="f-spi"></a>**`spi`** - Base spirit.
