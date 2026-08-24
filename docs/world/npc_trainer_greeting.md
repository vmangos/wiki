# npc_trainer_greeting Table

Defines custom greeting texts for specific trainer NPCs.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | int(11) unsigned | PRI | NO | 0 |  |
| [`content_default`](#f-content_default) | text |  | NO |  |  |
| [`content_loc1`](#f-content_loc1) | text |  | NO |  |  |
| [`content_loc2`](#f-content_loc2) | text |  | NO |  |  |
| [`content_loc3`](#f-content_loc3) | text |  | NO |  |  |
| [`content_loc4`](#f-content_loc4) | text |  | NO |  |  |
| [`content_loc5`](#f-content_loc5) | text |  | NO |  |  |
| [`content_loc6`](#f-content_loc6) | text |  | NO |  |  |
| [`content_loc7`](#f-content_loc7) | text |  | NO |  |  |
| [`content_loc8`](#f-content_loc8) | text |  | NO |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Trainer creature entry. (see [`creature_template`](creature_template.md).entry)
- <a id="f-content_default"></a>**`content_default`** - Greeting text shown when opening the trainer window.
- <a id="f-content_loc1"></a>**`content_loc1`** - Localized greeting (locale 1).
- <a id="f-content_loc2"></a>**`content_loc2`** - Localized greeting (locale 2).
- <a id="f-content_loc3"></a>**`content_loc3`** - Localized greeting (locale 3).
- <a id="f-content_loc4"></a>**`content_loc4`** - Localized greeting (locale 4).
- <a id="f-content_loc5"></a>**`content_loc5`** - Localized greeting (locale 5).
- <a id="f-content_loc6"></a>**`content_loc6`** - Localized greeting (locale 6).
- <a id="f-content_loc7"></a>**`content_loc7`** - Localized greeting (locale 7).
- <a id="f-content_loc8"></a>**`content_loc8`** - Russian locale variant.
