# guild_member Table

Guild roster with rank and public/officer notes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guild_id`](#f-guild_id) | int(6) unsigned | MUL | NO | 0 |  |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`rank`](#f-rank) | tinyint(2) unsigned |  | NO | 0 |  |
| [`player_note`](#f-player_note) | varchar(255) |  | NO | '' |  |
| [`officer_note`](#f-officer_note) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-guild_id"></a>**`guild_id`** - Guild reference.
- <a id="f-guid"></a>**`guid`** - Primary Key. Member character ([`characters`](characters.md).guid).
- <a id="f-rank"></a>**`rank`** - Rank id within the guild ([`guild_rank`](guild_rank.md).id).
- <a id="f-player_note"></a>**`player_note`** - Public note visible to all members.
- <a id="f-officer_note"></a>**`officer_note`** - Officer-only note.
