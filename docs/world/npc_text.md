# npc_text Table

Defines NPC gossip text with multiple broadcast text IDs and probabilities.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`ID`](#f-ID) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`BroadcastTextID0`](#f-BroadcastTextID0) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability0`](#f-Probability0) | float |  | NO | 0 |  |
| [`BroadcastTextID1`](#f-BroadcastTextID1) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability1`](#f-Probability1) | float |  | NO | 0 |  |
| [`BroadcastTextID2`](#f-BroadcastTextID2) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability2`](#f-Probability2) | float |  | NO | 0 |  |
| [`BroadcastTextID3`](#f-BroadcastTextID3) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability3`](#f-Probability3) | float |  | NO | 0 |  |
| [`BroadcastTextID4`](#f-BroadcastTextID4) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability4`](#f-Probability4) | float |  | NO | 0 |  |
| [`BroadcastTextID5`](#f-BroadcastTextID5) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability5`](#f-Probability5) | float |  | NO | 0 |  |
| [`BroadcastTextID6`](#f-BroadcastTextID6) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability6`](#f-Probability6) | float |  | NO | 0 |  |
| [`BroadcastTextID7`](#f-BroadcastTextID7) | mediumint(6) unsigned |  | NO | 0 |  |
| [`Probability7`](#f-Probability7) | float |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-ID"></a>**`ID`** - Primary Key. Gossip menu text-set id referenced by [`gossip_menu`](gossip_menu.md).text_id.
- <a id="f-BroadcastTextID0"></a>**`BroadcastTextID0`** - Greeting option 1 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability0"></a>**`Probability0`** - Weight of greeting option 1 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID1"></a>**`BroadcastTextID1`** - Greeting option 2 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability1"></a>**`Probability1`** - Weight of greeting option 2 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID2"></a>**`BroadcastTextID2`** - Greeting option 3 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability2"></a>**`Probability2`** - Weight of greeting option 3 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID3"></a>**`BroadcastTextID3`** - Greeting option 4 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability3"></a>**`Probability3`** - Weight of greeting option 4 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID4"></a>**`BroadcastTextID4`** - Greeting option 5 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability4"></a>**`Probability4`** - Weight of greeting option 5 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID5"></a>**`BroadcastTextID5`** - Greeting option 6 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability5"></a>**`Probability5`** - Weight of greeting option 6 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID6"></a>**`BroadcastTextID6`** - Greeting option 7 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability6"></a>**`Probability6`** - Weight of greeting option 7 in the random selection (0 disables the slot).
- <a id="f-BroadcastTextID7"></a>**`BroadcastTextID7`** - Greeting option 8 of eight: a [`broadcast_text`](broadcast_text.md) id.
- <a id="f-Probability7"></a>**`Probability7`** - Weight of greeting option 8 in the random selection (0 disables the slot).
