# mangos_string Table

Core system strings used by the server for messages, errors, and GM commands.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`content_default`](#f-content_default) | text |  | NO |  |  |
| [`content_loc1`](#f-content_loc1) | text |  | YES |  |  |
| [`content_loc2`](#f-content_loc2) | text |  | YES |  |  |
| [`content_loc3`](#f-content_loc3) | text |  | YES |  |  |
| [`content_loc4`](#f-content_loc4) | text |  | YES |  |  |
| [`content_loc5`](#f-content_loc5) | text |  | YES |  |  |
| [`content_loc6`](#f-content_loc6) | text |  | YES |  |  |
| [`content_loc7`](#f-content_loc7) | text |  | YES |  |  |
| [`content_loc8`](#f-content_loc8) | text |  | YES |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Core message string id (hardcoded references).
- <a id="f-content_default"></a>**`content_default`** - English text with %-format placeholders matching core usage.
- <a id="f-content_loc1"></a>**`content_loc1`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc2"></a>**`content_loc2`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc3"></a>**`content_loc3`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc4"></a>**`content_loc4`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc5"></a>**`content_loc5`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc6"></a>**`content_loc6`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc7"></a>**`content_loc7`** - Localized variants; empty falls back to `content_default`.
- <a id="f-content_loc8"></a>**`content_loc8`** - Localized variants; empty falls back to `content_default`.
