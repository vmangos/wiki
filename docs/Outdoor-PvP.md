# Outdoor PvP

World PvP objectives implemented as C++ systems in `src/game/OutdoorPvP/`:
**Silithus (SI)** and **Eastern Plaguelands (EP)**. Both are enabled by default and toggled in
`mangosd.conf`:

- `OutdoorPvP.SI.Enable` (`World.cpp:806`)
- `OutdoorPvP.EP.Enable`

---

## Silithus - Silithyst (SI)

Both factions fight over **Silithyst** clouds: carrying the geyser extract to a side's
collection point fills that faction's resource bar.

Key constants (`OutdoorPvPSI.h`):

| Constant | Value | Meaning |
| :--- | :---: | :--- |
| `SI_MAX_RESOURCES_DEFAULT` | 200 | resources needed to win the zone |
| `SI_AREATRIGGER_H` | 4168 | collection areatrigger |
| Silithyst spells | 29518/29519/29534 | flag aura / carry spell / trace buff |
| Cenarion Favor | 30754 | zone-wide reward buff on victory |

While carrying Silithyst the player is flagged and slowed; death drops the extract.

---

## Eastern Plaguelands - Echoes of Lordaeron (EP)

Tower-capture tug of war. Capturing the zone's four towers (Eastwall, Northpass, Plaguewood,
Crown Guard) shifts control toward a faction; each owned tower applies a stronger *Echoes of
Lordaeron* buff tier. Capturing Crown Guard Tower also links the contested graveyard to the
controlling faction.

Key constants (`OutdoorPvPEP.h`):

| Constant | Value | Meaning |
| :--- | :---: | :--- |
| `EP_Zone` | 139 | Eastern Plaguelands |
| `EP_GraveYardId` | 927 | contested graveyard |
| `EP_BuffZones` | 139, 2017, 2057 | zones receiving the victory buff |
| `EP_AllianceBuffs/HordeBuffs` | rank 1-4 | *Echoes of Lordaeron* tiers per number of towers controlled |

Capturing Eastwall Tower summons five spectral Lordaeron soldiers (`EP_SummonsNum`).

---

## Implementation Notes

- Systems register through `Register.cpp`; each zone runs its own update handler.
- Victory buffs persist until the next flip.
- These systems are pure C++, with no world-table configuration beyond the enable flags.

---

## Related Pages

- [Battlegrounds](Battlegrounds.md)
- [Honor & PvP](Honor-PvP.md)
