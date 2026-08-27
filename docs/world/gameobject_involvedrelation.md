# gameobject_involvedrelation Table

Maps game objects to quests - used for quest completion (e.g., click object to complete).

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

- <a id="f-id"></a>**`id`** - Primary Key. Game object template ID ([`gameobject_template`](gameobject_template.md).entry).
- <a id="f-quest"></a>**`quest`** - Primary Key. Quest ID. (see [`quest_template`](quest_template.md).entry)
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
