# Logs Database

The **logs** database is an optional audit/statistics sink: chat logs, trade records, anticheat detections, warden results and instance statistics. Keeping it separate lets heavy logging run without touching gameplay databases.

## Tables

- [`instance_creature_kills`](logs/instance_creature_kills.md) - Statistics log of creature kills inside instanced encounters.
- [`instance_custom_counters`](logs/instance_custom_counters.md) - Generic counters instance scripts increment during progression (used for statistics).
- [`instance_wipes`](logs/instance_wipes.md) - Logged wipes on boss encounters (duration, attempts).
- [`logs_battleground`](logs/logs_battleground.md) - Battleground lifecycle log entries (creation, finish).
- [`logs_player`](logs/logs_player.md) - Per-player audit log of notable events written when player logging is enabled.
- [`logs_trade`](logs/logs_trade.md) - Money flow log entries above the configured threshold (loot, quest rewards, trades, mail, GM changes).
- [`logs_transactions`](logs/logs_transactions.md) - Money/mail transaction audit trail.
- [`migrations`](logs/migrations.md) - Applied migration IDs for the logs database.
- [`smartlog_creature`](logs/smartlog_creature.md) - 'Smart log' rows for notable creature AI events such as boss deaths with combat time.
- [`system_fingerprint_usage`](logs/system_fingerprint_usage.md) - Records system fingerprint usage during logon for anti-cheat detection.
