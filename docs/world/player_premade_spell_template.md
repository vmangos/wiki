# player_premade_spell_template Table

Additional spell template data for premade characters.

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

- <a id="f-entry"></a>**`entry`** - Primary Key. Premade spell template ID. (see [`player_premade_spell`](player_premade_spell.md).entry)
- <a id="f-class"></a>**`class`** - Class ID.
- <a id="f-level"></a>**`level`** - Level.
- <a id="f-role"></a>**`role`** - Role.
- <a id="f-name"></a>**`name`** - Template name.
