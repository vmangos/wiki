# migrations Table

Applied migration IDs for the realmd database (see the core `sql/migrations` folder and [Database Setup](../Database-Setup.md)).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | varchar(255) | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Applied migration id from `sql/migrations/<id>_logon.sql`.
