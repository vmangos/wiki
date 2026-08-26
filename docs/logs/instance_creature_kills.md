# instance_creature_kills Table

Statistics log of **player deaths caused by creatures** inside instanced maps (not creature kills by players).

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

- <a id="f-mapId"></a>**`mapId`** - Primary Key. Map where the deaths happened.
- <a id="f-creatureEntry"></a>**`creatureEntry`** - Primary Key. Killing creature.
- <a id="f-spellEntry"></a>**`spellEntry`** - Primary Key. Killing-blow spell (0 = melee/direct).
- <a id="f-count"></a>**`count`** - Aggregated player death count for this creature+spell combination.
