# Transports

Boats and zeppelins between continents are moving game objects
(`src/game/Transports/TransportMgr.cpp`). Their routes come from client data; SQL only tweaks
timing.

---

## How a Transport Is Assembled

1. **Template** - [`gameobject_template`](world/gameobject_template.md) entry with
   `type = 15` (*MO_TRANSPORT* - boats/zeppelins). Its `data0` holds the **taxi path id**.
2. **Route** - `TransportMgr::GenerateWaypoints` reads that path from client
   `TaxiPathNode.dbc` (`sTaxiPathNodesByPath`) and builds a smoothed spline with map-change
   teleport points between continents.
3. **Timing** - stop frames, acceleration and cruise segments are computed automatically from
   path geometry.
4. **Override** - [`transports`](world/transports.md) may correct the result: a non-zero
   `period` replaces the computed round-trip duration (the core comment says it plainly:
   *"load period override from db since our algorithm is not perfect"*). Rows are selected per
   client build.

---

## Passengers

- Players and NPCs board by walking onto the object; their movement updates stream relative to
  the transport while attached (`GenericTransport::AddFollower`…).
- Disembarking happens automatically at stop frames or on logout.
- Being on a transport affects spell/LOs handling - transports count as the passenger's map
  position anchor.

---

## Adding / Fixing a Route

You cannot draw new routes in SQL: they require a taxi path in the client data. In SQL you can:

- point a custom GO template of type 15 (MO_TRANSPORT) at an existing taxi path id,
- adjust the cycle time via [`transports`](world/transports.md).period,
- gate variants per client build (`build` column).

---

## Related Pages

- [Movement System](Movement-System.md)
- [Maps & Pathfinding](Maps-and-Pathfinding.md)
