# The areatrigger_teleport table

Defines where areatriggers like dungeon portals teleport players, and the conditions to use them.

## Structure

### 1. id - mediumint(8) unsigned, primary key

Areatrigger id from the `areatrigger_template` table.

### 2. patch - tinyint(3) unsigned, primary key

Content patch in which this exact version of the entry was added. Patch values start from 0 for 1.2.4 and go up to 10 for 1.12.1. The core will load the version of the entry with the highest patch value that is not above the current patch.

### 3. name - varchar(64)

The name of the location that this triggers teleports players to. This field is not used by the core.

### 4. message - varchar(128)

Message sent to the client when the criteria to use the trigger is not met. This text is contained in Areatrigger.db2 in the new Classic client.

### 5. required_level - tinyint(3) unsigned

Minimum level required to use the trigger.

### 6. required_condition - mediumint(8) unsigned

Id from the `conditions` table. This condition must be met to use the trigger.

### 7. target_map - smallint(5) unsigned

Map id from the `map_template` table where players will get teleported. This value is contained in WorldSafeLocs.db2 in the new Classic client.

### 8. target_position_x - float

Global map coordinate of the location where players will get teleported. This value is contained in WorldSafeLocs.db2 in the new Classic client.

### 9. target_position_y - float

Global map coordinate of the location where players will get teleported. This value is contained in WorldSafeLocs.db2 in the new Classic client.

### 10. target_position_z - float

Global map coordinate of the location where players will get teleported. This value is contained in WorldSafeLocs.db2 in the new Classic client.

### 11. target_orientation - float

The orientation that players will have once they get teleported. This value is contained in WorldSafeLocs.db2 in the new Classic client.

