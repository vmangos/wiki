# Instances & Resets

How dungeon and raid instances are created, saved and reset
(`src/game/Maps/MapPersistentStateMgr.cpp`).

---

## Map Types

[`map_template`](world/map_template.md) classifies every map via `map_type`:

| Type | Meaning | Reset behaviour |
| :---: | :--- | :--- |
| 0 | Common/Continent (Eastern Kingdoms, Kalimdor) | never resets |
| 1 | Dungeon (5-man) | saves on boss kill; reset by schedule |
| 2 | Raid (40/20-man) | same as dungeon with longer `reset_delay` |
| 3 | Battleground | handled by the [Battlegrounds](Battlegrounds.md) system |

(`enum MapTypes`, `src/game/Database/DBCEnums.h`; vanilla has no arena map type.)

`reset_delay` on the map defines the days between resets; the actual schedule lives per map in [`instance_reset`](characters/instance_reset.md).

---

## Instance Saves & Binds

- When a group kills a save-triggering encounter, an entry is created in
  [`instance`](characters/instance.md) and binds are recorded for:
  - each player → [`character_instance`](characters/character_instance.md)
  - the group → [`group_instance`](characters/group_instance.md)
- Bound players re-enter the *same* instance id until it resets.
- Per-instance creature/object respawn state persists in
  [`creature_respawn`](characters/creature_respawn.md) /
  [`gameobject_respawn`](characters/gameobject_respawn.md), keyed by instance.

---

## Scripted Instances

- [`map_template`](world/map_template.md).script_name binds a C++ instance script
  (under `src/scripts/eastern_kingdoms/`, `src/scripts/kalimdor/`, … by continent/zone).
- Scripts store their own state via commands 37 `SET_INST_DATA` / 38 `SET_INST_DATA64`
  ([DB Script Tables](DB-Script-Tables.md)) and can read it back in conditions
  (`CONDITION_INSTANCE_DATA`, 34).
- Encounter statistics (kills, wipes, custom counters) stream into the logs database:
  [`instance_creature_kills`](logs/instance_creature_kills.md),
  [`instance_wipes`](logs/instance_wipes.md),
  [`instance_custom_counters`](logs/instance_custom_counters.md).

---

## Related Pages

- [map_template](world/map_template.md)
- [instance_reset](characters/instance_reset.md)
