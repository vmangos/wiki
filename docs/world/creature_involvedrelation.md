# creature_involvedrelation Table

Maps creatures (NPCs) to quests that they **end**, the turn-in side of the relation pair
(offer side: [`creature_questrelation`](creature_questrelation.md)).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`quest`](#f-quest) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Creature entry ID ([`creature_template`](creature_template.md).entry).
- <a id="f-quest"></a>**`quest`** - Primary Key. Quest ID ([`quest_template`](quest_template.md).entry).
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
