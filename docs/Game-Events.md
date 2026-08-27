# Game Events

The game event system (`GameEventMgr`, `src/game/GameEventMgr.cpp`) activates and deactivates
world content on a schedule: seasonal world events (Noblegarden, Harvest Festival…), the AQ war
effort, Darkmoon Faire and custom server events.

---

## Defining an Event

[`game_event`](world/game_event.md) is the master table:

| Field | Meaning |
| :--- | :--- |
| `entry` | Event id referenced by all `game_event_*` tables. |
| `start_time` / `end_time` | The window in which occurrences of the event may start. |
| `occurence` | Minutes between event starts (the cycle length). |
| `length` | Minutes the event stays active each cycle. |
| `holiday` | Link to a `Holiday.dbc` id - makes the client show the holiday calendar/announcement. |
| `description` | Human-readable name. |
| `hardcoded` | Event state driven by C++ (e.g. AQ) instead of the scheduler. |
| `disabled` | Skip entirely. |
| `patch_min` / `patch_max` | [Progression](Progression-System.md) gating. |

An event is *active* when the current time falls inside an occurrence window; scripts and
conditions can test this with `CONDITION_ACTIVE_GAME_EVENT`.

---

## What Events Can Change

| Table | Effect while the event is active |
| :--- | :--- |
| [`game_event_creature`](world/game_event_creature.md) | Add/remove creature spawns (guid-based). |
| [`game_event_creature_data`](world/game_event_creature_data.md) | Override display/faction/equipment of spawns during the event. |
| [`game_event_gameobject`](world/game_event_gameobject.md) | Add/remove gameobject spawns. |
| [`game_event_quest`](world/game_event_quest.md) | Make quests available only during the event. |
| [`game_event_mail`](world/game_event_mail.md) | Send reward mails on event conditions. |

Events can also be toggled manually by admins via the `event` commands (`event list`, `event enable`, `event disable`;
see [GM Commands](GM-Commands.md)); manual state is persisted in
[`game_event_status`](characters/game_event_status.md).

---

## Conditions & Scripts

- Check active state from any condition: `CONDITION_ACTIVE_GAME_EVENT` (12).
- Start/stop events from DB scripts: command 53 `GAME_EVENT`
  ([DB Script Tables](DB-Script-Tables.md)).
- Hardcoded events (AQ gate progression) live in `src/game/HardcodedEvents.cpp` with
  `hardcoded = 1`.

---

## Related Pages

- [game_event](world/game_event.md)
- [Progression System](Progression-System.md)
- [conditions](world/conditions.md)
