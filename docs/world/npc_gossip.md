# npc_gossip Table

Per-spawn gossip overrides - assigns custom gossip text to specific creature GUIDs.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`npc_guid`](#f-npc_guid) | int(10) unsigned | PRI | NO | 0 |  |
| [`textid`](#f-textid) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-npc_guid"></a>**`npc_guid`** - Primary Key. Creature GUID ([`creature`](creature.md).guid).
- <a id="f-textid"></a>**`textid`** - Gossip text ID ([`npc_text`](npc_text.md).ID).
