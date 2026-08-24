# Reputation System

How reputation works: faction definitions, gain rates and spillover. Sources:
`src/game/ReputationMgr.cpp`, tables [`faction`](world/faction.md),
[`faction_template`](world/faction_template.md).

---

## The Two Tables

- **[`faction`](world/faction.md)** - one row per *reputation group* players can hold standing with
  (e.g. Stormwind). Defines the rank thresholds, parent chain and spillover.
- **[`faction_template`](world/faction_template.md)** - the combat-side faction of every creature/GO
  ([`creature_template`](world/creature_template.md).faction). Its `friend/enemy` masks decide hostility; its
  `reputationListID` links a creature to a reputation group so killing it grants/denies rep.

Hostility is evaluated through `FactionTemplateReaction`: hated→hostile … friendly→friendly;
players react to creatures via these templates, not via the rep table directly.

---

## Gaining Reputation

| Mechanic | Where configured |
| :--- | :--- |
| Kill credit | creature's faction_template → reputation list id |
| Quest rewards | `quest_template.RepObjectiveFaction/Value`, plus `RewRepFaction*` |
| Items | item spells granting rep |
| Rate multipliers | [`reputation_reward_rate`](world/reputation_reward_rate.md) per faction & zone type |

`Rate.Reputation.Gain` in `mangosd.conf` scales everything globally.

---

## Ranks

Ranks run Hated → Exalted (`REP_HATED=0 … REP_EXALTED=7`, `SharedDefines.h`).
The standing cut-offs between ranks come from `Faction.dbc` (per-faction `ReputationMax`
values), not from SQL; conditions can test them with
`CONDITION_REPUTATION_RANK_MIN/MAX` ([conditions](world/conditions.md)), e.g.
[vendor items](Trainer-Vendor-Guide.md) visible only at Exalted.

---

## Spillover

[`reputation_spillover`](world/reputation_spillover_template.md) defines which parent faction receives
a fraction of gains (e.g. killing Defias raises Stormwind, and partially the other Alliance
cities):

- `faction_id` - the child faction gaining rep,
- `parent_faction` - where spillover goes,
- per-rank rate columns control percentages for hostile/unfriendly/friendly tiers.

---

## Character Side

Standing per player persists in [`character_reputation`](characters/character_reputation.md)
(faction → standing + flags such as "at war").

---

## Related Pages

- [faction](world/faction.md) · [faction_template](world/faction_template.md)
- [Quest System](Quest-System.md) - quest rep rewards
