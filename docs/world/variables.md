# variables Table

Key-value store for core variables (e.g., world state, script tracking).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`index`](#f-index) | int(10) unsigned | PRI | NO | 0 |  |
| [`value`](#f-value) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-index"></a>**`index`** - Primary Key. Variable key.
- <a id="f-value"></a>**`value`** - Variable value.
