# item_instance Table

One row per physical item in the world: owner, enchantments, charges, durability, flags.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO | 0 |  |
| [`item_id`](#f-item_id) | mediumint(8) unsigned | MUL | NO | 0 |  |
| [`owner_guid`](#f-owner_guid) | int(10) unsigned | MUL | NO | 0 |  |
| [`creator_guid`](#f-creator_guid) | int(10) unsigned |  | NO | 0 |  |
| [`gift_creator_guid`](#f-gift_creator_guid) | int(10) unsigned |  | NO | 0 |  |
| [`count`](#f-count) | int(10) unsigned |  | NO | 1 |  |
| [`duration`](#f-duration) | int(10) |  | NO | 0 |  |
| [`charges`](#f-charges) | tinytext |  | YES |  |  |
| [`flags`](#f-flags) | mediumint(8) unsigned |  | NO | 0 |  |
| [`enchantments`](#f-enchantments) | text |  | NO |  |  |
| [`random_property_id`](#f-random_property_id) | smallint(5) |  | NO | 0 |  |
| [`durability`](#f-durability) | smallint(5) unsigned |  | NO | 0 |  |
| [`text`](#f-text) | int(10) unsigned |  | NO | 0 |  |
| [`generated_loot`](#f-generated_loot) | tinyint(4) |  | YES | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Item GUID. Referenced from [`character_inventory`](character_inventory.md).guid, [`mail_items`](mail_items.md).item_guid, [`auction`](auction.md).item_guid and [`character_gifts`](character_gifts.md).item_guid.
- <a id="f-item_id"></a>**`item_id`** - [`item_template`](../world/item_template.md).entry.
- <a id="f-owner_guid"></a>**`owner_guid`** - Character that currently possesses the item ([`characters`](characters.md).guid).
- <a id="f-creator_guid"></a>**`creator_guid`** - Character that crafted the item.
- <a id="f-gift_creator_guid"></a>**`gift_creator_guid`** - Character that gift-wrapped the item.
- <a id="f-count"></a>**`count`** - Stack size.
- <a id="f-duration"></a>**`duration`** - Remaining duration seconds for temp items.
- <a id="f-charges"></a>**`charges`** - Space-separated remaining charges per charged spell.
- <a id="f-flags"></a>**`flags`** - Item state flags (`ItemDynFlags`, `ItemDefines.h`): soulbound, wrapped/gift-wrapped, unlocked, readable…
- <a id="f-enchantments"></a>**`enchantments`** - Enchantment triplets `(id, duration, charges)` concatenated for each slot.
- <a id="f-random_property_id"></a>**`random_property_id`** - Random enchant suffix id (rolled from
  [`item_enchantment_template`](../world/item_enchantment_template.md).ench where `entry` = the item's `random_property`) chosen at creation.
- <a id="f-durability"></a>**`durability`** - Current durability points.
- <a id="f-text"></a>**`text`** - Readable-book text id (from [`item_text`](item_text.md).id).
- <a id="f-generated_loot"></a>**`generated_loot`** - Loot already rolled and stored in [`item_loot`](item_loot.md) (rows keyed by the item's guid).
