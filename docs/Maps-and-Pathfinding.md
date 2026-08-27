# Maps & Pathfinding

How world maps, collision data and creature pathfinding are built and configured.
Tools live in `contrib/`, runtime settings in `mangosd.conf`.

---

## Data Pipeline

| Tool | Input → Output | Used for |
| :--- | :--- | :--- |
| `contrib/extractor` | client MPQs → `maps/` + DBC files | terrain height maps, game tables |
| `contrib/vmap_extractor` + `contrib/vmap_assembler` | MPQs → `vmaps/` | collision geometry (LOS, floors, walls) |
| `contrib/mmap` (Recast-based) | maps+vmaps → `mmaps/` | navigation meshes for pathfinding |

The mmap generator is configured with `contrib/mmap/config.json`: per-map overrides for
voxelisation metrics (`walkableSlopeAngle`, `walkableRadius`, `walkableClimb`,
`maxSimplificationError`, …) and tile-level overrides keyed like `"0307"` for tile (3,7).
`offmesh.txt` adds hand-made jump/shortcut connections; the generator supports
`--silent`, `--bigBaseUnit`, `--maxAngle`, `--skipLiquid`.

---

## Runtime Configuration

From `mangosd.conf`:

- `vmap.*` - enable LOS/collision, indoor checks, height/surface queries.
- `mmap.enabled` - server-side pathfinding using mmaps (default on).
- `DetectPosCollision` - verify final move/summon positions against vmaps.
- `Collision.Models.Unload` - memory vs. speed trade-off.
- `GridUnload` / `GridCleanUpDelay` / `MapUpdateInterval` / `CleanupTerrain` - grid memory
  management.

> Missing or stale `maps/`, `vmaps/`, `mmaps/` cause creatures to walk through walls,
> fall through floors, or pathfind in straight lines. Regenerate all three after client
> changes.

---

## Map Metadata

[`map_template`](world/map_template.md) defines per-map behaviour: type
(continent/dungeon/raid/BG), player limit, reset delay, ghost entrance and script binding
([Instances & Resets](Instances.md)). Weather per zone comes from
[`game_weather`](world/game_weather.md).

---

## Related Pages

- [Server Architecture](Server-Architecture.md)
- [Movement System](Movement-System.md)
