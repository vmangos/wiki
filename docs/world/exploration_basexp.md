# exploration_basexp Table

Base experience points awarded for discovering new areas (exploration XP).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`level`](#f-level) | tinyint(4) | PRI | NO | 0 |  |
| [`basexp`](#f-basexp) | mediumint(9) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-level"></a>**`level`** - Primary Key. Character level.
- <a id="f-basexp"></a>**`basexp`** - Base XP awarded for discovering a new zone at that level.
