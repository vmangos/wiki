# The cinematic_waypoints table

Contains the camera position at specific intervals during the intro cinematics. This information is used in order to load nearby creatures and objects even if there are no actual players in the area.

## Structure

### 1. cinematic - int(11) unsigned

Cinematic id from CinematicSequences.dbc.

### 2. timer - int(11) unsigned

Time in milliseconds.

### 3. position_x - float

Global map coordinate.

### 4. position_y - float

Global map coordinate.

### 5. position_z - float

Global map coordinate.

### 6. comment - varchar(255)

A description of this point. This field is not used by the core.
