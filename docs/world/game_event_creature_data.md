# game_event_creature_data Table

Overrides creature data (display, equipment, spells) during events.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`entry_id`](#f-entry_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`display_id`](#f-display_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`equipment_id`](#f-equipment_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`spell_start`](#f-spell_start) | smallint(5) unsigned |  | NO | 0 |  |
| [`spell_end`](#f-spell_end) | smallint(5) unsigned |  | NO | 0 |  |
| [`event`](#f-event) | smallint(5) unsigned | PRI | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Creature spawn GUID ([`creature`](creature.md).guid).
- <a id="f-patch"></a>**`patch`** - Primary Key. Client patch version.
- <a id="f-event"></a>**`event`** - Primary Key. Event ID. (see [`game_event`](game_event.md).entry)
- <a id="f-entry_id"></a>**`entry_id`** - Override creature template ID.
- <a id="f-display_id"></a>**`display_id`** - Override display model.
- <a id="f-equipment_id"></a>**`equipment_id`** - Override equipment set.
- <a id="f-spell_start"></a>**`spell_start`** - Spell to cast at event start.
- <a id="f-spell_end"></a>**`spell_end`** - Spell to cast at event end.
