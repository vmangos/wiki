# migrations Table

Tracks applied database migrations (schema updates).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | varchar(255) | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Migration identifier = timestamp prefix of the migration filename
  (filename minus the `_<database>` suffix and the `.sql` extension), e.g. `20210515110157` for
  `20210515110157_world.sql` in
  [`sql/migrations`](https://github.com/vmangos/core/tree/development/sql/migrations).
  Each database (world/characters/realmd/logs) has its own `migrations` table.
