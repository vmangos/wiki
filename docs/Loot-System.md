# Loot System

How loot works in VMaNGOS: which table feeds which loot store, how rows are grouped and rolled,
and where conditions and progression filtering apply. The loading/rolling code lives in
`src/game/LootMgr.cpp`.

---

## Loot Stores and Their ID Sources

Every `*_loot_template` is a *store*. Rows with the same `entry` form one loot table; the `entry`
is referenced from another table (the *loot id*):

| Store | Referenced by | Notes |
| :--- | :--- | :--- |
| [`creature_loot_template`](world/creature_loot_template.md) | [`creature_template`](world/creature_template.md).loot_id | Loot id `0` is never rolled; Alterac Valley player-kill loot uses `battleground_template`.player_loot_id into [`reference_loot_template`](world/reference_loot_template.md). |
| [`pickpocketing_loot_template`](world/pickpocketing_loot_template.md) | [`creature_template`](world/creature_template.md).pickpocket_loot_id | Empty loot id = nothing to pick. |
| [`skinning_loot_template`](world/skinning_loot_template.md) | [`creature_template`](world/creature_template.md).skinning_loot_id | Also used for herb/mining nodes that are skinnable. |
| [`disenchant_loot_template`](world/disenchant_loot_template.md) | [`item_template`](world/item_template.md).DisenchantID | |
| [`gameobject_loot_template`](world/gameobject_loot_template.md) | [`gameobject_template`](world/gameobject_template.md) loot id (`data1` for chest-type objects) | |
| [`item_loot_template`](world/item_loot_template.md) | [`item_template`](world/item_template.md).entry | Loot contained in items (e.g. clams). |
| [`fishing_loot_template`](world/fishing_loot_template.md) | Area id ([`skill_fishing_base_level`](world/skill_fishing_base_level.md) zones) | Entry `0` = junk loot on failed catch. |
| [`mail_loot_template`](world/mail_loot_template.md) | Mail reward systems | |
| [`reference_loot_template`](world/reference_loot_template.md) | other stores via `mincountOrRef < 0` | Shared sub-tables, see below. |

The loader validates references at startup: unused or missing loot ids produce DB errors in the
server log (`ReportUnusedIds` / `ReportNotExistedId`).

---

## How a Row Rolls

Shared columns of all loot templates:

- **`ChanceOrQuestChance`**
  - Positive value = plain percentage chance to drop.
  - Negative value = quest item; the absolute value is the chance, and the item only drops for
    characters on the matching quest.
  - `100` = always.
- **`groupid`** - rows sharing a non-zero group id form an *equally distributed* group: the
  server picks one (or more) members per kill so the total chance of the group stays constant.
  Set-chance groups use per-row chances instead when configured.
- **`mincountOrRef`**
  - Positive: minimum stack size for this drop.
  - **Negative:** `-reference_entry` - pull items from
    [`reference_loot_template`](world/reference_loot_template.md) instead of dropping an item directly.
- **`maxcount`** - maximum stack size (or number of pulls from a reference).
- **`condition_id`** - optional [conditions](world/conditions.md) check; the row is skipped when the
  condition fails.
- **`patch_min` / `patch_max`** - [progression](Progression-System.md) filtering.

Drop rates can be tuned globally with the `Rate.Drop.Item.*` settings in
`mangosd.conf`.

---

## Reference Templates

[`reference_loot_template`](world/reference_loot_template.md) lets many tables share one pool (e.g. "world drop epics"). A row in any
store with negative `mincountOrRef` expands into that reference table at roll time; each row of
the reference rolls independently using its own `ChanceOrQuestChance`. Nested references are
supported but keep them shallow for performance.

---

## Creature Money

Gold drops do **not** come from loot templates: [`creature_template`](world/creature_template.md).gold_min / `gold_max`
define the money range, scaled by `Rate.Drop.Money`.

---

## Related Pages

- [creature_template](world/creature_template.md) - `loot_id`, `pickpocket_loot_id`,
  `skinning_loot_id`, `gold_min`, `gold_max`
- [conditions](world/conditions.md)
- [Progression System](Progression-System.md) - patch filtering
