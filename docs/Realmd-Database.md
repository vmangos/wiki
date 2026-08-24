# Realmd (Logon) Database

The **realmd** (login/auth) database stores accounts, bans, GM access levels and the realm list. The `realmd` process authenticates clients here before handing them to a world server.

Created from [`sql/logon.sql`](https://github.com/vmangos/core/blob/development/sql/logon.sql); configured via `LoginDatabase.Info` in `mangosd.conf` and by `realmd.conf`.

## Tables

- [`account`](realmd/account.md) - Account credentials and per-account settings (username, password hash/verifier, expansion, locale).
- [`account_access`](realmd/account_access.md) - GM level and realm assignment per account (console/GM permissions).
- [`account_banned`](realmd/account_banned.md) - Account ban records with reason and expiration.
- [`allowed_clients`](realmd/allowed_clients.md) - Whitelist of exact client builds/platforms permitted to log on through realmd.
- [`geoip`](realmd/geoip.md) - IP range to country mapping cache used by the login server.
- [`ip2nation`](realmd/ip2nation.md) - Mapping of IP ranges to country codes for GeoIP lookups.
- [`ip2nationcountries`](realmd/ip2nationcountries.md) - Country metadata for [`ip2nation`](realmd/ip2nation.md).
- [`ip_banned`](realmd/ip_banned.md) - Banned IP addresses/networks.
- [`migrations`](realmd/migrations.md) - Applied migration IDs for the realmd database.
- [`rbac_account_permissions`](realmd/rbac_account_permissions.md) - Grants or revokes RBAC permissions per account.
- [`rbac_command_permissions`](realmd/rbac_command_permissions.md) - Binds chat/console commands to the RBAC permission required to execute them.
- [`rbac_permissions`](realmd/rbac_permissions.md) - Definitions of RBAC permissions referenced by account grants and command bindings.
- [`realmcharacters`](realmd/realmcharacters.md) - How many characters each account has per realm (enforces character-per-realm limit).
- [`realmlist`](realmd/realmlist.md) - Registered realms served by this auth server (name, address, type, security level).
- [`uptime`](realmd/uptime.md) - Uptime history of the realm(s): start time, player peak, revision.
