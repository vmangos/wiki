# The battleground_events table

Defines battleground events that spawn creatures and gameobjects.

## Structure

### 1. map - smallint(5) unsigned, primary key

Map id from the `map_template` table. 
```
30 - Alterac Valley
489 - Warsong Gulch
529 - Arathi Basin
```

### 2. event1 - tinyint(3) unsigned, primary key

Main event id.

### 3. event2 - tinyint(3) unsigned, primary key

Sub event id.

### 4. description - varchar(255)

The name of the event. This field is not used by the core.

