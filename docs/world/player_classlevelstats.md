# player_classlevelstats Table

Base health and mana per class/level.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO |  |  |
| [`level`](#f-level) | tinyint(3) unsigned | PRI | NO |  |  |
| [`basehp`](#f-basehp) | smallint(5) unsigned |  | NO |  |  |
| [`basemana`](#f-basemana) | smallint(5) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-class"></a>**`class`** - Primary Key. Class ID.
- <a id="f-level"></a>**`level`** - Primary Key. Character level.
- <a id="f-basehp"></a>**`basehp`** - Base health.
- <a id="f-basemana"></a>**`basemana`** - Base mana.
