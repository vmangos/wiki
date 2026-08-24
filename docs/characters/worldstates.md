# worldstates Table

World state variables broadcast to clients (BG scores, AQ war effort state…).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(11) | UNI | YES |  |  |
| [`value`](#f-value) | int(11) |  | YES |  |  |
| [`comment`](#f-comment) | varchar(255) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Unique. Worldstate variable id (client-known ids for BG scores, AQ war effort…).
- <a id="f-value"></a>**`value`** - Current integer value broadcast to clients.
- <a id="f-comment"></a>**`comment`** - Human-readable label.
