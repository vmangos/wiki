# gossip_menu_option Table

Defines options within a gossip menu - buttons, actions, and conditions.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`menu_id`](#f-menu_id) | smallint(6) unsigned | PRI | NO | 0 |  |
| [`id`](#f-id) | smallint(6) unsigned | PRI | NO | 0 |  |
| [`option_icon`](#f-option_icon) | mediumint(8) unsigned |  | NO | 0 |  |
| [`option_text`](#f-option_text) | text |  | YES |  |  |
| [`option_broadcast_text`](#f-option_broadcast_text) | mediumint(6) unsigned |  | NO | 0 |  |
| [`option_id`](#f-option_id) | tinyint(3) unsigned |  | NO | 0 |  |
| [`npc_option_npcflag`](#f-npc_option_npcflag) | int(10) unsigned |  | NO | 0 |  |
| [`action_menu_id`](#f-action_menu_id) | mediumint(8) |  | NO | 0 |  |
| [`action_poi_id`](#f-action_poi_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`action_script_id`](#f-action_script_id) | mediumint(8) unsigned |  | NO | 0 |  |
| [`box_coded`](#f-box_coded) | tinyint(3) unsigned |  | NO | 0 |  |
| [`box_money`](#f-box_money) | int(11) unsigned |  | NO | 0 |  |
| [`box_text`](#f-box_text) | text |  | YES |  |  |
| [`box_broadcast_text`](#f-box_broadcast_text) | mediumint(6) unsigned |  | NO | 0 |  |
| [`condition_id`](#f-condition_id) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-menu_id"></a>**`menu_id`** - Primary Key. Gossip menu ID ([`gossip_menu`](gossip_menu.md).entry).
- <a id="f-id"></a>**`id`** - Primary Key. Option index within the menu.
- <a id="f-option_icon"></a>**`option_icon`** - Icon to display (e.g., quest, vendor, taxi).
- <a id="f-option_text"></a>**`option_text`** - Text shown for this option.
- <a id="f-option_broadcast_text"></a>**`option_broadcast_text`** - Broadcast text ID for localized version.; references [`broadcast_text`](broadcast_text.md).entry
- <a id="f-option_id"></a>**`option_id`** - Action type (`Gossip_Option`, `GossipDef.h`): 0 none,
  1 gossip, 2 questgiver, 3 vendor, 4 taxi, 5 trainer, 6 spirit healer, 7 spirit guide,
  8 innkeeper, 9 banker, 10 petitioner, 11 tabard designer, 12 battleground, 13 auctioneer,
  14 stable pet, 15 armorer, 16 unlearn talents, 17 unlearn pet skills.
- <a id="f-npc_option_npcflag"></a>**`npc_option_npcflag`** - NPC flag required to display.
- <a id="f-action_menu_id"></a>**`action_menu_id`** - Menu to open when selected: `>0` opens that gossip menu,
  `<0` closes the gossip window. For vendor options it doubles as the vendor-menu filter
  (`1` normal / `2` template / `3` both).
- <a id="f-action_poi_id"></a>**`action_poi_id`** - Point of interest to display.
- <a id="f-action_script_id"></a>**`action_script_id`** - Script to execute.
- <a id="f-box_coded"></a>**`box_coded`** - `1` if requires a key/coded box.
- <a id="f-box_money"></a>**`box_money`** - Money required to choose this option (currently ignored by core -
  the core reads but never applies it).
- <a id="f-box_text"></a>**`box_text`** - Text shown in the confirmation box.
- <a id="f-box_broadcast_text"></a>**`box_broadcast_text`** - Broadcast text ID for box text.; references [`broadcast_text`](broadcast_text.md).entry
- <a id="f-condition_id"></a>**`condition_id`** - Condition required. (see [`conditions`](conditions.md).condition_entry)
