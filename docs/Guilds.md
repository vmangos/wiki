# Guild System

Guilds in VMaNGOS span the world DB (templates for ranks) and the characters database
(roster state).

---

## Creation

- A player buys a guild charter from a petition NPC (`GUILD_CHARTER_COST` = 1000 copper / 10 s)
  and collects **exactly 9 signatures** (the client hard-caps at 9)
  (`PetitionsHandler.cpp`):
  [`petition`](characters/petition.md) + [`petition_sign`](characters/petition_sign.md).
- One signature per account (`player_account` guard).
- Turning in the completed charter creates the guild rows.

---

## Data Model

| Table ([characters DB](Characters-Database.md)) | Purpose |
| :--- | :--- |
| [`guild`](characters/guild.md) | Guild header: name, leader, creation date, bank money. |
| [`guild_rank`](characters/guild_rank.md) | Rank names/rights per guild; rank count on the header row. |
| [`guild_member`](characters/guild_member.md) | Roster: member guid, rank, public/officer notes. |
| [`guild_eventlog`](characters/guild_eventlog.md) | Recent join/leave/leadership events (capped). |

Guild tabards are client-side customisation only in vanilla (no separate table).

---

## NPC Side

- Petition vendors are normal creatures with `npc_flags = UNIT_NPC_FLAG_PETITIONER` (`0x200`);
  guild tabard NPCs use `UNIT_NPC_FLAG_TABARDDESIGNER` (`0x400`).
- Greeting text comes from the [gossip system](Gossip-System.md).

---

## Related Pages

- [guild](characters/guild.md)
- [Security & RBAC](Security-RBAC.md) - who may create/delete guilds via commands
