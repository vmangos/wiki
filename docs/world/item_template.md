# item_template Table

Defines base properties for all items - stats, spells, quality, and behavior.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`class`](#f-class) | tinyint(3) unsigned | MUL | NO | 0 |  |
| [`subclass`](#f-subclass) | tinyint(3) unsigned |  | NO | 0 |  |
| [`name`](#f-name) | varchar(255) |  | NO | '' |  |
| [`description`](#f-description) | varchar(255) |  | NO | '' |  |
| [`display_id`](#f-display_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`quality`](#f-quality) | tinyint(3) unsigned |  | NO | 0 |  |
| [`flags`](#f-flags) | int(10) unsigned |  | NO | 0 |  |
| [`buy_count`](#f-buy_count) | tinyint(3) unsigned |  | NO | 1 |  |
| [`buy_price`](#f-buy_price) | int(10) unsigned |  | NO | 0 |  |
| [`sell_price`](#f-sell_price) | int(10) unsigned |  | NO | 0 |  |
| [`inventory_type`](#f-inventory_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`allowable_class`](#f-allowable_class) | mediumint(9) |  | NO | -1 |  |
| [`allowable_race`](#f-allowable_race) | mediumint(9) |  | NO | -1 |  |
| [`item_level`](#f-item_level) | tinyint(3) unsigned |  | NO | 0 |  |
| [`required_level`](#f-required_level) | tinyint(3) unsigned |  | NO | 0 |  |
| [`required_skill`](#f-required_skill) | smallint(5) unsigned |  | NO | 0 |  |
| [`required_skill_rank`](#f-required_skill_rank) | smallint(5) unsigned |  | NO | 0 |  |
| [`required_spell`](#f-required_spell) | smallint(5) unsigned |  | NO | 0 |  |
| [`required_honor_rank`](#f-required_honor_rank) | mediumint(8) unsigned |  | NO | 0 |  |
| [`required_city_rank`](#f-required_city_rank) | mediumint(8) unsigned |  | NO | 0 |  |
| [`required_reputation_faction`](#f-required_reputation_faction) | smallint(5) unsigned |  | NO | 0 |  |
| [`required_reputation_rank`](#f-required_reputation_rank) | smallint(5) unsigned |  | NO | 0 |  |
| [`max_count`](#f-max_count) | smallint(5) unsigned |  | NO | 0 |  |
| [`stackable`](#f-stackable) | smallint(5) unsigned |  | NO | 1 |  |
| [`container_slots`](#f-container_slots) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_type1`](#f-stat_type1) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value1`](#f-stat_value1) | smallint(6) |  | NO | 0 |  |
| [`stat_type2`](#f-stat_type2) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value2`](#f-stat_value2) | smallint(6) |  | NO | 0 |  |
| [`stat_type3`](#f-stat_type3) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value3`](#f-stat_value3) | smallint(6) |  | NO | 0 |  |
| [`stat_type4`](#f-stat_type4) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value4`](#f-stat_value4) | smallint(6) |  | NO | 0 |  |
| [`stat_type5`](#f-stat_type5) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value5`](#f-stat_value5) | smallint(6) |  | NO | 0 |  |
| [`stat_type6`](#f-stat_type6) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value6`](#f-stat_value6) | smallint(6) |  | NO | 0 |  |
| [`stat_type7`](#f-stat_type7) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value7`](#f-stat_value7) | smallint(6) |  | NO | 0 |  |
| [`stat_type8`](#f-stat_type8) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value8`](#f-stat_value8) | smallint(6) |  | NO | 0 |  |
| [`stat_type9`](#f-stat_type9) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value9`](#f-stat_value9) | smallint(6) |  | NO | 0 |  |
| [`stat_type10`](#f-stat_type10) | tinyint(3) unsigned |  | NO | 0 |  |
| [`stat_value10`](#f-stat_value10) | smallint(6) |  | NO | 0 |  |
| [`delay`](#f-delay) | smallint(5) unsigned |  | NO | 1000 |  |
| [`range_mod`](#f-range_mod) | float |  | NO | 0 |  |
| [`ammo_type`](#f-ammo_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`dmg_min1`](#f-dmg_min1) | float |  | NO | 0 |  |
| [`dmg_max1`](#f-dmg_max1) | float |  | NO | 0 |  |
| [`dmg_type1`](#f-dmg_type1) | tinyint(3) unsigned |  | NO | 0 |  |
| [`dmg_min2`](#f-dmg_min2) | float |  | NO | 0 |  |
| [`dmg_max2`](#f-dmg_max2) | float |  | NO | 0 |  |
| [`dmg_type2`](#f-dmg_type2) | tinyint(3) unsigned |  | NO | 0 |  |
| [`dmg_min3`](#f-dmg_min3) | float |  | NO | 0 |  |
| [`dmg_max3`](#f-dmg_max3) | float |  | NO | 0 |  |
| [`dmg_type3`](#f-dmg_type3) | tinyint(3) unsigned |  | NO | 0 |  |
| [`dmg_min4`](#f-dmg_min4) | float |  | NO | 0 |  |
| [`dmg_max4`](#f-dmg_max4) | float |  | NO | 0 |  |
| [`dmg_type4`](#f-dmg_type4) | tinyint(3) unsigned |  | NO | 0 |  |
| [`dmg_min5`](#f-dmg_min5) | float |  | NO | 0 |  |
| [`dmg_max5`](#f-dmg_max5) | float |  | NO | 0 |  |
| [`dmg_type5`](#f-dmg_type5) | tinyint(3) unsigned |  | NO | 0 |  |
| [`block`](#f-block) | mediumint(8) unsigned |  | NO | 0 |  |
| [`armor`](#f-armor) | smallint(5) |  | NO | 0 |  |
| [`holy_res`](#f-holy_res) | smallint(5) |  | NO | 0 |  |
| [`fire_res`](#f-fire_res) | smallint(5) |  | NO | 0 |  |
| [`nature_res`](#f-nature_res) | smallint(5) |  | NO | 0 |  |
| [`frost_res`](#f-frost_res) | smallint(5) |  | NO | 0 |  |
| [`shadow_res`](#f-shadow_res) | smallint(5) |  | NO | 0 |  |
| [`arcane_res`](#f-arcane_res) | smallint(5) |  | NO | 0 |  |
| [`spellid_1`](#f-spellid_1) | smallint(5) unsigned |  | NO | 0 |  |
| [`spelltrigger_1`](#f-spelltrigger_1) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spellcharges_1`](#f-spellcharges_1) | tinyint(4) |  | NO | 0 |  |
| [`spellppmrate_1`](#f-spellppmrate_1) | float |  | NO | 0 |  |
| [`spellcooldown_1`](#f-spellcooldown_1) | int(11) |  | NO | -1 |  |
| [`spellcategory_1`](#f-spellcategory_1) | smallint(5) unsigned |  | NO | 0 |  |
| [`spellcategorycooldown_1`](#f-spellcategorycooldown_1) | int(11) |  | NO | -1 |  |
| [`spellid_2`](#f-spellid_2) | smallint(5) unsigned |  | NO | 0 |  |
| [`spelltrigger_2`](#f-spelltrigger_2) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spellcharges_2`](#f-spellcharges_2) | tinyint(4) |  | NO | 0 |  |
| [`spellppmrate_2`](#f-spellppmrate_2) | float |  | NO | 0 |  |
| [`spellcooldown_2`](#f-spellcooldown_2) | int(11) |  | NO | -1 |  |
| [`spellcategory_2`](#f-spellcategory_2) | smallint(5) unsigned |  | NO | 0 |  |
| [`spellcategorycooldown_2`](#f-spellcategorycooldown_2) | int(11) |  | NO | -1 |  |
| [`spellid_3`](#f-spellid_3) | smallint(5) unsigned |  | NO | 0 |  |
| [`spelltrigger_3`](#f-spelltrigger_3) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spellcharges_3`](#f-spellcharges_3) | tinyint(4) |  | NO | 0 |  |
| [`spellppmrate_3`](#f-spellppmrate_3) | float |  | NO | 0 |  |
| [`spellcooldown_3`](#f-spellcooldown_3) | int(11) |  | NO | -1 |  |
| [`spellcategory_3`](#f-spellcategory_3) | smallint(5) unsigned |  | NO | 0 |  |
| [`spellcategorycooldown_3`](#f-spellcategorycooldown_3) | int(11) |  | NO | -1 |  |
| [`spellid_4`](#f-spellid_4) | smallint(5) unsigned |  | NO | 0 |  |
| [`spelltrigger_4`](#f-spelltrigger_4) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spellcharges_4`](#f-spellcharges_4) | tinyint(4) |  | NO | 0 |  |
| [`spellppmrate_4`](#f-spellppmrate_4) | float |  | NO | 0 |  |
| [`spellcooldown_4`](#f-spellcooldown_4) | int(11) |  | NO | -1 |  |
| [`spellcategory_4`](#f-spellcategory_4) | smallint(5) unsigned |  | NO | 0 |  |
| [`spellcategorycooldown_4`](#f-spellcategorycooldown_4) | int(11) |  | NO | -1 |  |
| [`spellid_5`](#f-spellid_5) | smallint(5) unsigned |  | NO | 0 |  |
| [`spelltrigger_5`](#f-spelltrigger_5) | tinyint(3) unsigned |  | NO | 0 |  |
| [`spellcharges_5`](#f-spellcharges_5) | tinyint(4) |  | NO | 0 |  |
| [`spellppmrate_5`](#f-spellppmrate_5) | float |  | NO | 0 |  |
| [`spellcooldown_5`](#f-spellcooldown_5) | int(11) |  | NO | -1 |  |
| [`spellcategory_5`](#f-spellcategory_5) | smallint(5) unsigned |  | NO | 0 |  |
| [`spellcategorycooldown_5`](#f-spellcategorycooldown_5) | int(11) |  | NO | -1 |  |
| [`bonding`](#f-bonding) | tinyint(3) unsigned |  | NO | 0 |  |
| [`page_text`](#f-page_text) | mediumint(8) unsigned |  | NO | 0 |  |
| [`page_language`](#f-page_language) | tinyint(3) unsigned |  | NO | 0 |  |
| [`page_material`](#f-page_material) | tinyint(3) unsigned |  | NO | 0 |  |
| [`start_quest`](#f-start_quest) | mediumint(8) unsigned |  | NO | 0 |  |
| [`lock_id`](#f-lock_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`material`](#f-material) | tinyint(4) |  | NO | 0 |  |
| [`sheath`](#f-sheath) | tinyint(3) unsigned |  | NO | 0 |  |
| [`random_property`](#f-random_property) | mediumint(8) unsigned |  | NO | 0 |  |
| [`set_id`](#f-set_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`max_durability`](#f-max_durability) | smallint(5) unsigned |  | NO | 0 |  |
| [`area_bound`](#f-area_bound) | mediumint(8) unsigned |  | NO | 0 |  |
| [`map_bound`](#f-map_bound) | smallint(6) |  | NO | 0 |  |
| [`duration`](#f-duration) | int(11) unsigned |  | NO | 0 |  |
| [`bag_family`](#f-bag_family) | mediumint(9) |  | NO | 0 |  |
| [`disenchant_id`](#f-disenchant_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`food_type`](#f-food_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`min_money_loot`](#f-min_money_loot) | int(10) unsigned |  | NO | 0 |  |
| [`max_money_loot`](#f-max_money_loot) | int(10) unsigned |  | NO | 0 |  |
| [`wrapped_gift`](#f-wrapped_gift) | mediumint(8) unsigned |  | NO | 0 |  |
| [`extra_flags`](#f-extra_flags) | tinyint(1) unsigned |  | NO | 0 |  |
| [`other_team_entry`](#f-other_team_entry) | int(11) unsigned |  | YES | 1 |  |

---

## Field Breakdown

### Identity & Display

- <a id="f-entry"></a>**`entry`** - Unique item template ID.
- <a id="f-patch"></a>**`patch`** - Content patch ([progression](../Progression-System.md)) this version applies to.
- <a id="f-class"></a>**`class`** - Item class; see the [Item Class table](#item-class) below.
- <a id="f-subclass"></a>**`subclass`** - Sub-class within the class; meaning depends on `class`
  (weapon types for class 2, armor types for class 4, ...).
- <a id="f-name"></a>**`name`** - Item name.
- <a id="f-description"></a>**`description`** - Flavor text shown in gold on the tooltip.
- <a id="f-display_id"></a>**`display_id`** - Model/icon display row.
- <a id="f-quality"></a>**`quality`** - Colour tier: `0` Poor (grey), `1` Common (white), `2` Uncommon (green),
  `3` Rare (blue), `4` Epic (purple), `5` Legendary (orange), `6` Artifact.

### Item Class {#item-class}

`class` (with `subclass`) drives behaviour and stats. From `enum ItemClass`
(`src/game/Objects/ItemPrototype.h`):

| Value | Class | Notes |
| :---: | :--- | :--- |
| 0 | CONSUMABLE | food, potions, scrolls |
| 1 | CONTAINER | bags (`ContainerSlots`) |
| 2 | WEAPON | subclass selects type; damage block applies |
| 3 | GEM | defined in the enum but unused in vanilla content |
| 4 | ARMOR | cloth...shield; armor/stat block applies |
| 5 | REAGENT | spell components |
| 6 | PROJECTILE | ammo (bows/guns) |
| 7 | TRADE_GOODS | crafting materials |
| 8 | GENERIC | misc non-trade goods |
| 9 | RECIPE | recipes/books teaching crafts |
| 10 | MONEY | coin objects |
| 11 | QUIVER | ammo pouches; ranged haste |
| 12 | QUEST | quest items; add flag `0x8000` NO_DISENCHANT so they cannot be disenchanted |
| 13 | KEY | permanent keys |
| 14 | PERMANENT | durable non-equippables |
| 15 | JUNK | vendor trash |

### Economy & Stacking

- <a id="f-flags"></a>**`flags`** - Item flag bitmask; see the [table](#flags-itemprototypeflags) below.
- <a id="f-buy_count"></a>**`buy_count`** - How many items one vendor purchase delivers.
- <a id="f-buy_price"></a>**`buy_price`** - Vendor price in copper (total for `buy_count`).
- <a id="f-sell_price"></a>**`sell_price`** - Vendor refund per item in copper.
- <a id="f-max_count"></a>**`max_count`** - Maximum count a player may carry/own ("Unique"); `0` = unlimited.
- <a id="f-stackable"></a>**`stackable`** - Maximum stack size.

### Flags (`ItemPrototypeFlags`) {#flags-itemprototypeflags}

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x00000001 | NO_PICKUP | not used by the core |
| 0x00000002 | CONJURED | conjured item (vanishes on logout unless stored) |
| 0x00000004 | LOOTABLE | right-click to open for loot (non-container) |
| 0x00000008 | EXOTIC | not used in pre-3.x content |
| 0x00000010 | DEPRECATED | renders with a red icon when durability is 0 |
| 0x00000020 | INDESTRUCTIBLE | cannot be destroyed except as a spell reagent (totems) |
| 0x00000040 | PLAYERCAST | usable by players ("usable" old note) |
| 0x00000080 | NO_EQUIP_COOLDOWN | no cooldown when equipping |
| 0x00000100 | INTBONUSINSTEAD | int bonus displayed instead of another stat |
| 0x00000200 | WRAPPER | gift-wrapped package state |
| 0x00000400 | IGNORE_BAG_SPACE | created without checking bag space |
| 0x00000800 | PARTY_LOOT | item is party loot |
| 0x00001000 | BRIEFSPELLEFFECTS | not used in pre-3.x |
| 0x00002000 | CHARTER | guild charter item |
| 0x00004000 | HAS_TEXT | readable item with text pages |
| 0x00008000 | NO_DISENCHANT | cannot be disenchanted |
| 0x00010000 | REAL_DURATION | duration ticks in real time |
| 0x00020000 | NO_CREATOR | last flag used in 1.12.1 |
| 0x00080000 | UNIQUE_EQUIPPED | server-side unique-equipped check |

Source: `enum ItemPrototypeFlags`, `src/game/Objects/ItemPrototype.h`.

### Slot & Requirements

- <a id="f-inventory_type"></a>**`inventory_type`** - Where it equips (non-equippable, head, neck, chest... two-handed
  weapons use their weapon subclass logic).
- <a id="f-allowable_class"></a>**`allowable_class`** - Class bitmask; `-1` = any class.
- <a id="f-allowable_race"></a>**`allowable_race`** - Race bitmask; `-1` = any race.
- <a id="f-item_level"></a>**`item_level`** - Item level (drives stat budget / disenchant results).
- <a id="f-required_level"></a>**`required_level`** - Minimum character level to equip/use.
- <a id="f-required_skill"></a>**`required_skill`** - Skill line required (e.g. enchanting for rods).
- <a id="f-required_skill_rank"></a>**`required_skill_rank`** - Value of that skill line required.
- <a id="f-required_spell"></a>**`required_spell`** - Spell that must be known (e.g. riding, dual wield).
- <a id="f-required_honor_rank"></a>**`required_honor_rank`** - PvP rank requirement.
- <a id="f-required_city_rank"></a>**`required_city_rank`** - City reputation rank requirement (unused in vanilla content).
- <a id="f-required_reputation_rank"></a><a id="f-required_reputation_faction"></a>**`required_reputation_faction`** / **`required_reputation_rank`** - Faction standing gate.

### Container / Bag Fields

- <a id="f-container_slots"></a>**`container_slots`** - Number of slots (bags only).
- <a id="f-bag_family"></a>**`bag_family`** - Bag family bits (herb/soul/enchanting bags restrict contents).

### Stats

Ten paired slots. `stat_type` uses `ItemModType`: `0` Mana · `1` Health · `3` Agility ·
`4` Strength · `5` Intellect · `6` Spirit · `7` Stamina (value `2` is unused).

- <a id="f-stat_type1"></a>**`stat_type1`** - Stat id for slot 1.
- <a id="f-stat_value1"></a>**`stat_value1`** - Amount of that stat.
- <a id="f-stat_type2"></a>**`stat_type2`** - Stat id for slot 2.
- <a id="f-stat_value2"></a>**`stat_value2`** - Amount of that stat.
- <a id="f-stat_type3"></a>**`stat_type3`** - Stat id for slot 3.
- <a id="f-stat_value3"></a>**`stat_value3`** - Amount of that stat.
- <a id="f-stat_type4"></a>**`stat_type4`** - Stat id for slot 4.
- <a id="f-stat_value4"></a>**`stat_value4`** - Amount of that stat.
- <a id="f-stat_type5"></a>**`stat_type5`** - Stat id for slot 5.
- <a id="f-stat_value5"></a>**`stat_value5`** - Amount of that stat.
- <a id="f-stat_type6"></a>**`stat_type6`** - Stat id for slot 6.
- <a id="f-stat_value6"></a>**`stat_value6`** - Amount of that stat.
- <a id="f-stat_type7"></a>**`stat_type7`** - Stat id for slot 7.
- <a id="f-stat_value7"></a>**`stat_value7`** - Amount of that stat.
- <a id="f-stat_type8"></a>**`stat_type8`** - Stat id for slot 8.
- <a id="f-stat_value8"></a>**`stat_value8`** - Amount of that stat.
- <a id="f-stat_type9"></a>**`stat_type9`** - Stat id for slot 9.
- <a id="f-stat_value9"></a>**`stat_value9`** - Amount of that stat.
- <a id="f-stat_type10"></a>**`stat_type10`** - Stat id for slot 10.
- <a id="f-stat_value10"></a>**`stat_value10`** - Amount of that stat.

### Weapon Damage & Ranged

- <a id="f-delay"></a>**`delay`** - Attack speed in milliseconds (1000 = 1.0).
- <a id="f-range_mod"></a>**`range_mod`** - Ranged range modifier.
- <a id="f-ammo_type"></a>**`ammo_type`** - Ammo category for projectiles.
- <a id="f-dmg_max1"></a><a id="f-dmg_type1"></a><a id="f-dmg_min1"></a>**`dmg_min1`**, **`dmg_max1`**, **`dmg_type1`** - Damage range 1: minimum, maximum and school (`SPELL_SCHOOL_*`).
- <a id="f-dmg_max2"></a><a id="f-dmg_type2"></a><a id="f-dmg_min2"></a>**`dmg_min2`**, **`dmg_max2`**, **`dmg_type2`** - Damage range 2: minimum, maximum and school (`SPELL_SCHOOL_*`).
- <a id="f-dmg_max3"></a><a id="f-dmg_type3"></a><a id="f-dmg_min3"></a>**`dmg_min3`**, **`dmg_max3`**, **`dmg_type3`** - Damage range 3: minimum, maximum and school (`SPELL_SCHOOL_*`).
- <a id="f-dmg_max4"></a><a id="f-dmg_type4"></a><a id="f-dmg_min4"></a>**`dmg_min4`**, **`dmg_max4`**, **`dmg_type4`** - Damage range 4: minimum, maximum and school (`SPELL_SCHOOL_*`).
- <a id="f-dmg_max5"></a><a id="f-dmg_type5"></a><a id="f-dmg_min5"></a>**`dmg_min5`**, **`dmg_max5`**, **`dmg_type5`** - Damage range 5: minimum, maximum and school (`SPELL_SCHOOL_*`).
- <a id="f-block"></a>**`block`** - Block value for shields.

### Armor & Resistances

- <a id="f-armor"></a>**`armor`** - Base armor value.
- <a id="f-fire_res"></a><a id="f-frost_res"></a><a id="f-nature_res"></a><a id="f-holy_res"></a><a id="f-shadow_res"></a><a id="f-arcane_res"></a>**`holy_res`**, **`fire_res`**, **`nature_res`**, **`frost_res`**, **`shadow_res`**,
  **`arcane_res`** - Resistance bonuses.

### Item Spells (slots 1-5)

- <a id="f-spellid_1"></a>**`spellid_1`** - Spell cast/granted by slot 1 (`0` = empty slot).
- <a id="f-spelltrigger_1"></a>**`spelltrigger_1`** - `0` on-use, `1` on-equip aura, `2` chance-on-hit.
- <a id="f-spellcharges_1"></a>**`spellcharges_1`** - Charges; `-1` consumes the item when the last charge is used.
- <a id="f-spellppmrate_1"></a>**`spellppmrate_1`** - Procs-per-minute rate for chance-on-hit triggers.
- <a id="f-spellcooldown_1"></a>**`spellcooldown_1`** - Per-item cooldown in ms (`-1` = use the spell's own cooldown).
- <a id="f-spellcategory_1"></a><a id="f-spellcategorycooldown_1"></a>**`spellcategory_1` / `spellcategorycooldown_1`** - Shared-category cooldown handling.
- <a id="f-spellid_2"></a>**`spellid_2`** - Spell cast/granted by slot 2 (`0` = empty slot).
- <a id="f-spelltrigger_2"></a>**`spelltrigger_2`** - `0` on-use, `1` on-equip aura, `2` chance-on-hit.
- <a id="f-spellcharges_2"></a>**`spellcharges_2`** - Charges; `-1` consumes the item when the last charge is used.
- <a id="f-spellppmrate_2"></a>**`spellppmrate_2`** - Procs-per-minute rate for chance-on-hit triggers.
- <a id="f-spellcooldown_2"></a>**`spellcooldown_2`** - Per-item cooldown in ms (`-1` = use the spell's own cooldown).
- <a id="f-spellcategory_2"></a><a id="f-spellcategorycooldown_2"></a>**`spellcategory_2` / `spellcategorycooldown_2`** - Shared-category cooldown handling.
- <a id="f-spellid_3"></a>**`spellid_3`** - Spell cast/granted by slot 3 (`0` = empty slot).
- <a id="f-spelltrigger_3"></a>**`spelltrigger_3`** - `0` on-use, `1` on-equip aura, `2` chance-on-hit.
- <a id="f-spellcharges_3"></a>**`spellcharges_3`** - Charges; `-1` consumes the item when the last charge is used.
- <a id="f-spellppmrate_3"></a>**`spellppmrate_3`** - Procs-per-minute rate for chance-on-hit triggers.
- <a id="f-spellcooldown_3"></a>**`spellcooldown_3`** - Per-item cooldown in ms (`-1` = use the spell's own cooldown).
- <a id="f-spellcategory_3"></a><a id="f-spellcategorycooldown_3"></a>**`spellcategory_3` / `spellcategorycooldown_3`** - Shared-category cooldown handling.
- <a id="f-spellid_4"></a>**`spellid_4`** - Spell cast/granted by slot 4 (`0` = empty slot).
- <a id="f-spelltrigger_4"></a>**`spelltrigger_4`** - `0` on-use, `1` on-equip aura, `2` chance-on-hit.
- <a id="f-spellcharges_4"></a>**`spellcharges_4`** - Charges; `-1` consumes the item when the last charge is used.
- <a id="f-spellppmrate_4"></a>**`spellppmrate_4`** - Procs-per-minute rate for chance-on-hit triggers.
- <a id="f-spellcooldown_4"></a>**`spellcooldown_4`** - Per-item cooldown in ms (`-1` = use the spell's own cooldown).
- <a id="f-spellcategory_4"></a><a id="f-spellcategorycooldown_4"></a>**`spellcategory_4` / `spellcategorycooldown_4`** - Shared-category cooldown handling.
- <a id="f-spellid_5"></a>**`spellid_5`** - Spell cast/granted by slot 5 (`0` = empty slot).
- <a id="f-spelltrigger_5"></a>**`spelltrigger_5`** - `0` on-use, `1` on-equip aura, `2` chance-on-hit.
- <a id="f-spellcharges_5"></a>**`spellcharges_5`** - Charges; `-1` consumes the item when the last charge is used.
- <a id="f-spellppmrate_5"></a>**`spellppmrate_5`** - Procs-per-minute rate for chance-on-hit triggers.
- <a id="f-spellcooldown_5"></a>**`spellcooldown_5`** - Per-item cooldown in ms (`-1` = use the spell's own cooldown).
- <a id="f-spellcategory_5"></a><a id="f-spellcategorycooldown_5"></a>**`spellcategory_5` / `spellcategorycooldown_5`** - Shared-category cooldown handling.

### Pages, Locks & Binding

- <a id="f-bonding"></a>**`bonding`** - `0` none, `1` binds when picked up, `2` binds when equipped,
  `3` binds when used, `4/5` quest-item variants.
- <a id="f-page_text"></a>**`page_text`** - First [`page_text`](page_text.md).entry for readable books.
- <a id="f-page_language"></a>**`page_language`** - Language the text is written in.
- <a id="f-page_material"></a>**`page_material`** - Visual material of book pages.
- <a id="f-start_quest"></a>**`start_quest`** - Quest offered by using this item.
- <a id="f-lock_id"></a>**`lock_id`** - `Lock.dbc` entry; opening may require lockpicking/keys.
- <a id="f-material"></a>**`material`** - Sound/impact material (DBC passthrough).
- <a id="f-sheath"></a>**`sheath`** - How weapons are carried on the belt/back.

### Enchants, Sets & Durability

- <a id="f-random_property"></a>**`random_property`** - Weighted pool id in
  [`item_enchantment_template`](item_enchantment_template.md) rolled at creation.
- <a id="f-set_id"></a>**`set_id`** - Item set ID from ItemSet.dbc.
- <a id="f-max_durability"></a>**`max_durability`** - Maximum durability points.
- <a id="f-disenchant_id"></a>**`disenchant_id`** - Entry in [`disenchant_loot_template`](disenchant_loot_template.md);
  `0` = not disenchantable.
- <a id="f-duration"></a>**`duration`** - Temporary-item lifetime (seconds); consumed by real-duration flags.

### Bindings to World & Food

- <a id="f-area_bound"></a><a id="f-map_bound"></a>**`area_bound` / `map_bound`** - Restricts where the item functions.
- <a id="f-food_type"></a>**`food_type`** - Food category used by "well fed"-style spells.
- <a id="f-wrapped_gift"></a>**`wrapped_gift`** - Set on gift-wrapped packages.

### Loot Money & Cross-Faction

- <a id="f-max_money_loot"></a><a id="f-min_money_loot"></a>**`min_money_loot` / `max_money_loot`** - Coin range rolled into
  [`item_loot_template`](item_loot_template.md)-style openable items.
- <a id="f-extra_flags"></a>**`extra_flags`** - Server-side behaviour flags (e.g. drop-rate category overrides).
- <a id="f-other_team_entry"></a>**`other_team_entry`** - Counterpart entry id on the opposing faction
  (faction-specific quest items pair up through this column).
