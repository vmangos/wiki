# item_enchantment_template Table

Defines random enchantments for items (e.g., from `random_property` fields).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`ench`](#f-ench) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`chance`](#f-chance) | float unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned | PRI | NO | 10 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Random-property group id referenced from
  [`item_template`](item_template.md) `RandomProperty`. All rows sharing an entry form one weighted pool.
- <a id="f-ench"></a>**`ench`** - Primary Key. Enchantment/property id; rolled ids must exist in
  `ItemRandomProperties.dbc`.
- <a id="f-chance"></a>**`chance`** - Relative weight (0-100). The roller normalises by the pool total:
  `roll = rand(0..total)`, then walks rows cumulatively, so weights need not sum to 100.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
---

## Rolling Mechanic

`GetItemEnchantMod()` (`src/game/ItemEnchantmentMgr.cpp`) picks one row per crafted/rolled item:

1. Sum all `chance` values of the pool.
2. Roll uniformly in `[0, total)`.
3. Return the first `ench` whose cumulative weight reaches the roll.

Missing pools log *"Item RandomProperty id #%u used in [`item_template`](item_template.md)
but it doesn't have records..."*. Rows with `chance` outside `(0,100]` are skipped at load.

The chosen id lands in [`item_instance.random_property_id`](../characters/item_instance.md).
