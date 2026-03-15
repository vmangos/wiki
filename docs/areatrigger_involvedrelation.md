# The areatrigger_involvedrelation table

Used to associate areatriggers with the completion of a quest.

## Structure

### 1. id - mediumint(8) unsigned, primary key

Areatrigger id from the `areatrigger_template` table.

### 2. quest - mediumint(8) unsigned

Quest id from the `quest_template` table. This quest will get completed once players reach the trigger. It should have  QUEST_SPECIAL_FLAG_EXPLORATION_OR_EVENT (2) in `SpecialFlags`.

