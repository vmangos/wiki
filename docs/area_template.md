# The area_template table

Contains information about all the areas and zones of the world.

## Structure

### 1. entry - mediumint(8) unsigned, primary key

Unique id of this area.

### 2. map_id - mediumint(8) unsigned

Map id from the `map_template` table.

### 3. zone_id - mediumint(8) unsigned

References an`entry` field from the same table. This is a zone to which this sub area belongs.

### 4. explore_flag - mediumint(8) unsigned

Exploration related flags.

### 5. flags - mediumint(8) unsigned

```
AREA_FLAG_SNOW           = 0x00000001, // snow (only Dun Morogh, Naxxramas, Razorfen Downs and Winterspring)
AREA_FLAG_UNK1           = 0x00000002, // unknown, (only Naxxramas and Razorfen Downs)
AREA_FLAG_UNK2           = 0x00000004, // Only used on development map
AREA_FLAG_SLAVE_CAPITAL  = 0x00000008, // slave capital city flag?
AREA_FLAG_UNK3           = 0x00000010, // unknown
AREA_FLAG_SLAVE_CAPITAL2 = 0x00000020, // slave capital city flag?
AREA_FLAG_DUEL           = 0x00000040, // zones where duels allowed
AREA_FLAG_ARENA          = 0x00000080, // arena, both instanced and world arenas
AREA_FLAG_CAPITAL        = 0x00000100, // main capital city flag
AREA_FLAG_CITY           = 0x00000200, // only for one zone named "City" (where it located?)
```

### 6. area_level - mediumint(8)

Recommended level for the area.

### 7. name - text

Name of the area.

### 8. team - tinyint(3) unsigned

```
2 - Alliance
4 - Horde
```

### 9. liquid_type - tinyint(3) unsigned

Liquid id from LiquidType.dbc.
```
1 - Water
2 - Ocean
3 - Magma
4 - Slime
5 - Naxxramas - Slime
```
