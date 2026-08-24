# playerbot Table

State storage for player bots managed by the built-in bot system.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`char_guid`](#f-char_guid) | bigint(20) unsigned | PRI | NO |  |  |
| [`chance`](#f-chance) | int(10) unsigned |  | NO | 10 |  |
| [`comment`](#f-comment) | varchar(255) |  | YES |  |  |
| [`ai`](#f-ai) | varchar(50) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-char_guid"></a>**`char_guid`** - Primary Key. Character guid usable as bot ([`characters`](characters.md).guid).
- <a id="f-chance"></a>**`chance`** - Relative chance the bot system picks this character.
- <a id="f-comment"></a>**`comment`** - Descriptive label.
- <a id="f-ai"></a>**`ai`** - Preferred AI module name for the bot.
