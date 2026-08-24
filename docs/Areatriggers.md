# Areatriggers

Areatriggers are client-defined trigger volumes (from `AreaTrigger.dbc`) the server reacts to
when a player enters or exits. The world DB adds behaviour per trigger id through a family of
tables.

---

## The Family

| Table | Behaviour on enter |
| :--- | :--- |
| [`areatrigger_template`](world/areatrigger_template.md) | Base metadata/flags for the trigger. |
| [`areatrigger_teleport`](world/areatrigger_teleport.md) | Teleports the player to target coordinates/map (dungeon entrances, portals). Honors required quest/level via fields; also patch-filtered (`patch` column). |
| [`areatrigger_tavern`](world/areatrigger_tavern.md) | Marks tavern zones: inside, players get the *resting* bonus and instant logout. |
| [`areatrigger_bg_entrance`](world/areatrigger_bg_entrance.md) | Registers an entrance portal to a battleground queue (links to [`battleground_template`](world/battleground_template.md)). |
| [`areatrigger_involvedrelation`](world/areatrigger_involvedrelation.md) | Completes "explore the area" quest objectives (quest explore triggers). |
| [`areatrigger_scripts`](world/areatrigger_scripts.md) | Runs [generic DB scripts](DB-Script-Tables.md) for fully custom behaviour. |

---

## How It Works

1. The client detects entry into an `AreaTrigger.dbc` volume and notifies the server.
2. The server looks up the trigger id in each table above; all matching behaviours apply
   (a trigger can teleport **and** run a script).
3. Teleports respect level/quest requirements configured on the row and can be blocked by
   conditions where supported.

---

## Examples

- **Custom portal**: add a row to [`areatrigger_teleport`](world/areatrigger_teleport.md) with destination coordinates, or use
  [`areatrigger_scripts`](world/areatrigger_scripts.md) + command 6 `TELEPORT_TO` when you need conditions
  ([conditions](world/conditions.md)).
- **Dungeon entrance with ghost entrance**: set `ghost_entrance_map/x/y/z` so dead players
  enter at the graveyard side.
- **Explore quests**: reference the areatrigger id from
  `quest_template.ReqCreatureOrGOId*`-style exploration objectives and link it in
  [`areatrigger_involvedrelation`](world/areatrigger_involvedrelation.md).

---

## Related Pages

- [Instances & Resets](Instances.md) - dungeon entrances
- [Game Events](Game-Events.md) - event-gated content nearby
