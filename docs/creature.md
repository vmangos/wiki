# The creature table

Contains creature spawn data.

## Structure

### 1. guid - int(10) unsigned, primary key

An unique id for the spawn.

### 2-5. id - mediumint(8) unsigned

Creature id from the `creature_template` table. A spawn can have up to 4 different creature ids.

### 6. map - smallint(5) unsigned

Map id from the `map_template` table (Map.dbc in client).

### 7. display_id - mediumint(8) unsigned

Creature display id from CreatureDisplayInfo.dbc in client. This value overrides the display id from the `creature_template` if its set.

### 8. equipment_id - mediumint(8) unsigned

Creature equipment id from the `creature_equip_template` table. This value overrides the equipment id from the `creature_template` if its set.

### 9. position_x - float

Global map coordinates for the spawn.

### 10. position_y - float

Global map coordinates for the spawn.

### 11. position_z - float

Global map coordinates for the spawn.

### 12. orientation - float

Orientation value for the spawn.

### 13. spawntimesecsmin - int(10) unsigned

Minimum respawn delay in seconds after the creature is killed.

### 14. spawntimesecsmax - int(10) unsigned

Maximum respawn delay in seconds after the creature is killed.

### 15. wander_distance - float

Maximum wandering radius to be used by the random movement generator if `movement_type` is set to 1.

### 16. health_percent - float

Starting health percentage. Used for quests that require the player to heal a creature.

### 17. mana_percent - float

Starting mana percentage.

### 18. movement_type - tinyint(3) unsigned

Default movement type used for this spawn.
```
0 - Idle
1 - Random Movement
2 - Waypoints
```

### 19. spawn_flags - int(10) unsigned

```
1 - Active Object (AI is updated even if no players are around)
2 - Disabled
4 - Random Respawn Time (spawn time will vary by ±10%)
8 - Dynamic Respawn Time (only if population above 2500)
16 - Force Dynamic Respawn For Elite
32 - Evade Out Of Home Area (only used by ScriptedAI)
64 - Not Visible (can be made visible by spell effect 46)
128 - Dead (used by quests that require player to revive npc)
```

### 20. visibility_mod - float

Maximum visibility distance in yards. This allows you to override the default visibility distance, but you must also make the creature an active object.

### 21. patch_min - tinyint(3) unsigned

Minimum content patch to load this entry. Patch values go from 0 for 1.2 to 10 for 1.12.

### 22. patch_max - tinyint(3) unsigned

Maximum content patch to load this entry. Patch values go from 0 for 1.2 to 10 for 1.12.

