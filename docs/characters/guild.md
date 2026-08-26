# guild Table

Guild headers: name, leader, creation date, tabard emblem, public info and MOTD.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guild_id`](#f-guild_id) | int(6) unsigned | PRI | NO | 0 |  |
| [`name`](#f-name) | varchar(255) |  | NO | '' |  |
| [`leader_guid`](#f-leader_guid) | int(6) unsigned |  | NO | 0 |  |
| [`emblem_style`](#f-emblem_style) | int(5) |  | NO | 0 |  |
| [`emblem_color`](#f-emblem_color) | int(5) |  | NO | 0 |  |
| [`border_style`](#f-border_style) | int(5) |  | NO | 0 |  |
| [`border_color`](#f-border_color) | int(5) |  | NO | 0 |  |
| [`background_color`](#f-background_color) | int(5) |  | NO | 0 |  |
| [`info`](#f-info) | text |  | NO |  |  |
| [`motd`](#f-motd) | varchar(255) |  | NO | '' |  |
| [`create_date`](#f-create_date) | bigint(20) |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guild_id"></a>**`guild_id`** - Primary Key. Guild identifier.
- <a id="f-name"></a>**`name`** - Guild name (unique per realm).
- <a id="f-leader_guid"></a>**`leader_guid`** - Guild master character guid ([`characters`](characters.md).guid).
- <a id="f-emblem_style"></a>**`emblem_style`** - Guild tabard emblem style.
- <a id="f-emblem_color"></a>**`emblem_color`** - Guild tabard emblem colour.
- <a id="f-border_style"></a>**`border_style`** - Guild tabard border style.
- <a id="f-border_color"></a>**`border_color`** - Guild tabard border colour.
- <a id="f-background_color"></a>**`background_color`** - Guild tabard background colour.
- <a id="f-info"></a>**`info`** - Public guild information text.
- <a id="f-motd"></a>**`motd`** - Message of the day shown to members at login.
- <a id="f-create_date"></a>**`create_date`** - Date the guild was founded.
