# player_premade_item_template Table

Defines premade character templates (name, class, level, role).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(10) unsigned | PRI | NO |  |  |
| [`class`](#f-class) | tinyint(3) unsigned |  | NO | 0 |  |
| [`level`](#f-level) | tinyint(3) unsigned |  | NO | 60 |  |
| [`role`](#f-role) | tinyint(3) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(50) |  | YES | '' |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Premade template ID.
- <a id="f-class"></a>**`class`** - Class ID.
- <a id="f-level"></a>**`level`** - Starting level.
- <a id="f-role"></a>**`role`** - Role (e.g., tank, healer, DPS).
- <a id="f-name"></a>**`name`** - Template name.
