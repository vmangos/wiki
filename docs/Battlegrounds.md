# Battlegrounds

VMaNGOS supports the three classic battlegrounds with full C++ implementations in
`src/game/Battlegrounds/`:

| Queue id | Battleground | Implementation |
| :---: | :--- | :--- |
| 1 | Alterac Valley (AV) | `BattleGroundAV.cpp` |
| 2 | Warsong Gulch (WS) | `BattleGroundWS.cpp` |
| 3 | Arathi Basin (AB) | `BattleGroundAB.cpp` |

---

## Data Tables

| Table | Purpose |
| :--- | :--- |
| [`battleground_template`](world/battleground_template.md) | Per-map definition: level brackets, player limits, start locations, world safe locs. |
| [`battlemaster_entry`](world/battlemaster_entry.md) | Which NPCs queue players into which battleground (`npc_flags` battlemaster). |
| [`creature_battleground`](world/creature_battleground.md) | Creatures that only spawn inside a battleground (guards, quest givers). |
| [`gameobject_battleground`](world/gameobject_battleground.md) | Objects spawned only inside a battleground (flags, bases, buff objects). |
| [`battleground_events`](world/battleground_events.md) | Timed object/creature state changes during a match (gate openings, capture effects). |

Battleground-specific spawns reference these tables instead of the normal
[`creature`](world/creature.md)/[`gameobject`](world/gameobject.md) spawn tables.

---

## Runtime Concepts

- **Queue ids** - `BATTLEGROUND_QUEUE_AV/WS/AB` (`BattleGroundDefines.h`).
- **Brackets** - up to 6 level ranges per battleground; bracket layout comes from the template.
- **Status flow** - wait → invitation → prestart countdown → running → finished
  (`enum BattleGroundStatus`). Timers such as `BattleGround.PrematureFinishTimer`
  are config options (`mangosd.conf`).
- **Rewards** - marks of honour and bonus honour are handled by the core;
  weekend/holiday bonuses come through the [game event](Game-Events.md) system.

---

## Configuration Highlights

From `mangosd.conf`:

- `Battleground.CastDeserter` - deserter debuff for leavers.
- `Battleground.QueueAnnouncer.Join/Start` - queue announcements.
- `Battleground.InvitationType` - balanced vs. first-come team filling.
- `BattleGround.PremadeGroupWaitForMatch` - premade matching in WSG/AB.

---

## Related Pages

- [battleground_template](world/battleground_template.md)
- [Honor & PvP](Honor-PvP.md)
