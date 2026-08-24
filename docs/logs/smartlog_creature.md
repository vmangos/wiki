# smartlog_creature Table

'Smart log' of notable creature AI events (e.g. boss deaths with combat time and party composition).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`time`](#f-time) | timestamp |  | NO | current_timestamp() |  |
| [`type`](#f-type) | enum('Death','LongCombat','ScriptInfo','') |  | NO | '' |  |
| [`entry`](#f-entry) | int(11) | MUL | NO | 0 |  |
| [`guid`](#f-guid) | int(11) |  | NO | 0 |  |
| [`specifier`](#f-specifier) | varchar(255) |  | NO | '' |  |
| [`combatTime`](#f-combatTime) | int(11) |  | NO | 0 |  |
| [`content`](#f-content) | varchar(255) |  | NO | '' |  |

---

## Field Breakdown

- <a id="f-time"></a>**`time`** - Event timestamp.
- <a id="f-type"></a>**`type`** - Smart-log category (e.g. Death).
- <a id="f-entry"></a>**`entry`** - Creature template entry.
- <a id="f-guid"></a>**`guid`** - Spawn guid involved.
- <a id="f-specifier"></a>**`specifier`** - "MapName.CreatureName" context string.
- <a id="f-combatTime"></a>**`combatTime`** - Combat duration in seconds before the event.
- <a id="f-content"></a>**`content`** - Serialized context blob (party composition etc.).
