# game_event_gameobject Table

Spawns game objects only during specific game events.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  |  |
| [`event`](#f-event) | smallint(6) | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Game object GUID ([`gameobject`](gameobject.md).guid).
- <a id="f-event"></a>**`event`** - Primary Key. Event ID ([`game_event`](game_event.md).entry).
