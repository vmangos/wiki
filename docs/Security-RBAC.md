# Security & RBAC

How account security levels and the role-based access control (RBAC) layer govern who may run
which command. Sources: `src/game/AccountMgr.cpp`, `src/game/Chat/Chat.cpp`,
`src/realmd` for account checks.

---

## Security Levels

Every account has a GM level per realm in [`account_access`](realmd/account_access.md)
(`gmlevel`, `RealmID = -1` applies to all realms). Levels are defined in
`src/shared/Common.h`:

| Level | Name | Typical use |
| :---: | :--- | :--- |
| 0 | Player | normal gameplay commands |
| 1 | Moderator | ticket handling, basic lookup/teleport |
| 2 | Ticket Master | ticket system only |
| 3 | Game Master | spawn/npc/item manipulation |
| 4 | Basic Admin | reload, server control |
| 5 | Developer | advanced debugging, data overrides |
| 6 | Administrator | everything except console-only |
| 7 | Console | server console only |

The full command list with required levels is in the [GM Commands Reference](GM-Commands.md).

---

## RBAC Tables

On top of static levels, commands can be bound to **permissions**:

| Table | Purpose |
| :--- | :--- |
| [`rbac_permissions`](realmd/rbac_permissions.md) | Defines permission ids (name + id). |
| [`rbac_account_permissions`](realmd/rbac_account_permissions.md) | Grants (`granted = 1`) or revokes (`granted = 0`) a permission for an account. |
| [`rbac_command_permissions`](realmd/rbac_command_permissions.md) | Binds a command string to the permission id required to run it. |

Resolution order for a command:

1. If [`rbac_command_permissions`](realmd/rbac_command_permissions.md) contains the command → check the bound permission against
   the account's granted permissions.
2. Otherwise fall back to the classic `SEC_*` level comparison from the command table.

This lets operators grant individual commands without raising the whole account's level - e.g.
allow a moderator to use `.tele` explicitly.

---

## Account Bans & Client Whitelist

| Table | Purpose |
| :--- | :--- |
| [`account_banned`](realmd/account_banned.md) | Per-account bans with reason/expiry. |
| [`ip_banned`](realmd/ip_banned.md) | IP/network bans. |
| [`allowed_clients`](realmd/allowed_clients.md) | Exact client build/platform whitelist; empty = allow all supported builds. |

---

## Related Pages

- [account_access](realmd/account_access.md)
- [GM Commands Reference](GM-Commands.md)
