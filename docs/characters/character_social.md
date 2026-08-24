# character_social Table

Friends and ignores of each character.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`friend`](#f-friend) | int(11) unsigned | PRI | NO | 0 |  |
| [`flags`](#f-flags) | tinyint(1) unsigned | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character owning the social entry ([`characters`](characters.md).guid).
- <a id="f-friend"></a>**`friend`** - Primary Key. The other character's guid ([`characters`](characters.md).guid).
- <a id="f-flags"></a>**`flags`** - Primary Key. Relationship type: 1 = friend, 2 = ignored. One row per relationship type between two characters.
