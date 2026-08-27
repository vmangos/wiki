# Progression (Patch) System

VMaNGOS can emulate any content patch of Vanilla WoW (1.2 - 1.12). The configured patch controls
gameplay mechanics, quest/NPC/dungeon availability, and which database rows are loaded. This page
explains how the system works and how `patch`, `patch_min` and `patch_max` columns behave.

The server reads the active patch from the `WowPatch` setting in `mangosd.conf`
(`src/game/World.cpp`: `m_wowPatch = sConfig.GetIntDefault("WowPatch", WOW_PATCH_102)`).

---

## Content Patch Values

Defined in `src/shared/Progression.h` (`enum WowPatch`) and `World::GetPatchName()`:

| Value | Client | Patch name |
| :---: | :--- | :--- |
| 0 | 1.2 | Mysteries of Maraudon |
| 1 | 1.3 | Ruins of the Dire Maul |
| 2 | 1.4 | The Call to War |
| 3 | 1.5 | Battlegrounds |
| 4 | 1.6 | Assault on Blackwing Lair |
| 5 | 1.7 | Rise of the Blood God |
| 6 | 1.8 | Dragons of Nightmare |
| 7 | 1.9 | The Gates of Ahn'Qiraj |
| 8 | 1.10 | Storms of Azeroth |
| 9 | 1.11 | Shadow of the Necropolis |
| 10 | 1.12 | Drums of War |

> **Note:** Patch `0` represents the 1.2 state, not original release (1.1). Data before 1.2 is
> generally not represented.

---

## Column Semantics

### `patch` - "this row replaces earlier versions"

Tables with a plain `patch` column keep **multiple versions of the same logical row**. The loader
selects the highest `patch` value that is **≤** the server's configured patch:

```sql
-- Example from ObjectMgr::LoadCreatureTemplates:
SELECT ... FROM creature_template t1
WHERE patch = (SELECT max(patch) FROM creature_template t2
               WHERE t1.entry = t2.entry AND patch <= <server_patch>)
```

Changing an NPC's stats for patch 1.10 therefore means **adding a new row** with the same `entry`
and `patch = 8` (or higher) rather than editing the existing one.

Used by: [`creature_template`](world/creature_template.md), [`gameobject_template`](world/gameobject_template.md), [`quest_template`](world/quest_template.md), [`creature_addon`](world/creature_addon.md),
[`areatrigger_teleport`](world/areatrigger_teleport.md), [`battleground_template`](world/battleground_template.md), [`forbidden_items`](world/forbidden_items.md), [`map_template`](world/map_template.md),
[`creature_onkill_reputation`](world/creature_onkill_reputation.md), [`game_event_creature_data`](world/game_event_creature_data.md).

### `patch_min` / `patch_max` - "this row exists only within a range"

Rows are loaded only if

```
patch_min <= server_patch <= patch_max
```

Defaults are `0` and `10`, i.e. *always visible*. Typical uses:

- A spawn that only exists after a certain patch → set `patch_min`.
- An item/quest removed in a later patch → cap `patch_max`.
- Progression-gated loot: give a boss its pre-nerf loot table until patch X.

Used by (non-exhaustive): [`creature`](world/creature.md), [`gameobject`](world/gameobject.md), `*_loot_template`, `pool_*`,
[`creature_questrelation`](world/creature_questrelation.md) / [`creature_involvedrelation`](world/creature_involvedrelation.md) (+ gameobject equivalents),
[`creature_equip_template`](world/creature_equip_template.md), [`item_enchantment_template`](world/item_enchantment_template.md), [`game_graveyard_zone`](world/game_graveyard_zone.md),
[`petcreateinfo_spell`](world/petcreateinfo_spell.md), [`game_event`](world/game_event.md), [`areatrigger_tavern`](world/areatrigger_tavern.md), [`creature_charm_spells`](world/creature_charm_spells.md).

---

## Related Configuration

Several `mangosd.conf` settings complement the progression system:

- `WowPatch` - the active content patch (shipped config default `10`; falls back internally to `0`/1.2 if unset).
- `PvP.AccurateTimeline` and related `PvP.*` toggles - honour/PvP behaviour per timeline.
- `Progression*` rate toggles that gate content-specific tuning.

---

## Tips for Database Work

- Check which patch a row belongs to **before** editing: `SELECT patch FROM creature_template WHERE entry = X;`
  may return several rows.
- When adding content intended for all patches, leave `patch_min = 0` and `patch_max = 10`.
- The [ScriptEditor](https://github.com/brotalnia/scripteditor) understands these columns when
  editing templates.
