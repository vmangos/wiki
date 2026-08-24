# command Table

Overrides the default security level and provides help text for in-game chat commands.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`name`](#f-name) | varchar(50) | PRI | NO | '' |  |
| [`security`](#f-security) | tinyint(3) unsigned |  | NO | 0 |  |
| [`help`](#f-help) | longtext |  | YES |  |  |
| [`flags`](#f-flags) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-name"></a>**`name`** - Primary Key. Full command name (including categories, e.g., `.tele`).
- <a id="f-security"></a>**`security`** - Minimum account rank: `0` = player, `1` = moderator, `2` = ticketmaster, `3` = gamemaster, `4` = basic admin, `5` = developer, `6` = administrator, up to `7` = console only.
- <a id="f-help"></a>**`help`** - Usage information shown when the command is used with invalid parameters.
- <a id="f-flags"></a>**`flags`** - Bitmask:
  - `0x01` - Only on self (cannot target others).
  - `0x02` - Critical - usage is logged.
