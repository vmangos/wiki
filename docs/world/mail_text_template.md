# mail_text_template Table

Defines mail body text with localized support.

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

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Mail template id referenced by reward/game systems.
- <a id="f-content_default"></a>**`content_default`** - Default text (English).
- <a id="f-content_loc1"></a>**`content_loc1`** - Localized body text; subject/subject_locN may exist depending on schema revision.
- <a id="f-content_loc2"></a>**`content_loc2`** - Localized body text; subject/subject_locN may exist depending on schema revision.
- <a id="f-content_loc3"></a>**`content_loc3`** - Localized body text; subject/subject_locN may exist depending on schema revision.
- <a id="f-content_loc4"></a>**`content_loc4`** - Localized body text; subject/subject_locN may exist depending on schema revision.
- <a id="f-content_loc5"></a>**`content_loc5`** - Localized body text; subject/subject_locN may exist depending on schema revision.
- <a id="f-content_loc6"></a>**`content_loc6`** - Localized body text; subject/subject_locN may exist depending on schema revision.
- <a id="f-content_loc7"></a>**`content_loc7`** - Localized body text; subject/subject_locN may exist depending on schema revision.
