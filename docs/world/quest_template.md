# quest_template Table

Defines all quest data: objectives, rewards, requirements, text, and emote sequences.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`patch`](#f-patch) | tinyint(3) unsigned | PRI | NO | 0 |  |
| [`Method`](#f-Method) | tinyint(3) unsigned |  | NO | 2 |  |
| [`ZoneOrSort`](#f-ZoneOrSort) | smallint(6) |  | NO | 0 |  |
| [`MinLevel`](#f-MinLevel) | tinyint(3) unsigned |  | NO | 0 |  |
| [`MaxLevel`](#f-MaxLevel) | tinyint(3) unsigned |  | NO | 0 |  |
| [`QuestLevel`](#f-QuestLevel) | tinyint(3) unsigned |  | NO | 0 |  |
| [`Type`](#f-Type) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredClasses`](#f-RequiredClasses) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredRaces`](#f-RequiredRaces) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredSkill`](#f-RequiredSkill) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredSkillValue`](#f-RequiredSkillValue) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredCondition`](#f-RequiredCondition) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RepObjectiveFaction`](#f-RepObjectiveFaction) | smallint(5) unsigned |  | NO | 0 |  |
| [`RepObjectiveValue`](#f-RepObjectiveValue) | mediumint(9) |  | NO | 0 |  |
| [`RequiredMinRepFaction`](#f-RequiredMinRepFaction) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredMinRepValue`](#f-RequiredMinRepValue) | mediumint(9) |  | NO | 0 |  |
| [`RequiredMaxRepFaction`](#f-RequiredMaxRepFaction) | smallint(5) unsigned |  | NO | 0 |  |
| [`RequiredMaxRepValue`](#f-RequiredMaxRepValue) | mediumint(9) |  | NO | 0 |  |
| [`SuggestedPlayers`](#f-SuggestedPlayers) | tinyint(3) unsigned |  | NO | 0 |  |
| [`LimitTime`](#f-LimitTime) | int(10) unsigned |  | NO | 0 |  |
| [`QuestFlags`](#f-QuestFlags) | smallint(5) unsigned |  | NO | 0 |  |
| [`SpecialFlags`](#f-SpecialFlags) | tinyint(3) unsigned |  | NO | 0 |  |
| [`PrevQuestId`](#f-PrevQuestId) | mediumint(9) |  | NO | 0 |  |
| [`NextQuestId`](#f-NextQuestId) | mediumint(9) |  | NO | 0 |  |
| [`ExclusiveGroup`](#f-ExclusiveGroup) | mediumint(9) |  | NO | 0 |  |
| [`BreadcrumbForQuestId`](#f-BreadcrumbForQuestId) | mediumint(9) unsigned |  | NO | 0 |  |
| [`NextQuestInChain`](#f-NextQuestInChain) | mediumint(8) unsigned |  | NO | 0 |  |
| [`SrcItemId`](#f-SrcItemId) | mediumint(8) unsigned |  | NO | 0 |  |
| [`SrcItemCount`](#f-SrcItemCount) | tinyint(3) unsigned |  | NO | 0 |  |
| [`SrcSpell`](#f-SrcSpell) | smallint(5) unsigned |  | NO | 0 |  |
| [`Title`](#f-Title) | text |  | YES |  |  |
| [`Details`](#f-Details) | text |  | YES |  |  |
| [`Objectives`](#f-Objectives) | text |  | YES |  |  |
| [`OfferRewardText`](#f-OfferRewardText) | text |  | YES |  |  |
| [`RequestItemsText`](#f-RequestItemsText) | text |  | YES |  |  |
| [`EndText`](#f-EndText) | text |  | YES |  |  |
| [`ObjectiveText1`](#f-ObjectiveText1) | text |  | YES |  |  |
| [`ObjectiveText2`](#f-ObjectiveText2) | text |  | YES |  |  |
| [`ObjectiveText3`](#f-ObjectiveText3) | text |  | YES |  |  |
| [`ObjectiveText4`](#f-ObjectiveText4) | text |  | YES |  |  |
| [`ReqItemId1`](#f-ReqItemId1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqItemId2`](#f-ReqItemId2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqItemId3`](#f-ReqItemId3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqItemId4`](#f-ReqItemId4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqItemCount1`](#f-ReqItemCount1) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqItemCount2`](#f-ReqItemCount2) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqItemCount3`](#f-ReqItemCount3) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqItemCount4`](#f-ReqItemCount4) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqSourceId1`](#f-ReqSourceId1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceId2`](#f-ReqSourceId2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceId3`](#f-ReqSourceId3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceId4`](#f-ReqSourceId4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceCount1`](#f-ReqSourceCount1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceCount2`](#f-ReqSourceCount2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceCount3`](#f-ReqSourceCount3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqSourceCount4`](#f-ReqSourceCount4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`ReqCreatureOrGOId1`](#f-ReqCreatureOrGOId1) | mediumint(9) |  | NO | 0 |  |
| [`ReqCreatureOrGOId2`](#f-ReqCreatureOrGOId2) | mediumint(9) |  | NO | 0 |  |
| [`ReqCreatureOrGOId3`](#f-ReqCreatureOrGOId3) | mediumint(9) |  | NO | 0 |  |
| [`ReqCreatureOrGOId4`](#f-ReqCreatureOrGOId4) | mediumint(9) |  | NO | 0 |  |
| [`ReqCreatureOrGOCount1`](#f-ReqCreatureOrGOCount1) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqCreatureOrGOCount2`](#f-ReqCreatureOrGOCount2) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqCreatureOrGOCount3`](#f-ReqCreatureOrGOCount3) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqCreatureOrGOCount4`](#f-ReqCreatureOrGOCount4) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqSpellCast1`](#f-ReqSpellCast1) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqSpellCast2`](#f-ReqSpellCast2) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqSpellCast3`](#f-ReqSpellCast3) | smallint(5) unsigned |  | NO | 0 |  |
| [`ReqSpellCast4`](#f-ReqSpellCast4) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewChoiceItemId1`](#f-RewChoiceItemId1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewChoiceItemId2`](#f-RewChoiceItemId2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewChoiceItemId3`](#f-RewChoiceItemId3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewChoiceItemId4`](#f-RewChoiceItemId4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewChoiceItemId5`](#f-RewChoiceItemId5) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewChoiceItemId6`](#f-RewChoiceItemId6) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewChoiceItemCount1`](#f-RewChoiceItemCount1) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewChoiceItemCount2`](#f-RewChoiceItemCount2) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewChoiceItemCount3`](#f-RewChoiceItemCount3) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewChoiceItemCount4`](#f-RewChoiceItemCount4) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewChoiceItemCount5`](#f-RewChoiceItemCount5) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewChoiceItemCount6`](#f-RewChoiceItemCount6) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewItemId1`](#f-RewItemId1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewItemId2`](#f-RewItemId2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewItemId3`](#f-RewItemId3) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewItemId4`](#f-RewItemId4) | mediumint(8) unsigned |  | NO | 0 |  |
| [`RewItemCount1`](#f-RewItemCount1) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewItemCount2`](#f-RewItemCount2) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewItemCount3`](#f-RewItemCount3) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewItemCount4`](#f-RewItemCount4) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewRepFaction1`](#f-RewRepFaction1) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewRepFaction2`](#f-RewRepFaction2) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewRepFaction3`](#f-RewRepFaction3) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewRepFaction4`](#f-RewRepFaction4) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewRepFaction5`](#f-RewRepFaction5) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewRepValue1`](#f-RewRepValue1) | mediumint(9) |  | NO | 0 |  |
| [`RewRepValue2`](#f-RewRepValue2) | mediumint(9) |  | NO | 0 |  |
| [`RewRepValue3`](#f-RewRepValue3) | mediumint(9) |  | NO | 0 |  |
| [`RewRepValue4`](#f-RewRepValue4) | mediumint(9) |  | NO | 0 |  |
| [`RewRepValue5`](#f-RewRepValue5) | mediumint(9) |  | NO | 0 |  |
| [`RewRepSpilloverMask`](#f-RewRepSpilloverMask) | tinyint(3) unsigned |  | NO | 0 |  |
| [`RewXP`](#f-RewXP) | mediumint(9) unsigned |  | NO | 0 |  |
| [`RewOrReqMoney`](#f-RewOrReqMoney) | int(11) |  | NO | 0 |  |
| [`RewMoneyMaxLevel`](#f-RewMoneyMaxLevel) | int(10) unsigned |  | NO | 0 |  |
| [`RewSpell`](#f-RewSpell) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewSpellCast`](#f-RewSpellCast) | smallint(5) unsigned |  | NO | 0 |  |
| [`RewMailTemplateId`](#f-RewMailTemplateId) | mediumint(8) |  | NO | 0 |  |
| [`RewMailDelaySecs`](#f-RewMailDelaySecs) | int(11) unsigned |  | NO | 0 |  |
| [`RewMailMoney`](#f-RewMailMoney) | int(10) unsigned |  | NO | 0 |  |
| [`PointMapId`](#f-PointMapId) | smallint(5) unsigned |  | NO | 0 |  |
| [`PointX`](#f-PointX) | float |  | NO | 0 |  |
| [`PointY`](#f-PointY) | float |  | NO | 0 |  |
| [`PointOpt`](#f-PointOpt) | mediumint(8) unsigned |  | NO | 0 |  |
| [`DetailsEmote1`](#f-DetailsEmote1) | smallint(5) unsigned |  | NO | 0 |  |
| [`DetailsEmote2`](#f-DetailsEmote2) | smallint(5) unsigned |  | NO | 0 |  |
| [`DetailsEmote3`](#f-DetailsEmote3) | smallint(5) unsigned |  | NO | 0 |  |
| [`DetailsEmote4`](#f-DetailsEmote4) | smallint(5) unsigned |  | NO | 0 |  |
| [`DetailsEmoteDelay1`](#f-DetailsEmoteDelay1) | int(11) unsigned |  | NO | 0 |  |
| [`DetailsEmoteDelay2`](#f-DetailsEmoteDelay2) | int(11) unsigned |  | NO | 0 |  |
| [`DetailsEmoteDelay3`](#f-DetailsEmoteDelay3) | int(11) unsigned |  | NO | 0 |  |
| [`DetailsEmoteDelay4`](#f-DetailsEmoteDelay4) | int(11) unsigned |  | NO | 0 |  |
| [`IncompleteEmote`](#f-IncompleteEmote) | smallint(5) unsigned |  | NO | 0 |  |
| [`CompleteEmote`](#f-CompleteEmote) | smallint(5) unsigned |  | NO | 0 |  |
| [`OfferRewardEmote1`](#f-OfferRewardEmote1) | smallint(5) unsigned |  | NO | 0 |  |
| [`OfferRewardEmote2`](#f-OfferRewardEmote2) | smallint(5) unsigned |  | NO | 0 |  |
| [`OfferRewardEmote3`](#f-OfferRewardEmote3) | smallint(5) unsigned |  | NO | 0 |  |
| [`OfferRewardEmote4`](#f-OfferRewardEmote4) | smallint(5) unsigned |  | NO | 0 |  |
| [`OfferRewardEmoteDelay1`](#f-OfferRewardEmoteDelay1) | int(11) unsigned |  | NO | 0 |  |
| [`OfferRewardEmoteDelay2`](#f-OfferRewardEmoteDelay2) | int(11) unsigned |  | NO | 0 |  |
| [`OfferRewardEmoteDelay3`](#f-OfferRewardEmoteDelay3) | int(11) unsigned |  | NO | 0 |  |
| [`OfferRewardEmoteDelay4`](#f-OfferRewardEmoteDelay4) | int(11) unsigned |  | NO | 0 |  |
| [`StartScript`](#f-StartScript) | mediumint(8) unsigned |  | NO | 0 |  |
| [`CompleteScript`](#f-CompleteScript) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Unique quest ID.
- <a id="f-patch"></a>**`patch`** - Primary Key. Client patch version.
- <a id="f-Method"></a>**`Method`** - Quest method: `0` auto-complete, `1` disabled, `2` deliver (normal).
- <a id="f-ZoneOrSort"></a>**`ZoneOrSort`** - Zone ID or sort index (negative for sorting).
- <a id="f-MaxLevel"></a><a id="f-MinLevel"></a>**`MinLevel` / `MaxLevel`** - Level requirements.
- <a id="f-QuestLevel"></a>**`QuestLevel`** - Quest difficulty level.
- <a id="f-Type"></a>**`Type`** - Quest type (`QuestInfo.dbc`): `0` normal, `1` elite, `41` PvP, `62` raid, `81` dungeon.
- <a id="f-RequiredClasses"></a><a id="f-RequiredRaces"></a>**`RequiredClasses` / `RequiredRaces`** - Class/race masks.
- <a id="f-RequiredSkill"></a><a id="f-RequiredSkillValue"></a>**`RequiredSkill` / `RequiredSkillValue`** - Skill requirement.
- <a id="f-RequiredCondition"></a>**`RequiredCondition`** - Condition ID.
- <a id="f-RepObjectiveFaction"></a><a id="f-RepObjectiveValue"></a>**`RepObjectiveFaction` / `RepObjectiveValue`** - Reputation goal.
- <a id="f-RequiredMinRepFaction"></a><a id="f-RequiredMinRepValue"></a>**`RequiredMinRepFaction` / `RequiredMinRepValue`** - Minimum reputation requirement.
- <a id="f-RequiredMaxRepFaction"></a><a id="f-RequiredMaxRepValue"></a>**`RequiredMaxRepFaction` / `RequiredMaxRepValue`** - Maximum reputation (for hostile quests).
- <a id="f-SuggestedPlayers"></a>**`SuggestedPlayers`** - Suggested group size.
- <a id="f-LimitTime"></a>**`LimitTime`** - Time limit (seconds).
- <a id="f-QuestFlags"></a>**`QuestFlags`** - Flags.
- <a id="f-SpecialFlags"></a>**`SpecialFlags`** - Special flags (e.g., `1` repeatable, `2` exploration/event).
- <a id="f-NextQuestId"></a><a id="f-PrevQuestId"></a>**`PrevQuestId` / `NextQuestId`** - Quest chain links.
- <a id="f-ExclusiveGroup"></a>**`ExclusiveGroup`** - Shared group (only one quest in group can be active).
- <a id="f-BreadcrumbForQuestId"></a>**`BreadcrumbForQuestId`** - Lead-in quest pointing at the target quest X given here.
  This quest is acceptable only while X itself is takeable (it hides behind X's own prerequisites);
  while this breadcrumb is active/incomplete, X cannot be accepted.
- <a id="f-NextQuestInChain"></a>**`NextQuestInChain`** - Next quest in chain.
- <a id="f-SrcItemCount"></a><a id="f-SrcItemId"></a>**`SrcItemId` / `SrcItemCount`** - Source item required.
- <a id="f-SrcSpell"></a>**`SrcSpell`** - Spell cast to start quest.
- <a id="f-Details"></a><a id="f-Objectives"></a><a id="f-Title"></a>**`Title` / `Details` / `Objectives`** - Quest text.
- <a id="f-OfferRewardText"></a>**`OfferRewardText`** - Text shown when completing.
- <a id="f-RequestItemsText"></a>**`RequestItemsText`** - Text shown when turning in.
- <a id="f-EndText"></a>**`EndText`** - Final dialogue.
- <a id="f-ObjectiveText1"></a><a id="f-ObjectiveText2"></a><a id="f-ObjectiveText3"></a><a id="f-ObjectiveText4"></a>**`ObjectiveText1-4`** - Objective descriptions.
- <a id="f-ReqItemCount1"></a><a id="f-ReqItemCount2"></a><a id="f-ReqItemCount3"></a><a id="f-ReqItemCount4"></a><a id="f-ReqItemId1"></a><a id="f-ReqItemId2"></a><a id="f-ReqItemId3"></a><a id="f-ReqItemId4"></a>**`ReqItemId1-4` / `ReqItemCount1-4`** - Required items.
- <a id="f-ReqSourceCount1"></a><a id="f-ReqSourceCount2"></a><a id="f-ReqSourceCount3"></a><a id="f-ReqSourceCount4"></a><a id="f-ReqSourceId1"></a><a id="f-ReqSourceId2"></a><a id="f-ReqSourceId3"></a><a id="f-ReqSourceId4"></a>**`ReqSourceId1-4` / `ReqSourceCount1-4`** - Required source items.
- <a id="f-ReqCreatureOrGOCount1"></a><a id="f-ReqCreatureOrGOCount2"></a><a id="f-ReqCreatureOrGOCount3"></a><a id="f-ReqCreatureOrGOCount4"></a><a id="f-ReqCreatureOrGOId1"></a><a id="f-ReqCreatureOrGOId2"></a><a id="f-ReqCreatureOrGOId3"></a><a id="f-ReqCreatureOrGOId4"></a>**`ReqCreatureOrGOId1-4` / `ReqCreatureOrGOCount1-4`** - Required kills/interactions.
- <a id="f-ReqSpellCast1"></a><a id="f-ReqSpellCast2"></a><a id="f-ReqSpellCast3"></a><a id="f-ReqSpellCast4"></a>**`ReqSpellCast1-4`** - Required spell casts.
- <a id="f-RewChoiceItemCount1"></a><a id="f-RewChoiceItemCount2"></a><a id="f-RewChoiceItemCount3"></a><a id="f-RewChoiceItemCount4"></a><a id="f-RewChoiceItemCount5"></a><a id="f-RewChoiceItemCount6"></a><a id="f-RewChoiceItemId1"></a><a id="f-RewChoiceItemId2"></a><a id="f-RewChoiceItemId3"></a><a id="f-RewChoiceItemId4"></a><a id="f-RewChoiceItemId5"></a><a id="f-RewChoiceItemId6"></a>**`RewChoiceItemId1-6` / `RewChoiceItemCount1-6`** - Choice rewards.
- <a id="f-RewItemCount1"></a><a id="f-RewItemCount2"></a><a id="f-RewItemCount3"></a><a id="f-RewItemCount4"></a><a id="f-RewItemId1"></a><a id="f-RewItemId2"></a><a id="f-RewItemId3"></a><a id="f-RewItemId4"></a>**`RewItemId1-4` / `RewItemCount1-4`** - Fixed item rewards.
- <a id="f-RewRepFaction1"></a><a id="f-RewRepFaction2"></a><a id="f-RewRepFaction3"></a><a id="f-RewRepFaction4"></a><a id="f-RewRepFaction5"></a><a id="f-RewRepValue1"></a><a id="f-RewRepValue2"></a><a id="f-RewRepValue3"></a><a id="f-RewRepValue4"></a><a id="f-RewRepValue5"></a>**`RewRepFaction1-5` / `RewRepValue1-5`** - Reputation rewards.
- <a id="f-RewRepSpilloverMask"></a>**`RewRepSpilloverMask`** - Bitmask over `RewRepFaction1..5` indexes
  (bit 0 = faction 1 ... bit 4 = faction 5). A set bit **disables** reputation spillover from that reward faction.
- <a id="f-RewXP"></a>**`RewXP`** - Experience reward.
- <a id="f-RewOrReqMoney"></a>**`RewOrReqMoney`** - Money reward (or cost).
- <a id="f-RewMoneyMaxLevel"></a>**`RewMoneyMaxLevel`** - Max-level money reward.
- <a id="f-RewSpell"></a>**`RewSpell`** - Spell reward (learn spell).
- <a id="f-RewSpellCast"></a>**`RewSpellCast`** - Spell cast on completion.
- <a id="f-RewMailDelaySecs"></a><a id="f-RewMailMoney"></a><a id="f-RewMailTemplateId"></a>**`RewMailTemplateId` / `RewMailDelaySecs` / `RewMailMoney`** - Mail reward.
- <a id="f-PointMapId"></a><a id="f-PointOpt"></a><a id="f-PointX"></a><a id="f-PointY"></a>**`PointMapId` / `PointX` / `PointY` / `PointOpt`** - Map POI for quest objective.
- <a id="f-DetailsEmote1"></a><a id="f-DetailsEmote2"></a><a id="f-DetailsEmote3"></a><a id="f-DetailsEmote4"></a><a id="f-DetailsEmoteDelay1"></a><a id="f-DetailsEmoteDelay2"></a><a id="f-DetailsEmoteDelay3"></a><a id="f-DetailsEmoteDelay4"></a>**`DetailsEmote1-4` / `DetailsEmoteDelay1-4`** - Emotes during quest details.
- <a id="f-CompleteEmote"></a><a id="f-IncompleteEmote"></a>**`IncompleteEmote` / `CompleteEmote`** - Emotes for incomplete/complete state.
- <a id="f-OfferRewardEmote1"></a><a id="f-OfferRewardEmote2"></a><a id="f-OfferRewardEmote3"></a><a id="f-OfferRewardEmote4"></a><a id="f-OfferRewardEmoteDelay1"></a><a id="f-OfferRewardEmoteDelay2"></a><a id="f-OfferRewardEmoteDelay3"></a><a id="f-OfferRewardEmoteDelay4"></a>**`OfferRewardEmote1-4` / `OfferRewardEmoteDelay1-4`** - Emotes during reward offering.
- <a id="f-StartScript"></a>**`StartScript`** - Script ID for quest start.
- <a id="f-CompleteScript"></a>**`CompleteScript`** - Script ID for quest completion.

---

## Flag Bitmasks

Values from `src/game/QuestDef.h`.

### `QuestFlags` (client-visible)

| Flag | Name | Effect |
| ---: | :--- | :--- |
| 0x00000000 | NONE | no flags |
| 0x00000001 | STAY_ALIVE | *(not used currently)* |
| 0x00000002 | PARTY_ACCEPT | whole party gets a confirmation popup to accept |
| 0x00000004 | EXPLORATION | *(not used currently)* |
| 0x00000008 | SHARABLE | quest can be shared with party members (`CanShareQuest`) |
| 0x00000010 | - | reserved / unused |
| 0x00000020 | EPIC | *(unused)* |
| 0x00000040 | RAID | *(unused)* |
| 0x00000100 | UNK2 | - |
| 0x00000200 | HIDDEN_REWARDS | rewards hidden in the offer window & quest log |
| 0x00000400 | AUTO_REWARDED | auto-completes; never appears in the quest log |

### `SpecialFlags` (server-side)

Set with `|value` syntax in DB:

| Value | Name | Effect |
| ---: | :--- | :--- |
| 1 | REPEATABLE | quest can be repeated (resets on completion) |
| 2 | EXPLORATION_OR_EVENT | completes via area exploration, the `QUEST_EXPLORED` script command, or the quest-complete spell effect |

Values 0x008+ (DELIVER, SPEAKTO, KILL_OR_CAST, TIMED) are **internal** flags computed by the
core from your objective columns; never set them manually.

---

### Interaction With Other Systems

- Timed quests: `LimitTime > 0` sets the countdown (internal TIMED flag).
- Exploration completion pairs `SpecialFlags = 2` with an areatrigger id in
  [`areatrigger_involvedrelation`](areatrigger_involvedrelation.md).
- Repeatable daily/weekly rotation is driven by
  [game events](../Game-Events.md) + `QUEST_SPECIAL_FLAG_REPEATABLE`.
- Reward visibility for surprise rewards uses HIDDEN_REWARDS.

---

### Related Pages

- [Quest System](../Quest-System.md)
- [Tutorial: Adding a Custom Quest](../Tutorial-Custom-Quest.md)
