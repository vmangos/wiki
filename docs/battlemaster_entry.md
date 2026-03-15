# The battlemaster_entry table

Defines which creatures are [battlemasters](https://wowwiki.fandom.com/wiki/Battlemaster).

## Structure

### 1. entry - mediumint(8) unsigned, primary key

Creature id from the `creature_template` table.

### 2. bg_template - mediumint(8) unsigned

Battleground id from the `battleground_template` table.
```
1 - Alterac Valley
2 - Warsong Gulch
3 - Arathi Basin
```
