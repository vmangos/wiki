# script_escort_data Table

Defines escort quest data - creature, quest, and faction override.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`creature_id`](#f-creature_id) | int(11) | UNI | YES |  |  |
| [`quest`](#f-quest) | int(11) |  | YES |  |  |
| [`escort_faction`](#f-escort_faction) | int(11) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-creature_id"></a>**`creature_id`** - Escort NPC entry. (see [`creature_template`](creature_template.md).entry)
- <a id="f-quest"></a>**`quest`** - Associated quest. (see [`quest_template`](quest_template.md).entry)
- <a id="f-escort_faction"></a>**`escort_faction`** - Faction override during escort.
