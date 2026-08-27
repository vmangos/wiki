# game_event_status Table

Restart persistence for active [`game_event`](../world/game_event.md) entries: rows track **every** currently
active event (scheduled or admin-started). Written on activation, deleted on stop; at startup the list is
read to resume events and then truncated.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`event`](#f-event) | smallint(6) unsigned | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-event"></a>**`event`** - Primary Key. [`game_event`](../world/game_event.md).entry of an event that was active when the server last stopped.
