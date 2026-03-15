# The battleground_template table

Contains definitions for each battleground.

## Structure

### 1. id - mediumint(8) unsigned, unsigned

The unique id of the battleground.
```
1 - Alterac Valley
2 - Warsong Gulch
3 - Arathi Basin
```

### 2. patch - tinyint(3) unsigned, primary key

Content patch in which this exact version of the entry was added. Patch values start from 0 for 1.2.4 and go up to 10 for 1.12.1. The core will load the version of the entry with the highest patch value that is not above the current patch.

### 3. min_players_per_team - smallint(5) unsigned

Minimum amount of players on each faction needed to start a battleground game.

### 4. max_players_per_team- smallint(5) unsigned

Maximum amount of players on each faction.

### 5. min_level - tinyint(3) unsigned

Minimum required level to queue for this battleground.

### 6. min_level - tinyint(3) unsigned

Maximum level above which queuing for this battleground is not allowed.

### 7. alliance_win_spell - smallint(5) unsigned

Spell id from the `spell_template` table that will be cast on Alliance players if they win.

### 8. alliance_lose_spell - smallint(5) unsigned

Spell id from the `spell_template` table that will be cast on Alliance players if they lose.

### 9. horde_win_spell - smallint(5) unsigned

Spell id from the `spell_template` table that will be cast on Horde players if they win.

### 10. horde_lose_spell - smallint(5) unsigned

Spell id from the `spell_template` table that will be cast on Horde players if they lose.

### 11. alliance_start_location - mediumint(8) unsigned

Id from WorldSafeLocs.dbc that defines where Alliance players spawn when joining the battleground.

### 12. horde_start_location - mediumint(8) unsigned

Id from WorldSafeLocs.dbc that defines where Horde players spawn when joining the battleground.