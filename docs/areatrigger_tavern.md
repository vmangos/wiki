# The areatrigger_tavern table

This table defines which areatriggers are [Inns](https://wowwiki.fandom.com/wiki/Inn). You accumulate rested XP faster there and can log out instantly.

## Structure

### 1. id - mediumint(8) unsigned, primary key

Areatrigger id from the `areatrigger_template` table.

### 2. name - text

The name of the Inn. This field is not used by the core.

### 3. patch_min - tinyint(3) unsigned

The patch in which the Inn was introduced. Patch values start from 0 for 1.2.4 and go up to 10 for 1.12.1.


