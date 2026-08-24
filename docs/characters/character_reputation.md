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

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Character guid (from [`characters`](characters.md).guid).
- <a id="f-faction"></a>**`faction`** - Part of the primary key. Reputation group id ([`faction`](../world/faction.md).id).
- <a id="f-standing"></a>**`standing`** - Numeric reputation points (-42000…42999).
- <a id="f-flags"></a>**`flags`** - State bits (`FactionFlag`): 1 = visible, 2 = *At War*, 4 = hidden from the client reputation pane.

---

### flags Values

| Bit | Meaning |
| ---: | :--- |
| 1 | Faction shown in the reputation pane |
| 2 | *At War* toggled for the faction |
| 4 | Faction hidden from the client reputation pane |
