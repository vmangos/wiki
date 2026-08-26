# characters_guid_delete Table

List of character GUIDs purged by the `.character clean todelete` admin command.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(11) | UNI | YES |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Unique. Character guid queued for final deletion via `.character clean todelete`.
