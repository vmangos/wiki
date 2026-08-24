# spell_elixir Table

Defines elixir spells and their mask (battle/guardian) for stacking rules.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`mask`](#f-mask) | tinyint(1) unsigned |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned |  | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-mask"></a>**`mask`** - Elixir mask: `1` battle, `2` guardian.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
