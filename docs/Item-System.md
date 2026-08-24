# Item System

How items are defined and wired together. The master table is
[`item_template`](world/item_template.md); every physical item in play is an
[`item_instance`](characters/item_instance.md) row in the characters database.

---

## Item Classes

The full `class` table (0-15, from `enum ItemClass`) lives on the
[`item_template`](world/item_template.md) page together with the rest of its columns.

## Field Groups of [`item_template`](world/item_template.md)

| Group | Fields | Purpose |
| :--- | :--- | :--- |
| Identity | `entry`, `patch`, `class`, `subclass`, `name`, `displayid`, quality/inventory | what it *is* and looks like |
| Requirements | `ItemLevel`, `RequiredLevel`, `RequiredSkill`, `RequiredSpell`, `RequiredReputation*`, `AllowedClasses`? | who can use it |
| Combat | `armor`, `block`, weapon damage fields (`dmg_min1..5`, `dmg_type1..5`, delay), stat blocks (`stat_type1..10`, `stat_value1..10`) | combat contribution |
| Resistances | `holy_res` … `arcane_res` | passive resists |
| Spells | `spellid_1..5`, `spelltrigger_1..5`, `spellcharges_*`, `spellcooldown_*`, `spellcategory*` | on-use/on-equip effects |
| Enchant / disenchant | `RandomProperty` group id, `DisenchantID` | see below and [Loot System](Loot-System.md) |
| Economy | `BuyPrice`, `SellPrice`, `MaxCount`, `BuyCount`, vendor references via [`npc_vendor`](world/npc_vendor.md) | trade rules |
| Loot containers | [`item_loot`](characters/item_loot.md) via [`item_loot_template`](world/item_loot_template.md) | clams etc. |

### Random Properties

[`item_template`](world/item_template.md).RandomProperty selects a weighted pool in
[`item_enchantment_template`](world/item_enchantment_template.md); one entry of that pool becomes
the item's `random_property_id`.

Column-level details (stat ids, spell triggers, bonding, and the full
[flags table](world/item_template.md)) live on the
[`item_template`](world/item_template.md) page.

## Wiring to Other Systems

- **Vendors**: [`npc_vendor`](world/npc_vendor.md)/[`npc_vendor_template`](world/npc_vendor_template.md)
  reference item entries; rows may carry a [condition](world/conditions.md).
- **Loot**: every `*_loot_template.item` must exist here - the loader reports missing ones.
- **Quests**: `quest_template.ReqItemId*` / `RewItemId*`.
- **Forbidden items**: [`forbidden_items`](world/forbidden_items.md) hides items per
  [progression patch](Progression-System.md), also filtering loot rolls.
- **Instances**: each owned copy is an [`item_instance`](characters/item_instance.md); charges/durability live there, not in
  the template.

---

## Related Pages

- [Loot System](Loot-System.md)
- [Mail System](Mail-System.md) - attachments
