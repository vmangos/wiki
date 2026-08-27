# Character Login Pipeline

What the server loads when a player logs in, and which tables feed it. The query set lives in
`Player::_LoadFrom` / `PLAYER_LOGIN_QUERY_*` (`src/game/Objects/Player.cpp`).

---

## Load Order

| Step | Data | Source table(s) |
| :---: | :--- | :--- |
| 1 | Character row: vitals, position, money, appearance | [`characters`](characters/characters.md) |
| 2 | Home bind (hearthstone point) | [`character_homebind`](characters/character_homebind.md) |
| 3 | Group membership | [`groups`](characters/groups.md), [`group_member`](characters/group_member.md) |
| 4 | Honour CP for today | [`character_honor_cp`](characters/character_honor_cp.md) |
| 5 | Instance saves & BG data | [`character_instance`](characters/character_instance.md), [`character_battleground_data`](characters/character_battleground_data.md) |
| 6 | Guild | [`guild_member`](characters/guild_member.md), [`guild_rank`](characters/guild_rank.md) |
| 7 | Skills (+ forgotten skills) | [`character_skills`](characters/character_skills.md), [`character_forgotten_skills`](characters/character_forgotten_skills.md) |
| 8 | Auras that persist | [`character_aura`](characters/character_aura.md) |
| 9 | Spells | [`character_spell`](characters/character_spell.md) |
| 10 | Quest state | [`character_queststatus`](characters/character_queststatus.md) |
| 11 | Reputations | [`character_reputation`](characters/character_reputation.md) |
| 12 | Inventory items | [`character_inventory`](characters/character_inventory.md) → [`item_instance`](characters/item_instance.md) |
| 13 | Open item loot | [`item_loot`](characters/item_loot.md) |
| 14 | Spell cooldowns | [`character_spell_cooldown`](characters/character_spell_cooldown.md) |

After the load phase the world sends login packets; `online` on the character row flips to 1
until logout.

---

## Why It Matters

- **Missing rows** (e.g. an inventory entry without its [`item_instance`](characters/item_instance.md)) are logged as DB errors
  and skipped, so keep referential integrity.
- **Corrupt position** (bad map/coords) triggers a home-bind fallback from
  [`character_homebind`](characters/character_homebind.md).
- **Bots** reuse the same pipeline when `PlayerBot.AllowSaving` is enabled
  ([Player Bots](Player-Bots.md)).

---

## Related Pages

- [Characters Database index](Characters-Database.md)
- [Server Architecture](Server-Architecture.md)
