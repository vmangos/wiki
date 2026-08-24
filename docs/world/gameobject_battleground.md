# gameobject_battleground Table

Links game objects to battleground events (e.g., flag spawns, towers).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  |  |
| [`event1`](#f-event1) | tinyint(3) unsigned | PRI | NO |  |  |
| [`event2`](#f-event2) | tinyint(3) unsigned | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Game object spawn GUID ([`gameobject`](gameobject.md).guid).
- <a id="f-event1"></a>**`event1`** - Part of the primary key. First event index (joins [`battleground_events`](battleground_events.md).event1 together with the object's map).
- <a id="f-event2"></a>**`event2`** - Part of the primary key. Second event index (joins [`battleground_events`](battleground_events.md).event2).
