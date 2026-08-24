# locales_gossip_menu_option Table

Localized gossip menu option texts.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`menu_id`](#f-menu_id) | smallint(6) unsigned | PRI | NO | 0 |  |
| [`id`](#f-id) | smallint(6) unsigned | PRI | NO | 0 |  |
| [`option_text_loc1`](#f-option_text_loc1) | text |  | YES |  |  |
| [`option_text_loc2`](#f-option_text_loc2) | text |  | YES |  |  |
| [`option_text_loc3`](#f-option_text_loc3) | text |  | YES |  |  |
| [`option_text_loc4`](#f-option_text_loc4) | text |  | YES |  |  |
| [`option_text_loc5`](#f-option_text_loc5) | text |  | YES |  |  |
| [`option_text_loc6`](#f-option_text_loc6) | text |  | YES |  |  |
| [`option_text_loc7`](#f-option_text_loc7) | text |  | YES |  |  |
| [`option_text_loc8`](#f-option_text_loc8) | text |  | YES |  |  |
| [`box_text_loc1`](#f-box_text_loc1) | text |  | YES |  |  |
| [`box_text_loc2`](#f-box_text_loc2) | text |  | YES |  |  |
| [`box_text_loc3`](#f-box_text_loc3) | text |  | YES |  |  |
| [`box_text_loc4`](#f-box_text_loc4) | text |  | YES |  |  |
| [`box_text_loc5`](#f-box_text_loc5) | text |  | YES |  |  |
| [`box_text_loc6`](#f-box_text_loc6) | text |  | YES |  |  |
| [`box_text_loc7`](#f-box_text_loc7) | text |  | YES |  |  |
| [`box_text_loc8`](#f-box_text_loc8) | text |  | YES |  |  |

---

## Field Breakdown

- <a id="f-menu_id"></a>**`menu_id`** - Part of the primary key. Gossip menu id.; references [`gossip_menu_option`](gossip_menu_option.md).menu_id / [`gossip_menu_option`](gossip_menu_option.md).id
- <a id="f-id"></a>**`id`** - Part of the primary key. Option index within the menu.; references [`gossip_menu_option`](gossip_menu_option.md).menu_id / [`gossip_menu_option`](gossip_menu_option.md).id
- <a id="f-option_text_loc1"></a>**`option_text_loc1`** - Localized option label.
- <a id="f-option_text_loc2"></a>**`option_text_loc2`** - Localized option label.
- <a id="f-option_text_loc3"></a>**`option_text_loc3`** - Localized option label.
- <a id="f-option_text_loc4"></a>**`option_text_loc4`** - Localized option label.
- <a id="f-option_text_loc5"></a>**`option_text_loc5`** - Localized option label.
- <a id="f-option_text_loc6"></a>**`option_text_loc6`** - Localized option label.
- <a id="f-option_text_loc7"></a>**`option_text_loc7`** - Localized option label.
- <a id="f-option_text_loc8"></a>**`option_text_loc8`** - Localized option label.
- <a id="f-box_text_loc1"></a>**`box_text_loc1`** - Localized input-box text.
- <a id="f-box_text_loc2"></a>**`box_text_loc2`** - Localized input-box text.
- <a id="f-box_text_loc3"></a>**`box_text_loc3`** - Localized input-box text.
- <a id="f-box_text_loc4"></a>**`box_text_loc4`** - Localized input-box text.
- <a id="f-box_text_loc5"></a>**`box_text_loc5`** - Localized input-box text.
- <a id="f-box_text_loc6"></a>**`box_text_loc6`** - Localized input-box text.
- <a id="f-box_text_loc7"></a>**`box_text_loc7`** - Localized input-box text.
- <a id="f-box_text_loc8"></a>**`box_text_loc8`** - Localized input-box text.
