# migrations Table

Tracks applied database migrations (schema updates).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | varchar(255) | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Migration identifier = filename stem of the SQL file in
  [`sql/migrations`](https://github.com/vmangos/core/tree/development/sql/migrations).
