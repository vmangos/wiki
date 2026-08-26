# spell_threat Table

Defines threat values for spells - how much threat they generate.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`threat`](#f-threat) | float |  | NO | 0 |  |
| [`multiplier`](#f-multiplier) | float |  | NO | 1 |  |
| [`inverse_effect_mask`](#f-inverse_effect_mask) | tinyint(3) unsigned |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned | PRI | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned | PRI | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Spell ID. (see [`spell_template`](spell_template.md).entry)
- <a id="f-threat"></a>**`threat`** - Base threat value.
- <a id="f-multiplier"></a>**`multiplier`** - Threat multiplier.
- <a id="f-inverse_effect_mask"></a>**`inverse_effect_mask`** - Bitmask over effect indexes (`1` = effect 1, `2` = effect 2,
  `4` = effect 3): effects with their bit set are excluded from the flat threat value.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
