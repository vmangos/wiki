# creature_respawn Table

Persisted respawn times of creatures so respawn state survives server restarts.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO | 0 |  |
| [`respawn_time`](#f-respawn_time) | bigint(20) |  | NO | 0 |  |
| [`instance`](#f-instance) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`map`](#f-map) | int(5) unsigned |  | YES | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Creature spawn guid (from [`creature`](../world/creature.md).guid).
- <a id="f-respawn_time"></a>**`respawn_time`** - Unix time when it becomes alive again.
- <a id="f-instance"></a>**`instance`** - Primary Key. Instance-bound respawn or 0 for world spawns ([`instance`](instance.md).id).
- <a id="f-map"></a>**`map`** - Map id.
