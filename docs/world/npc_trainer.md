# npc_trainer Table

Defines spells taught by specific NPC trainers (per creature entry, or shared via [`npc_trainer_template`](npc_trainer_template.md)).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`spell`](#f-spell) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`spellcost`](#f-spellcost) | int(10) unsigned |  | NO | 0 |  |
| [`reqskill`](#f-reqskill) | smallint(5) unsigned |  | NO | 0 |  |
| [`reqskillvalue`](#f-reqskillvalue) | smallint(5) unsigned |  | NO | 0 |  |
| [`reqlevel`](#f-reqlevel) | tinyint(3) unsigned |  | NO | 0 |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |
| [`build_max`](#f-build_max) | smallint(4) unsigned | PRI | NO | 5875 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - NPC entry ID ([`creature_template`](creature_template.md).entry).
- <a id="f-spell"></a>**`spell`** - Spell ID to teach ([`spell_template`](spell_template.md).entry).
- <a id="f-spellcost"></a>**`spellcost`** - Cost to learn (copper).
- <a id="f-reqskill"></a>**`reqskill`** - Required skill ID.
- <a id="f-reqskillvalue"></a>**`reqskillvalue`** - Required skill level.
- <a id="f-reqlevel"></a>**`reqlevel`** - Required character level.
- <a id="f-build_max"></a><a id="f-build_min"></a>**`build_min` / `build_max`** - Client build range.
