# Player Bots

VMaNGOS ships a full player-bot framework (`src/game/PlayerBots/`, ~15k lines): bots are real
player characters driven by the server, useful for testing, populating battlegrounds or soloing
content. Bots use the normal player pipeline, so they exercise spells, AI and combat like players.

---

## Bot Types

| Class | Purpose |
| :--- | :--- |
| `PlayerBotAI` | Base class / generic bot behaviour |
| `BattleBotAI` | Battleground bots (fight objectives, use hard-coded BG waypoints) |
| `PartyBotAI` | Party/raid follower bots with role support (tank/healer/dps) |
| `CombatBotBaseAI` | Shared duelling/combat drill logic |

---

## Commands

All commands require Administrator level; see [GM Commands](GM-Commands.md) for the full tree.

**Bots** (`bot …`, works from console):

| Command | Effect |
| :--- | :--- |
| `bot add <name>` | Spawn a specific character as a bot |
| `bot ranadd` | Add a random character as bot |
| `bot add_all` | Add all eligible characters |
| `bot delete <name>` | Remove a bot |
| `bot start` / `bot stop` | Start/stop the bot engine |
| `bot info` | Show current bots and state |
| `bot reload` | Reload configuration |

**Party bots** (`partybot …`, in-game only):

| Group | Subcommands |
| :--- | :--- |
| Roster | `add`, `clone`, `load`, `remove` |
| Roles & combat | `setrole`, `attackstart`, `attackstop`, `caststart`, `caststop`, `aoe`, `pull` |
| Targeting marks | `ccmark`, `focusmark`, `clearmarks` |
| Movement/objects | `cometome`, `usegobject`, `pause`, `unpause` |
| Gear | `unequip` |

`partybot clone` duplicates your own character as a bot; `setrole` assigns
roles from `CombatBotRoles` (`SharedDefines.h`) used by `PartyBotAI`:

| Value | Role |
| :---: | :--- |
| 1 | Melee DPS |
| 2 | Ranged DPS |
| 3 | Tank |
| 4 | Healer |

---

## Configuration

From `mangosd.conf` ("Player Bots" category):

- `RandomBot.Enable` - automatic background population.
- `RandomBot.MinBots` / `RandomBot.MaxBots` - target population range.
- `RandomBot.Refresh` - respawn/re-evaluation interval.
- `PlayerBot.AllowSaving` - persist bot state on logout.
- `PlayerBot.ShowInWhoList` - whether bots answer `/who`.
- `PlayerBot.UpdateMs`, `PlayerBot.Debug` - performance and logging.

---

### Database-driven AI selection

Rows in the [`playerbot`](characters/playerbot.md) table pick their behaviour via the `ai`
column using these factory names (`CreatePlayerBotAI`):

`MageOrgrimmarAttackerAI` · `IronforgePopulationAI` · `StormwindPopulationAI` ·
`OrgrimmarPopulationAI` · `PlayerBotFleeingAI` · *(empty)* = generic `PlayerBotAI`.

### Battleground waypoints

`BattleBotWaypoints.cpp` (~2 200 lines) hard-codes AV/WSG/AB path nodes the battle bots follow
per map and team; objectives routing is driven from these tables in code rather than SQL.

## Persistence

- Characters chosen for bots can be stored in the [`playerbot`](characters/playerbot.md)
  table (`char_guid`, preferred `ai`, spawn `chance`, `comment`) so the same cast returns
  across restarts.
- With `PlayerBot.AllowSaving = 1` bots save like real players into the
  [characters database](Characters-Database.md).

---

## Related Pages

- [GM Commands Reference](GM-Commands.md)
- [Anticheat](Anticheat.md)
