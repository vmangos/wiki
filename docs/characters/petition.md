# petition Table

Charter petitions for forming guilds (arena teams are not part of 1.12).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`owner_guid`](#f-owner_guid) | int(10) unsigned | PRI | NO |  |  |
| [`petition_guid`](#f-petition_guid) | int(10) unsigned |  | YES | 0 |  |
| [`charter_guid`](#f-charter_guid) | int(10) unsigned | UNI | YES |  |  |
| [`name`](#f-name) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-owner_guid"></a>**`owner_guid`** - Primary Key. Charter holder.
- <a id="f-petition_guid"></a>**`petition_guid`** - Petition identifier (referenced by [`petition_sign`](petition_sign.md).petition_guid).
- <a id="f-charter_guid"></a>**`charter_guid`** - Unique. Guid of the physical charter item held by the owner.
- <a id="f-name"></a>**`name`** - Requested guild name.
