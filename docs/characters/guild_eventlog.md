# guild_eventlog Table

Recent guild events (member join/leave, leadership changes) shown in-game.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guild_id`](#f-guild_id) | int(11) | PRI | NO |  |  |
| [`log_guid`](#f-log_guid) | int(11) | PRI | NO |  |  |
| [`event_type`](#f-event_type) | tinyint(1) |  | NO |  |  |
| [`player_guid1`](#f-player_guid1) | int(11) | MUL | NO |  |  |
| [`player_guid2`](#f-player_guid2) | int(11) | MUL | NO |  |  |
| [`new_rank`](#f-new_rank) | tinyint(2) |  | NO |  |  |
| [`timestamp`](#f-timestamp) | bigint(20) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-guild_id"></a>**`guild_id`** - Primary Key. Guild the event belongs to.
- <a id="f-log_guid"></a>**`log_guid`** - Primary Key. Log entry counter.
- <a id="f-event_type"></a>**`event_type`** - Event code (`GuildEventLogEntryTypes`): 1 invite, 2 join, 3 promotion,
  4 demotion, 5 uninvite, 6 leave.
- <a id="f-player_guid1"></a>**`player_guid1`** - Actors involved (e.g. leaver + issuer).
- <a id="f-player_guid2"></a>**`player_guid2`** - Actors involved (e.g. leaver + issuer).
- <a id="f-new_rank"></a>**`new_rank`** - Rank after promotion events.
- <a id="f-timestamp"></a>**`timestamp`** - When it happened. Table keeps a rolling recent window only.
