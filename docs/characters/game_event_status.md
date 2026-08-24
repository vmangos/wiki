# game_event_status Table

Manual override of [`game_event`](../world/game_event.md) state set by admins (start/stop events independent of their schedule).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`event`](#f-event) | smallint(6) unsigned | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-event"></a>**`event`** - Primary Key. [`game_event`](../world/game_event.md).entry forced started/stopped by an admin; overrides scheduling until removed.
