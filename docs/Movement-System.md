# Creature Movement System

This page explains how creatures move: the `movement_type` column, wander behaviour, waypoint
paths, and formations. Movement generators live in `src/game/Movement/`; the default generator for
a creature is chosen in `FactorySelector::selectMovementGenerator`
(`src/game/AI/CreatureAISelector.cpp`).

---

## Default Movement Type

The `movement_type` column of [`creature`](world/creature.md) (and
[`creature_template`](world/creature_template.md)) selects the *default* movement generator:

| Value | Generator | Behaviour |
| :---: | :--- | :--- |
| 0 | `IdleMovementGenerator` | Creature stays at its spawn point. |
| 1 | `RandomMovementGenerator` | Random wandering within `wander_distance` yards of the spawn point. |
| 2 | `WaypointMovementGenerator` | Follows a waypoint path (see [Waypoint Movement](#waypoint-movement)). |

Notes:

- A player-owned unit defaults to `FOLLOW_MOTION_TYPE` instead.
- If the creature belongs to a [creature group](world/creature_groups.md) formation but is **not** the
  leader, it is forced into `PATROL_MOTION_TYPE` so it follows the leader.
- Combat, flee, fear, confusion and home-movement are handled by additional generators that
  temporarily override the default (`MotionMaster`, `src/game/Movement/MotionMaster.h`).

### `wander_distance`

Maximum radius (yards) around the spawn point used by `RandomMovementGenerator`. Only meaningful
when `movement_type = 1`.

---

## Waypoint Movement

With `movement_type = 2` the creature walks a waypoint path stored either in
[`creature_movement`](world/creature_movement.md) (path bound to a specific spawn `guid`) or in
[`creature_movement_template`](world/creature_movement_template.md) (path shared by all spawns of an
entry). The guid-specific path takes precedence.

Each waypoint defines position, wait time, movement flags and - via
[`creature_movement_scripts`](world/creature_movement_scripts.md) - actions to run when the point is
reached (say text, cast spells, start scripts…).

Waypoints can also be started/stopped from DB scripts with the `START_WAYPOINTS` command (60),
see [DB Script Tables](DB-Script-Tables.md).

---

## Formation / Group Movement

[`creature_groups`](world/creature_groups.md) lets several spawns move as one pack:

- The `leader_guid` follows its own path; members keep their `dist`/`angle` offsets.
- Members use patrol movement automatically (see selection notes above).
- Group behaviours on attack/death/respawn (assist together, evade/respawn together…) are
  controlled by `flags` bits, documented in the table page; per-spawn limits live in
  [`creature_groups_entry_limit`](world/creature_groups_entry_limit.md).

---

## Runtime Overrides from Scripts

DB scripts can change movement at runtime using these commands (full parameter tables in
[DB Script Tables](DB-Script-Tables.md)):

| Command | Effect |
| :---: | --- |
| 3 `MOVE_TO` | Walk to coordinates or target |
| 20 `MOVEMENT` | Switch/pause/resume the current generator |
| 60 `START_WAYPOINTS` | Start a waypoint path |
| 67 `SET_DEFAULT_MOVEMENT` | Change idle/wander/waypoint default and wander distance |
| 77 `SET_FLY` | Toggle flying movement |

---

## Related Pages

- [creature](world/creature.md) - `movement_type`, `wander_distance` columns
- [creature_movement](world/creature_movement.md) / [creature_movement_template](world/creature_movement_template.md)
- [creature_groups](world/creature_groups.md)
