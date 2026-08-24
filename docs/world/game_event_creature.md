# game_event_creature Table

Adds or removes creature spawns while a [`game_event`](game_event.md) is active. Each row binds
an existing spawn (from [`creature`](creature.md)) to an event entry.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  |  |
| [`event`](#f-event) | smallint(6) | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Part of the primary key. Creature spawn GUID (from [`creature`](creature.md).guid).
- <a id="f-event"></a>**`event`** - Part of the primary key. [`game_event`](game_event.md).entry this spawn belongs to.
