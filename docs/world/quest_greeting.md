# quest_greeting Table

Defines greeting text and emotes for quest givers (creatures or game objects).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`type`](#f-type) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`content_default`](#f-content_default) | text |  | NO |  |  |
| [`content_loc1`](#f-content_loc1) | text |  | YES |  |  |
| [`content_loc2`](#f-content_loc2) | text |  | YES |  |  |
| [`content_loc3`](#f-content_loc3) | text |  | YES |  |  |
| [`content_loc4`](#f-content_loc4) | text |  | YES |  |  |
| [`content_loc5`](#f-content_loc5) | text |  | YES |  |  |
| [`content_loc6`](#f-content_loc6) | text |  | YES |  |  |
| [`content_loc7`](#f-content_loc7) | text |  | YES |  |  |
| [`content_loc8`](#f-content_loc8) | text |  | YES |  |  |
| [`emote_id`](#f-emote_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`emote_delay`](#f-emote_delay) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Creature or gameobject entry this greeting belongs to. (see [`creature_template`](creature_template.md).entry or [`gameobject_template`](gameobject_template.md).entry)
- <a id="f-type"></a>**`type`** - Primary Key. Owner type: 0 creature, 1 gameobject.
- <a id="f-content_default"></a>**`content_default`** - Greeting text shown when opening the quest giver window.
- <a id="f-content_loc1"></a>**`content_loc1`** - Localized greeting variants.
- <a id="f-content_loc2"></a>**`content_loc2`** - Localized greeting variants.
- <a id="f-content_loc3"></a>**`content_loc3`** - Localized greeting variants.
- <a id="f-content_loc4"></a>**`content_loc4`** - Localized greeting variants.
- <a id="f-content_loc5"></a>**`content_loc5`** - Localized greeting variants.
- <a id="f-content_loc6"></a>**`content_loc6`** - Localized greeting variants.
- <a id="f-content_loc7"></a>**`content_loc7`** - Localized greeting variants.
- <a id="f-content_loc8"></a>**`content_loc8`** - Localized greeting variants.
- <a id="f-emote_id"></a>**`emote_id`** - Emote played with the greeting. (see `Emotes.dbc`)
- <a id="f-emote_delay"></a>**`emote_delay`** - Delay in ms before the emote fires.
