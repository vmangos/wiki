# pool_gameobject_template Table

Links game object template IDs to spawn pools.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(10) unsigned | PRI | NO | 0 |  |
| [`pool_entry`](#f-pool_entry) | smallint(5) unsigned | MUL | NO | 0 |  |
| [`chance`](#f-chance) | float unsigned |  | NO | 0 |  |
| [`description`](#f-description) | varchar(255) |  | NO |  |  |
| [`flags`](#f-flags) | int(10) unsigned |  | NO | 0 |  |
| [`patch_min`](#f-patch_min) | tinyint(3) unsigned |  | NO | 0 |  |
| [`patch_max`](#f-patch_max) | tinyint(3) unsigned |  | NO | 10 |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Game object template ID ([`gameobject_template`](gameobject_template.md).entry).
- <a id="f-pool_entry"></a>**`pool_entry`** - Pool ID. (see [`pool_template`](pool_template.md).entry)
- <a id="f-chance"></a>**`chance`** - Spawn chance: `0` = equal share among all zero-chance members; explicit percentages must sum to 100 and apply only when the pool's `max_limit` is 1.
- <a id="f-description"></a>**`description`** - Comment.
- <a id="f-flags"></a>**`flags`** - Pool flags: `0x1` = auto-spawn (forced by core), `0x2` = max-limit scales linearly with population (`MAXLIMIT_SCALING_LINEAR`).
- <a id="f-patch_max"></a><a id="f-patch_min"></a>**`patch_min` / `patch_max`** - Client patch range.
