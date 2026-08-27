# Server Architecture

How a VMaNGOS server is put together: processes, databases and the flow of a client login.

```
WoW client (1.12.x)
   │  auth (port 3724)
   ▼
realmd ────────────────► realmd database
   │  realm list, account check
   │  world (port from WorldServerPort, default 8085)
   ▼
mangosd ──┬────────────► mangos (world) database
          ├────────────► characters database
          ├────────────► realmd database (account updates)
          └────────────► logs database (optional audit sink)
```

---

## Processes

| Binary | Source | Role |
| :--- | :--- | :--- |
| `realmd` | `src/realmd` | Authentication server. Handles logon challenges, account bans, realm list ([`realmlist`](realmd/realmlist.md) table). Configured by `realmd.conf`. |
| `mangosd` | `src/mangosd` | World server. Simulates maps, units, spells, battlegrounds; runs DB-backed scripts and AI. Configured by `mangosd.conf`, optionally exposes a console / RA / SOAP interface. |

Both read their database credentials from their config files - see the
`mangosd.conf`.

## Databases

| Database | Contents |
| :--- | :--- |
| **realmd** | Accounts, bans, GM access, realms |
| **mangos** (world) | All static game content |
| **characters** | Player state |
| **logs** | Audit/statistics sinks |

The world database **is** shipped as one complete dump; after importing it you either apply the
migration files from `sql/migrations` on top, or download a full database release with all
migrations already applied (see [Database Setup](Database-Setup.md)).

## Threading Model (mangosd)

- **Map update threads** - `MapUpdate.Threads`; each thread advances the maps assigned to it.
- **Network threads** - `Network.Threads`, plus separate packet-broadcast workers.
- **Database worker/async connections** - per-database `.Connections` (sync SELECT pool),
  `.WorkerThreads` (background writes).
- The main thread ticks the world at `MapUpdateInterval` ms.

Tuning knobs for all of these are documented in the `mangosd.conf`.

## Remote Interfaces

| Interface | Config | Default port | Notes |
| :--- | :--- | :---: | :--- |
| Console | `Console.Enable` | stdin | local CLI; runs same command set |
| Remote Access (RA) | `Ra.Enable`, `Ra.IP`, `Ra.Port` | 3443 | telnet-style socket; `Ra.MinAccountLevel` gate, `Ra.Restricted` limits to localhost-listed IPs when enabled |
| SOAP | `SOAP.Enabled`, `SOAP.IP`, `SOAP.Port` | 7878 | HTTP endpoint for scripted command execution |

All three expose the commands documented in the [GM Commands Reference](GM-Commands.md);
console-only commands are marked there. Example SOAP call against the default bind:

```bash
curl --header "Content-Type: text/xml; charset=utf-8" \
     --header 'SOAPAction: "urn:MangosServer"' \
     --data @- http://127.0.0.1:7878/ <<'XML'
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
 <soap:Body><m:executeCommand xmlns:m="urn:MANGOS">
   <m:command>server info</m:command>
 </m:executeCommand></soap:Body>
</soap:Envelope>
XML
```

> RA and SOAP authenticate against realmd accounts; use an account whose
> [`account_access`](realmd/account_access.md) level satisfies the target commands.

---

## Related Pages

- [Compiling on Linux](Compiling-on-Linux.md) / [Compiling on Windows](Compiling-on-Windows.md)
- [Getting it Working (Linux)](Getting-it-working-Linux.md) / [(Windows)](Getting-it-working-Windows.md)
- [Database Setup](Database-Setup.md)
