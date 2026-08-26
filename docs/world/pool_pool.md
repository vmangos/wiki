# pool_pool Table

Defines nested pools - a pool within a pool, with shared chance.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`pool_id`](#f-pool_id) | smallint(5) unsigned | PRI | NO | 0 |  |
| [`mother_pool`](#f-mother_pool) | smallint(5) unsigned | MUL | NO | 0 |  |
| [`chance`](#f-chance) | float |  | NO | 0 |  |
| [`description`](#f-description) | varchar(255) |  | NO |  |  |
| [`flags`](#f-flags) | int(10) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-pool_id"></a>**`pool_id`** - Primary Key. Child pool ID.; references [`pool_template`](pool_template.md).entry
- <a id="f-mother_pool"></a>**`mother_pool`** - Parent pool ID.; references [`pool_template`](pool_template.md).entry
- <a id="f-chance"></a>**`chance`** - Spawn chance within the parent pool: `0` = equal share among all zero-chance members; explicit percentages must sum to 100 and apply only when the parent pool's `max_limit` is 1.
- <a id="f-description"></a>**`description`** - Comment.
- <a id="f-flags"></a>**`flags`** - Pool flags.
