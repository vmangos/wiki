# Zone Mechanics

Small world systems that operate per zone: weather, graveyards, exploration XP and fishing
zones.

---

## Weather

[`game_weather`](world/game_weather.md) defines per-zone weather chances for each season
(spring/summer/fall/winter × rain/snow/storm). The active season is derived from the server date in `Weather.cpp`:
`season = ((yday − 78 + 365) / 91) % 4`, so spring begins around 20 March. The server rolls
periodically (`ChangeWeatherInterval` in `mangosd.conf`) and broadcasts the
result to players in the zone; rolls under a 60 % threshold with grade below ⅓ resolve to
*fair* weather, keeping most zones clear most of the time. GMs can force weather with the
`.wchange <type> <grade>` command.

---

## Graveyards

[`game_graveyard_zone`](world/game_graveyard_zone.md) links nearest-graveyard ids to zones (with
faction and [patch](Progression-System.md) filters). When a player dies, the core picks the
closest valid graveyard for the zone they died in; ghosts run back from there.
[`areatrigger_tavern`](world/areatrigger_tavern.md) marks tavern areas where logging out counts as "resting".

---

## Exploration

- [`exploration_basexp`](world/exploration_basexp.md) - base XP granted for discovering a zone
  at a given level.
- Discovery state is stored per player as an exploration bitmask on
  [`characters`](characters/characters.md).

---

## Fishing Zones

[`skill_fishing_base_level`](world/skill_fishing_base_level.md) sets the minimum fishing skill
per zone/area. Fishing loot itself comes from
[`fishing_loot_template`](world/fishing_loot_template.md) keyed by area id (entry `0` = junk on
failure) - see the [Loot System](Loot-System.md).

---

## Related Pages

- [game_weather](world/game_weather.md)
- [game_graveyard_zone](world/game_graveyard_zone.md)
