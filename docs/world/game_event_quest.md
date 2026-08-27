# game_event_quest Table

Makes quests available only during specific events.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`quest`](#f-quest) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`event`](#f-event) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-quest"></a>**`quest`** - Primary Key. Quest ID. (see [`quest_template`](quest_template.md).entry)
- <a id="f-event"></a>**`event`** - Primary Key. Event ID. (see [`game_event`](game_event.md).entry)
- <a id="f-patch_min"></a>**`patch_min`** - Minimum patch version.
