# pool_creature Table

Links creature spawns to spawn pools (group of spawns that share a spawn limit).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO | 0 |  |
| [`pool_entry`](#f-pool_entry) | smallint(5) unsigned | MUL | NO | 0 |  |
| [`chance`](#f-chance) | float unsigned |  | NO | 0 |  |
| [`description`](#f-description) | varchar(255) |  | NO |  |  |
| [`flags`](#f-flags) | int(10) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Creature GUID ([`creature`](creature.md).guid).
- <a id="f-pool_entry"></a>**`pool_entry`** - Pool ID ([`pool_template`](pool_template.md).entry).
- <a id="f-chance"></a>**`chance`** - Probability of spawning (0-100).
- <a id="f-description"></a>**`description`** - Comment.
- <a id="f-flags"></a>**`flags`** - Pool flags.
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
