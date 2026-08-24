# Tutorial: Adding a Custom Quest

A kill-and-collect quest for the NPC from [Adding a Custom NPC](Tutorial-Custom-NPC.md):
bring 5 *Crier Tokens* (item 900001) and earn gold + an item reward.

---

## 1. Quest Template

```sql
INSERT INTO quest_template
(entry, Method, MinLevel, QuestLevel, RequiredRaces, Title, Details,
 Objectives, EndText, ReqItemCount1, ReqItemId1, RewOrReqMoney, RewXP,
 RewItemId1, RewItemCount1)
VALUES
(90002, 2, 10, 15, 1 /*human only*/, 'Tokens of Gratitude',
 'The crier asked me to gather his tokens back from the ruffians in Elwynn.',
 'Bring 5 Crier Tokens to the Stormwind Town Crier.', 'You found them all!',
 5, 900001, 1500, 3, 900002, 1);
```

Key groups explained: [Quest System](Quest-System.md). Column list:
[`quest_template`](world/quest_template.md).

## 2. Give & Take

```sql
-- offered by our NPC (creature_questrelation = giver)
INSERT INTO creature_questrelation (id, quest) VALUES (90001, 90002);

-- turned in to the same NPC
INSERT INTO creature_involvedrelation (id, quest) VALUES (90001, 90002);
```

## 3. The Objective Item

```sql
INSERT INTO item_template (entry, class, name, display_id, Quality, Flags,
                           Bonding, BuyPrice, SellPrice, InventoryType, stackable)
VALUES (900001, 12 /*quest item*/, 'Crier Token', 6440, 1, 32768, 1, 25, 6, 0, 5);
```

Quest items use class `12`; adding flag `0x8000` (NO_DISENCHANT) prevents players
 disenchanting them; class 12 alone is what makes them quest items.

## 4. Reward Item (optional)

Insert item `900002` similarly with a real quality/class - or reuse any existing entry.

## 5. Chain It (optional)

```sql
UPDATE quest_template SET NextQuestId = 90003 WHERE entry = 90002;
```

Flow-control fields (`PrevQuestId`, `ExclusiveGroup`, `NextQuestInChain`…) are documented in
the [Quest System](Quest-System.md) overview.

## 6. Localization (optional)

Fill `Title_locN`, `Details_locN`, … in [`locales_quest`](world/locales_quest.md) -
see [Localization](Localization.md).

## 7. Verify

```
.reload quest_template
.quest add 90002      -- self-test as GM
.additem 900001 5     -- simulate objective progress
```

Common load errors logged at startup: missing `ReqItemId`, wrong race/class masks, or a quest
attached to a creature that does not exist.
