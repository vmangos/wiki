# locales_spell Table

Localized spell names, subtitles, descriptions, and aura descriptions.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | smallint(5) unsigned | PRI | NO |  |  |
| [`name_loc1`](#f-name_loc1) | varchar(256) |  | NO | '' |  |
| [`name_loc2`](#f-name_loc2) | varchar(256) |  | NO | '' |  |
| [`name_loc3`](#f-name_loc3) | varchar(256) |  | NO | '' |  |
| [`name_loc4`](#f-name_loc4) | varchar(256) |  | NO | '' |  |
| [`name_loc5`](#f-name_loc5) | varchar(256) |  | NO | '' |  |
| [`name_loc6`](#f-name_loc6) | varchar(256) |  | NO | '' |  |
| [`nameSubtext_loc1`](#f-nameSubtext_loc1) | varchar(256) |  | NO | '' |  |
| [`nameSubtext_loc2`](#f-nameSubtext_loc2) | varchar(256) |  | NO | '' |  |
| [`nameSubtext_loc3`](#f-nameSubtext_loc3) | varchar(256) |  | NO | '' |  |
| [`nameSubtext_loc4`](#f-nameSubtext_loc4) | varchar(256) |  | NO | '' |  |
| [`nameSubtext_loc5`](#f-nameSubtext_loc5) | varchar(256) |  | NO | '' |  |
| [`nameSubtext_loc6`](#f-nameSubtext_loc6) | varchar(256) |  | NO | '' |  |
| [`description_loc1`](#f-description_loc1) | varchar(1024) |  | NO | '' |  |
| [`description_loc2`](#f-description_loc2) | varchar(1024) |  | NO | '' |  |
| [`description_loc3`](#f-description_loc3) | varchar(1024) |  | NO | '' |  |
| [`description_loc4`](#f-description_loc4) | varchar(1024) |  | NO | '' |  |
| [`description_loc5`](#f-description_loc5) | varchar(1024) |  | NO | '' |  |
| [`description_loc6`](#f-description_loc6) | varchar(1024) |  | NO | '' |  |
| [`auraDescription_loc1`](#f-auraDescription_loc1) | varchar(512) |  | NO | '' |  |
| [`auraDescription_loc2`](#f-auraDescription_loc2) | varchar(512) |  | NO | '' |  |
| [`auraDescription_loc3`](#f-auraDescription_loc3) | varchar(512) |  | NO | '' |  |
| [`auraDescription_loc4`](#f-auraDescription_loc4) | varchar(512) |  | NO | '' |  |
| [`auraDescription_loc5`](#f-auraDescription_loc5) | varchar(512) |  | NO | '' |  |
| [`auraDescription_loc6`](#f-auraDescription_loc6) | varchar(512) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Spell id ([`spell_template`](spell_template.md).entry).
- <a id="f-name_loc1"></a>**`name_loc1`** - Localized spell name.
- <a id="f-name_loc2"></a>**`name_loc2`** - Localized spell name.
- <a id="f-name_loc3"></a>**`name_loc3`** - Localized spell name.
- <a id="f-name_loc4"></a>**`name_loc4`** - Localized spell name.
- <a id="f-name_loc5"></a>**`name_loc5`** - Localized spell name.
- <a id="f-name_loc6"></a>**`name_loc6`** - Localized spell name.
- <a id="f-nameSubtext_loc1"></a>**`nameSubtext_loc1`** - Localized subtext (rank line).
- <a id="f-nameSubtext_loc2"></a>**`nameSubtext_loc2`** - Localized subtext (rank line).
- <a id="f-nameSubtext_loc3"></a>**`nameSubtext_loc3`** - Localized subtext (rank line).
- <a id="f-nameSubtext_loc4"></a>**`nameSubtext_loc4`** - Localized subtext (rank line).
- <a id="f-nameSubtext_loc5"></a>**`nameSubtext_loc5`** - Localized subtext (rank line).
- <a id="f-nameSubtext_loc6"></a>**`nameSubtext_loc6`** - Localized subtext (rank line).
- <a id="f-description_loc1"></a>**`description_loc1`** - Localized tooltip description.
- <a id="f-description_loc2"></a>**`description_loc2`** - Localized tooltip description.
- <a id="f-description_loc3"></a>**`description_loc3`** - Localized tooltip description.
- <a id="f-description_loc4"></a>**`description_loc4`** - Localized tooltip description.
- <a id="f-description_loc5"></a>**`description_loc5`** - Localized tooltip description.
- <a id="f-description_loc6"></a>**`description_loc6`** - Localized tooltip description.
- <a id="f-auraDescription_loc1"></a>**`auraDescription_loc1`** - Localized aura description.
- <a id="f-auraDescription_loc2"></a>**`auraDescription_loc2`** - Localized aura description.
- <a id="f-auraDescription_loc3"></a>**`auraDescription_loc3`** - Localized aura description.
- <a id="f-auraDescription_loc4"></a>**`auraDescription_loc4`** - Localized aura description.
- <a id="f-auraDescription_loc5"></a>**`auraDescription_loc5`** - Localized aura description.
- <a id="f-auraDescription_loc6"></a>**`auraDescription_loc6`** - Localized aura description.
