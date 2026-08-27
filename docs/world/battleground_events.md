# battleground_events Table

Defines events that spawn creatures and gameobjects during battleground matches.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`map`](#f-map) | smallint(5) unsigned | PRI | NO |  |  |
| [`event1`](#f-event1) | tinyint(3) unsigned | PRI | NO |  |  |
| [`event2`](#f-event2) | tinyint(3) unsigned | PRI | NO |  |  |
| [`description`](#f-description) | varchar(255) |  | NO |  |  |

---

## Field Breakdown

- <a id="f-map"></a>**`map`** - Primary Key. Map ID: (see [`map_template`](map_template.md).entry)
  - `30` - Alterac Valley
  - `489` - Warsong Gulch
  - `529` - Arathi Basin
- <a id="f-event1"></a>**`event1`** - Primary Key. Main event ID.
- <a id="f-event2"></a>**`event2`** - Primary Key. Sub-event ID.
- <a id="f-description"></a>**`description`** - Event name (not used by core - descriptive only).
