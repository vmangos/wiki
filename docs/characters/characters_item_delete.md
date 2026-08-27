# characters_item_delete Table

Purge list consumed by the `.character clean items` admin command, which destroys matching items on players (destructive pass runs only from the console).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(11) | UNI | YES |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Unique. Item **template entry id** (matched against ([`item_instance`](item_instance).id).
