# Data Lifecycle & Cleanup

How character data is created, flagged for deletion and physically purged, plus the admin
commands that drive the process. Sources: `CharacterCommands.cpp` (`character deleted …`,
`character clean …`), `Player.cpp`, `CharDelete.*` config.

---

## Deletion Flow

```
player deletes character
        │  (immediate if below CharDelete.MinLevel)
        ▼
grace period (CharDelete.KeepDays)          [characters.deleted_time]
        │
        ├─ admin: .character deleted restore → back to normal rows
        └─ expiry / .character deleted delete
                   │
                   ▼
   dependent rows purged (inventory, quests, mail, pets, …)
```

Config (`mangosd.conf`):

- `CharDelete.Method` - 0 = remove instantly, 1 = keep for N days.
- `CharDelete.MinLevel` - levels at/below bypass the grace period.
- `CharDelete.KeepDays` - grace window length.

While in the window the row keeps `deleted_account/deleted_name/deleted_time`
([characters](characters/characters.md)) so the name is protected but the slot freed.

---

## Admin Commands

### Deleted characters (`character deleted …`)

| Command | Level | Effect |
| :--- | :--- | :--- |
| `.character deleted list` | GM(3) | list characters in the grace window |
| `.character deleted restore <name> [newName]` | Basic Admin(4) | undelete, optionally renaming |
| `.character deleted delete <name>` | Console only | purge immediately |
| `.character deleted old` | Console only | purge everything past `KeepDays` |

### Bulk cleanup queues (`character clean …`, Admin(6))

Two helper tables feed a controlled mass-purge:

- `.character clean todelete` reads [`characters_guid_delete`](characters/characters_guid_delete.md)
  and deletes those characters properly.
- `.character clean items` reads [`characters_item_delete`](characters/characters_item_delete.md)
  (item template entries) and removes matching item instances from the world.

This is safer than hand-written SQL because the normal dependency cleanup runs for each victim.

---

## Pending-Rename Flags

Operations like name conflicts or `.character rename` set flags in the characters table's
`character_flags` column so players resolve state on next login:

| Flag | Meaning |
| ---: | :--- |
| 0x0100 | CHARACTER_FLAG_RESET_TALENTS_ON_LOGIN - clear talents at next login |
| 0x4000 | CHARACTER_FLAG_RENAME - force rename prompt |
| 0x8000 | CHARACTER_FLAG_RENAME_NEEDS_GM_REVIEW - set after rename for GM review |

(core `CHARACTER_FLAG_*`, `Player.h`.)

## Per-Character Runtime Flags

The `extra_flags` column stores persistent session toggles (`PlayerExtraFlags`,
`AbstractPlayer.h`), mostly GM state:

| Bit | Meaning |
| ---: | :--- |
| 0x0001 | GM mode on |
| 0x0002 | accept tickets |
| 0x0004 | accept whispers |
| 0x0008 | taxi cheat (free/all flights) |
| 0x0010 | GM invisible |
| 0x0020 | GM chat badge |
| 0x0040 | neutral auction houses only |
| 0x0080 | enemy auction houses (overrides 0x40) |
| 0x0100 | PvP death pending corpse creation |
| 0x0200 | whisper restriction |
| 0x0400 | city protector |

---

## Related Pages

- [Characters Database index](Characters-Database.md)
- [Security & RBAC](Security-RBAC.md)
