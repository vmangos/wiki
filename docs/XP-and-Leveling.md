# XP & Leveling Formulas

How experience is calculated, straight from `src/game/Formulas.h` and `QuestDef.cpp`.
All multipliers below are further scaled by the `Rate.XP.*` settings in
`mangosd.conf`.

---

## Kill XP Colour Coding

Relative mob level decides the colour of the target's level (`XP::GetColorCode`):

| Colour | Condition |
| :--- | :--- |
| Red | mob ≥ player + 5 |
| Orange | mob ≥ player + 3 |
| Yellow | mob within −2 … +2 |
| Green | mob > gray level |
| Gray | mob ≤ gray level → **no XP** |

### Gray Level ("no XP" boundary)

```
player ≤ 5   : none (everything gives XP)
player ≤ 39  : player − 5 − player/10
player ≥ 40  : player − 1 − player/5
```

### Zero Difference (`GetZeroDifference`)

Used for green-mob scaling:

| Player level | ZD |
| :---: | :---: |
| <8 | 5 |
| <10 | 6 |
| <12 | 7 |
| <16 | 8 |
| <20 | 9 |
| <30 | 11 |
| <40 | 12 |
| <45 | 13 |
| <50 | 14 |
| <55 | 15 |
| <60 | 16 |

---

## Kill XP Formula

```
base      = (killer_level × 5 + 45) × levelFactor
levelFactor:
  victim ≥ killer : 1 + 0.05 × min(victim−killer, 4)
  victim > gray   : (ZD + victim − killer) / ZD
  victim ≤ gray   : 0        (BaseGainLevelFactor returns 0)
```

Multipliers applied afterwards (`XP::Gain`):

| Modifier | Value |
| :--- | :--- |
| Elite in non-raid dungeon | × 2.5 |
| Elite elsewhere | × 2 |
| Victim is a pet | × 0.75 |
| Creature `xp_multiplier` | per-template |
| Damage-origin modifier | partial credit when pet/totem did damage |
| Config | `Rate.XP.Kill` or `Rate.XP.Kill.Elite` |

Zero-XP cases: summoned critters/totems and `CREATURE_STATIC_FLAG_NO_XP`. Pre-1.7 pets use their
owner's level for scaling ([progression](Progression-System.md)).

### Group Bonus

`xp_in_group_rate` scales group kills (then splits):

| Members | Rate |
| :---: | :--- |
| 1-2 | × 1.0 |
| 3 | × 1.166 |
| 4 | × 1.3 |
| 5 | × 1.4 |
| 6+ | max(1 − 0.05 × count, 0.01) |

---

## Quest XP Degradation

`Quest::XPValue(playerLevel)`. Quest level `q`, character level `p`, base reward `RewXP`:

| Character level | XP granted |
| :--- | :--- |
| p ≤ q + 5 | 100 % |
| p = q + 6 | 80 % |
| p = q + 7 | 60 % |
| p = q + 8 | 40 % |
| p = q + 9 | 20 % |
| p ≥ q + 10 | 10 % |

---

## Rested Bonus

Rest bonus accrues into [`characters.rest_bonus`](characters/characters.md) and is consumed as
bonus XP. Accrual/consumption rates are configurable:

- `Rate.Rest.InGame` - resting while logged in (tavern/city).
- `Rate.Rest.Offline.InTavernOrCity` - offline in a rest area.
- `Rate.Rest.Offline.InWilderness` - offline elsewhere (internally ÷ 4).

Tavern areas come from [`areatrigger_tavern`](world/areatrigger_tavern.md); innkeeper binds set the
recall point ([npc flags](world/creature_template.md#flag-bitmasks)).

---

## Related Pages

- [Progression System](Progression-System.md) - content patches (different concept!)
- [exploration_basexp](world/exploration_basexp.md) - discovery XP
