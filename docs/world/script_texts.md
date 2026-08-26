# script_texts Table

Generic script texts. This table is deprecated and will be deleted in the future.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) | PRI | NO |  |  |
| [`content_default`](#f-content_default) | text |  | NO |  |  |
| [`content_loc1`](#f-content_loc1) | text |  | YES |  |  |
| [`content_loc2`](#f-content_loc2) | text |  | YES |  |  |
| [`content_loc3`](#f-content_loc3) | text |  | YES |  |  |
| [`content_loc4`](#f-content_loc4) | text |  | YES |  |  |
| [`content_loc5`](#f-content_loc5) | text |  | YES |  |  |
| [`content_loc6`](#f-content_loc6) | text |  | YES |  |  |
| [`content_loc7`](#f-content_loc7) | text |  | YES |  |  |
| [`content_loc8`](#f-content_loc8) | text |  | YES |  |  |
| [`sound`](#f-sound) | mediumint(8) unsigned |  | NO | 0 |  |
| [`type`](#f-type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`language`](#f-language) | tinyint(3) unsigned |  | NO | 0 |  |
| [`emote`](#f-emote) | smallint(5) unsigned |  | NO | 0 |  |
| [`comment`](#f-comment) | text |  | YES |  |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Script text ID. Must be a negative id in the range −1999999…−1000000;
  positive ids are rejected by the core.
- <a id="f-content_default"></a>**`content_default`** - Default text.
- <a id="f-content_loc1"></a>**`content_loc1`** - Localized variant of `content_default` (locale 1).
- <a id="f-content_loc2"></a>**`content_loc2`** - Localized variant of `content_default` (locale 2).
- <a id="f-content_loc3"></a>**`content_loc3`** - Localized variant of `content_default` (locale 3).
- <a id="f-content_loc4"></a>**`content_loc4`** - Localized variant of `content_default` (locale 4).
- <a id="f-content_loc5"></a>**`content_loc5`** - Localized variant of `content_default` (locale 5).
- <a id="f-content_loc6"></a>**`content_loc6`** - Localized variant of `content_default` (locale 6).
- <a id="f-content_loc7"></a>**`content_loc7`** - Localized variant of `content_default` (locale 7).
- <a id="f-content_loc8"></a>**`content_loc8`** - Russian locale variant of `content_default`.
- <a id="f-sound"></a>**`sound`** - Sound ID. (see [`sound_entries`](sound_entries.md).id)
- <a id="f-type"></a>**`type`** - Chat type (say/yell/emote…) used when the core speaks this text.
- <a id="f-language"></a>**`language`** - Language ID. (see `Languages.dbc`)
- <a id="f-emote"></a>**`emote`** - Emote ID. (see `Emotes.dbc`)
- <a id="f-comment"></a>**`comment`** - Human label describing where the text is used.
