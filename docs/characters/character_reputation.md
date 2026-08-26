# character_reputation Table

Reputation standing per faction for every character.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`faction`](#f-faction) | int(11) unsigned | PRI | NO | 0 |  |
| [`standing`](#f-standing) | int(11) |  | NO | 0 |  |
| [`flags`](#f-flags) | int(11) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-faction"></a>**`faction`** - Primary Key. Reputation group id ([`faction`](../world/faction.md).id).
- <a id="f-standing"></a>**`standing`** - Numeric reputation points (-42000…42999).
- <a id="f-flags"></a>**`flags`** - State bits (`FactionFlags`, `ReputationMgr.h`): 1 = visible, 2 = *At War*, 4 = hidden,
  8 = invisibility forced by core, 16 = peace forced by core, 32 = marked inactive by the player, 64 = rival.

---

### flags Values

| Bit | Meaning |
| ---: | :--- |
| 1 | Faction shown in the reputation pane |
| 2 | *At War* toggled for the faction |
| 4 | Faction hidden from the client reputation pane |
| 8 | Visibility forced by core (e.g. during events) |
| 16 | At-war/peace state forced by core |
| 32 | Faction marked inactive by player (XP gain off) |
| 64 | Rival faction (forced hostile) |

> Bits 8, 16 and 64 are core-managed but can appear in saved rows; bit 32 is explicitly restored from the DB at load.
