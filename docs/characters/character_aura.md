# character_aura Table

Non-passive auras persisting on a character across logout, including self-cast stances/shapeshift forms.
Passive spells are skipped by the save and re-applied from learned spells instead.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`caster_guid`](#f-caster_guid) | bigint(20) unsigned | PRI | NO | 0 |  |
| [`item_guid`](#f-item_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | int(11) unsigned | PRI | NO | 0 |  |
| [`stacks`](#f-stacks) | int(11) unsigned |  | NO | 1 |  |
| [`charges`](#f-charges) | int(11) unsigned |  | NO | 0 |  |
| [`base_points0`](#f-base_points0) | float |  | NO | 0 |  |
| [`base_points1`](#f-base_points1) | float |  | NO | 0 |  |
| [`base_points2`](#f-base_points2) | float |  | NO | 0 |  |
| [`periodic_time0`](#f-periodic_time0) | int(11) unsigned |  | NO | 0 |  |
| [`periodic_time1`](#f-periodic_time1) | int(11) unsigned |  | NO | 0 |  |
| [`periodic_time2`](#f-periodic_time2) | int(11) unsigned |  | NO | 0 |  |
| [`max_duration`](#f-max_duration) | int(11) |  | NO | 0 |  |
| [`duration`](#f-duration) | int(11) |  | NO | 0 |  |
| [`effect_index_mask`](#f-effect_index_mask) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid carrying the aura ([`characters`](characters.md).guid).
- <a id="f-caster_guid"></a>**`caster_guid`** - Primary Key. Unit guid of the aura caster (the player's own guid for
  self-cast auras; `0` only if applied without a caster object).
- <a id="f-item_guid"></a>**`item_guid`** - Primary Key. Item that granted the aura (proc/enchant), else 0.
- <a id="f-spell"></a>**`spell`** - Primary Key. Spell id producing this aura.
- <a id="f-stacks"></a>**`stacks`** - Current stack count (refreshable auras).
- <a id="f-charges"></a>**`charges`** - Remaining proc/consumable charges.
- <a id="f-base_points0"></a>**`base_points0`** - Rolled base points (damage/heal magnitude) per effect, overriding DBC dice.
- <a id="f-base_points1"></a>**`base_points1`** - Rolled base points (damage/heal magnitude) per effect, overriding DBC dice.
- <a id="f-base_points2"></a>**`base_points2`** - Rolled base points (damage/heal magnitude) per effect, overriding DBC dice.
- <a id="f-periodic_time0"></a>**`periodic_time0`** - Tick interval in ms for periodic effects 1-3.
- <a id="f-periodic_time1"></a>**`periodic_time1`** - Tick interval in ms for periodic effects 1-3.
- <a id="f-periodic_time2"></a>**`periodic_time2`** - Tick interval in ms for periodic effects 1-3.
- <a id="f-max_duration"></a>**`max_duration`** - Total duration in ms when applied.
- <a id="f-duration"></a>**`duration`** - Remaining duration in ms at save time.
- <a id="f-effect_index_mask"></a>**`effect_index_mask`** - Bitmask of active effect indexes (bit0 = effect1 …).
