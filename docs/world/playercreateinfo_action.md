# playercreateinfo_action Table

Defines starting action bar layout for each race/class combination.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`race`](#f-race) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`class`](#f-class) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`button`](#f-button) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`action`](#f-action) | int(11) unsigned |  | NO | 0 |  |
| [`type`](#f-type) | smallint(5) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-race"></a>**`race`** - Primary Key. Race ID.; references Player race/class combination.
- <a id="f-class"></a>**`class`** - Primary Key. Class ID.; references Player race/class combination.
- <a id="f-button"></a>**`button`** - Primary Key. Action bar button index.
- <a id="f-action"></a>**`action`** - Spell ID or action ID. (see [`spell_template`](spell_template.md).entry (if spell).)
- <a id="f-type"></a>**`type`** - Action type: `0` spell, `1` C (click), `64` macro, `128` item.
