# player_factionchange_reputations Table

Maps faction reputations between Alliance and Horde equivalents.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`alliance_id`](#f-alliance_id) | int(8) | PRI | NO |  |  |
| [`horde_id`](#f-horde_id) | int(8) | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-alliance_id"></a>**`alliance_id`** - Primary Key. Alliance faction ID.; references [`faction`](faction.md).id
- <a id="f-horde_id"></a>**`horde_id`** - Primary Key. Horde faction ID.; references [`faction`](faction.md).id
