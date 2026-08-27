# Database Setup & Migrations

How the four databases are created and how schema changes ship with the core.

---

## The Four Databases

| Database | Schema source | Purpose |
| :--- | :--- | :--- |
| `realmd` | [`sql/logon.sql`](https://github.com/vmangos/core/blob/development/sql/logon.sql) | Accounts, realms ([docs](Realmd-Database.md)) |
| [`characters`](characters/characters.md) | [`sql/characters.sql`](https://github.com/vmangos/core/blob/development/sql/characters.sql) | Player state ([docs](Characters-Database.md)) |
| `mangos` (world) | full dump + `sql/migrations` | Game content ([docs](World-Database.md)) |
| `logs` | [`sql/logs.sql`](https://github.com/vmangos/core/blob/development/sql/logs.sql) | Audit logs ([docs](Logs-Database.md)) |

## Getting the World Database

The world database **ships as one complete dump**. You have two options:

1. **Dump + migrations** - import the base dump, then apply the files from
   [`sql/migrations`](https://github.com/vmangos/core/tree/development/sql/migrations) in
   chronological order (see [Migration System](#migration-system)).
2. **Pre-applied release** - download a full database build with all migrations already
   applied; just import and go.

Either way the schema matches what this wiki documents. For the client-side data folders
(`maps/`, `vmaps/`, `mmaps/`, DBCs) use the extraction tools described in
[Maps & Pathfinding](Maps-and-Pathfinding.md).

---

## Migration System

Schema and data changes ship as timestamped SQL files in
[`sql/migrations`](https://github.com/vmangos/core/tree/development/sql/migrations):

```
20210515110157_world.sql
20210615223353_world.sql
…
<timestamp>_characters.sql
<timestamp>_logon.sql
<timestamp>_logs.sql
```

Each file wraps its changes in an `add_migration()` stored procedure that inserts the migration ID
into the target database's [`migrations`](world/migrations.md) table **only if it has not been applied yet**, making the
files safely re-runnable:

```sql
DROP PROCEDURE IF EXISTS add_migration;
DELIMITER ??
CREATE PROCEDURE `add_migration`()
BEGIN
DECLARE v INT DEFAULT 1;
SET v = (SELECT COUNT(*) FROM `migrations` WHERE `id`='20210515110157');
IF v = 0 THEN
INSERT INTO `migrations` VALUES ('20210515110157');
-- Add your query below.
...
-- End of migration.
END IF;
END??
DELIMITER ;
CALL add_migration();
DROP PROCEDURE IF EXISTS add_migration;
```

Each database keeps its own applied-ID list: [`migrations`](characters/migrations.md) in the
characters DB, plus equivalents in realmd, logs and world.

### Creating a New Migration

Two helpers live in `sql/`:

- `make_migration.py` - writes `migrations/<UTC-timestamp>_world.sql` pre-filled with the wrapper.
- `touch_migration.sh` - bash equivalent of the above (also writes world migrations).

Workflow for contributors:

1. Run the helper to create the file.
2. Put your SQL between the marked comments.
3. Name every table with its schema prefix if ambiguous and keep statements idempotent where possible.
4. Submit with your pull request - never edit older migrations.

---

## Applying Migrations

Migrations are plain SQL files; apply them with any client in chronological order:

```bash
mysql -u mangos -p mangos < sql/migrations/20210515110157_world.sql
```

The server also checks the `migrations` table at startup and reports any required
migrations that have not been applied yet.

---

## Verifying Your Setup

- Table counts per schema should match the documentation indexes:
  [world](World-Database.md), [characters](Characters-Database.md),
  [realmd](Realmd-Database.md), [logs](Logs-Database.md).
- Watch the server log at startup for `LOG_DBERROR` messages - they call out missing loot ids,
  invalid conditions and other data problems (see the individual table pages).
