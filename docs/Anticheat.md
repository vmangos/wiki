# Anticheat

VMaNGOS ships two independent anti-cheat systems: a **movement anticheat** that validates
movement packets server-side, and an implementation of the vanilla **Warden** anti-cheat client module.
Sources: `src/game/Anticheat/`.

---

## Movement Anticheat

`MovementAnticheat/MovementAnticheat.cpp` inspects every movement packet
(`HandlePositionTests`, `HandleFlagTests`) and runs a battery of checks:

| Check | Method | Catches |
| :--- | :--- | :--- |
| Speed hack | `CheckSpeedHack` | movement faster than allowed per move type |
| Teleport hacks | `CheckTeleport`, `IsTeleportAllowed3D` | position jumps without teleport packets |
| Wall climbing | `CheckWallClimb` | Z-gain while touching geometry |
| Falling abuse | `CheckNoFallTime`, `CheckFallReset/Stop` | fly-hack signatures (no fall time) |
| Fake transports | `CheckFakeTransport`, `CheckTeleportToTransport` | bogus transport positions |
| Forbidden areas | `CheckForbiddenArea` | entering out-of-bounds maps |
| Time desync | `CheckTimeDesync` | packet timestamp manipulation |

### Reactions & Logging

- Actions per detection level (log, notify, kick, ban) are controlled by the
  `Anticheat.*` settings - 125 of them, documented in the
  `mangosd.conf`.
- Detections are written to the unified [`logs_player`](logs/logs_player.md) table
  (`type = 'Anticheat'`).
- Suspected bot characters can be flagged into
  [`logs_trashcharacters`](logs/logs_trashcharacters.md).

---

## Warden

The Warden system (`WardenAnticheat/`) implements the client-side anti-cheat challenge protocol
for Windows (`WardenWin.cpp`) and macOS (`WardenMac.cpp`):

- Modules are binary payloads loaded from disk: point `Warden.ModuleDir` (default `warden_modules/`) at a folder containing the Windows/macOS modules; missing files log *"No ... Warden module found - reduced cheat detection capabilities!"*.
- Module contents are decrypted with `WardenModuleMgr`;
  scan definitions come from the [`warden_scans`](world/warden_scans.md) world table.
- The server schedules scans via `Warden.NumScans`, `Warden.ScanFrequency`,
  `Warden.ClientResponseDelay` etc. (`mangosd.conf`).
- Scan outcomes are written to [`logs_player`](logs/logs_player.md)
  (`type = 'Anticheat'`).
- Enable/disable per platform with `Warden.WinEnabled` / `Warden.OSXEnabled`.

> Warden only works with clients whose Warden module matches what the server expects; it is
> primarily useful against known cheat tooling.

---

## Related Pages

- `mangosd.conf` - `Anticheat.*`, `Warden.*` categories
- [Player Bots](Player-Bots.md) - the legitimate "bots" the core ships for testing/population
