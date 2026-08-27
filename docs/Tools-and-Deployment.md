# Tools & Deployment

Helper tooling shipped in the repository beyond the two server binaries.

---

## Build & CI

### Docker build (`contrib/docker-build/`)

Builds Linux binaries inside a container without touching your host toolchain:

```bash
docker build -t vmangos-build .          # from contrib/docker-build/
docker run --rm -v /opt/vmangos/out:/root/vmangos/out vmangos-build
```

The container pulls the latest development sources, compiles and drops binaries into the
mounted folder.

### git_id (`contrib/git_id/`)

Generates a header with the current git revision so [`uptime`](realmd/uptime.md).revision
([realmd database](Realmd-Database.md)) and logs can identify the exact build.

---

## Data Tools

| Tool | Purpose |
| :--- | :--- |
| `contrib/extractor` | Client MPQs → `maps/` + DBC files |
| `contrib/vmap_extractor` / `contrib/vmap_assembler` | Collision/LOS geometry → `vmaps/` |
| `contrib/mmap` (+ `mmap_extract.py`, `config.json`) | Navigation meshes → `mmaps/` |
| `contrib/model_reader` | Debug-dumps M2/WMO model geometry to Wavefront `.obj` for inspection |

See [Maps & Pathfinding](Maps-and-Pathfinding.md) for usage and tuning.

### RealmMerge (`contrib/RealmMerge/`)

Standalone utility that **merges two character databases** into one:

- Copies accounts/characters/guilds/mail between schemas.
- On name collisions it renames the incoming character to its guid and sets the rename flag
  (`at_login_flags |= AT_LOGIN_RENAME`), forcing players to pick a new name at next login.
- Run it against two source DBs and one target; always take backups first.

---

## Watchdog Scripts (`src/mangosd/`)

- `run-mangosd` - launches the world server inside `screen` for easy attach/detach.
- `monitor-mangosd` - cron-friendly watchdog: kills the process when it exceeds 95 % CPU
  (stuck-loop guard) and appends the event to a `serverlog` file. Pair with your init system
  to auto-restart.

## Runtime Interfaces

For remote administration options (console, RA on port 3443, SOAP on port 7878) see
[Server Architecture](Server-Architecture.md#remote-interfaces).

---

## Related Pages

- [Database Setup & Migrations](Database-Setup.md)
