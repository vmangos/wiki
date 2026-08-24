# guild_rank Table

Rank definitions per guild (rights and money withdraw limits).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guild_id`](#f-guild_id) | int(6) unsigned | PRI | NO | 0 |  |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  |  |
| [`name`](#f-name) | varchar(255) |  | NO | '' |  |
| [`rights`](#f-rights) | int(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guild_id"></a>**`guild_id`** - Primary Key. Guild reference.
- <a id="f-id"></a>**`id`** - Primary Key. Rank number (0 = guild master).
- <a id="f-name"></a>**`name`** - Rank title.
- <a id="f-rights"></a>**`rights`** - Permission bitmask (`GuildRankRights` / `GR_RIGHT_*`): guild/officer chat listen & speak, promote/demote, invite/remove, set MOTD, edit/view public and officer notes, modify guild info.
