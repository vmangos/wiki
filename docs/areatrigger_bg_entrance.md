# The areatrigger_bg_entrance table

Contains definitions of battleground entrance portals that players can use to join the queue.

## Structure

### 1. id - mediumint(8) unsigned, primary key

Areatrigger id from the `areatrigger_template` table.

### 2. name - text

Name of the battleground. This field is just for clarity, it is not used by the core.

### 3. team - mediumint(8) unsigned

Player team faction that can use this entrance.
```
67 - Horde
469 - Alliance
```

### 4. bg_template - mediumint(8) unsigned

Battleground id from the `battleground_template` table.
```
1 - Alterac Valley
2 - Warsong Gulch
3 - Arathi Basin
```

### 5. exit_map - smallint(5) unsigned

Map id from the `map_template` table. This is where players will get teleported once they leave the battleground.

### 6. exit_position_x - float

Global map coordinate of the location that players get teleported to once they leave the battleground.

### 7. exit_position_y - float

Global map coordinate of the location that players get teleported to once they leave the battleground.

### 8. exit_position_z - float

Global map coordinate of the location that players get teleported to once they leave the battleground.

### 9. exit_position_o - float

The orientation that players will have once they leave the battleground.



