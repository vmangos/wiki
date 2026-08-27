# areatrigger_involvedrelation Table

Associates area triggers with quest completion. When a player enters the trigger, the associated quest is marked as complete (provided the quest has the `QUEST_SPECIAL_FLAG_EXPLORATION_OR_EVENT` flag set).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`quest`](#f-quest) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Areatrigger ID from [`areatrigger_template`](areatrigger_template.md).entry.
- <a id="f-quest"></a>**`quest`** - Quest ID from [`quest_template`](quest_template.md).entry. This quest will be completed when the player reaches the trigger. The quest must have the special flag `QUEST_SPECIAL_FLAG_EXPLORATION_OR_EVENT` (2) set.
