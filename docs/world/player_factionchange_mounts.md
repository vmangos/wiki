# player_factionchange_mounts Table

Maps faction-specific mounts between Alliance and Horde.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`RaceId`](#f-RaceId) | int(8) | PRI | NO |  |  |
| [`MountNum`](#f-MountNum) | int(8) | PRI | NO |  |  |
| [`ItemEntry`](#f-ItemEntry) | int(8) |  | NO |  |  |
| [`Comment`](#f-Comment) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-RaceId"></a>**`RaceId`** - Primary Key. Race ID.
- <a id="f-MountNum"></a>**`MountNum`** - Primary Key. Arbitrary index identifying a mount within a race; mounts of different races sharing the same number are treated as faction equivalents during a race change.
- <a id="f-ItemEntry"></a>**`ItemEntry`** - Mount item ID. (see [`item_template`](item_template.md).entry)
- <a id="f-Comment"></a>**`Comment`** - Description.
