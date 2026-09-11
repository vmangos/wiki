# Honor & PvP

How honor, dishonor and PvP flags work in VMaNGOS (`src/game/HonorMgr.cpp`).

---

## The Honor Day

Honor is calculated once per week per realm (on the configured maintenance day):

1. The core stores accumulated honor contribution points (CP) per character in
   [`character_honor_cp`](characters/character_honor_cp.md) during the day.
2. At the weekly maintenance tick the standing calculation runs over all characters, awards ranks/titles
   and writes history.
3. The tick date is persisted in [`saved_variables`](characters/saved_variables.md).

The whole pipeline can be emulated for a specific client timeline using the `PvP.Accurate*`
config toggles (`mangosd.conf`).

---

## Dishonor & Kills

- Killing civilians and other dishonorable targets subtracts CP / gives dishonorable kills.
- `PvP.DishonorableKills` configures the behaviour.
- Honor gains scale with the victim's level/rank and group size; the gain formula itself is
  hardcoded in `MaNGOS::Honor::GetHonorGain` (`Formulas.h`), with no rate config options.

---

## PvP Flags

| Mechanic | Where |
| :--- | :--- |
| Player vs. player flagging | `UnitDefines.h` unit flags; set by attacking, zones, spells |
| Duel handling | core, no DB data |
| [Battlegrounds](Battlegrounds.md) | own flag rules inside instances |

DB scripts can toggle PvP state on players with command 86 `SET_PVP`
([DB Script Tables](DB-Script-Tables.md)).

---

## Rank System Internals

From `HonorMgr.h/.cpp` and `MaNGOS::Honor::GetHonorGain` (`Formulas.h`):

- **19 ranks total**: 4 negative (dishonor) + 15 positive; the client rank bar visualises
  `-4 … +14`.
- Rank points thresholds: first positive rank at `2000 RP`, then one rank per additional
  `5000 RP`; dishonor ranks mirror this downward.
- Minimum honor kills for ranking: **25** pre-1.10, **15** post-1.10
  (`MIN_HONOR_KILLS_PRE/POST_1_10`).
- **HK diminishing returns**: repeated kills of the same victim lose value: 25 % per repeat
  pre-1.12, **10 %** post-1.12 (progression-aware via `ACCURATE_PVP_REWARDS`).
- Honor per kill:
  ```
  gain = levelCoeff(killerLevel) × sameVictimPenalty
         × expFactor × e^(0.05331 × victimVisualRank)
         × levelDiffPenalty / groupSize
  ```
  with `expFactor = 157.4` pre-1.8 and `188.3` after.
- **Dishonorable kills** vs civilians grant penalty CP by victim level (10 → capped 100).
- Weekly tick redistributes standings (`DistributeRankPoints`), decays inactive players
  (`InactiveDecayRankPoints`) and persists rank/RP/standing into the
  [`characters`](characters/characters.md) columns.

## Related Pages

- [character_honor_cp](characters/character_honor_cp.md)
- [Battlegrounds](Battlegrounds.md)
