# instance_creature_kills Table

Statistics log of creature kills inside instanced encounters.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`mapId`](#f-mapId) | int(10) unsigned | PRI | NO |  |  |
| [`creatureEntry`](#f-creatureEntry) | int(10) unsigned | PRI | NO |  |  |
| [`spellEntry`](#f-spellEntry) | int(10) | PRI | NO |  |  |
| [`count`](#f-count) | int(10) unsigned |  | NO |  |  |

---

## Field Breakdown

- <a id="f-mapId"></a>**`mapId`** - Primary Key. Map where the kill happened.
- <a id="f-creatureEntry"></a>**`creatureEntry`** - Primary Key. Creature killed.
- <a id="f-spellEntry"></a>**`spellEntry`** - Primary Key. Finishing spell (0 = melee/direct).
- <a id="f-count"></a>**`count`** - Aggregated kill count.
