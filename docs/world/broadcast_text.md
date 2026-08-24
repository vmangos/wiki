# broadcast_text Table

Central repository for in-game NPC text strings. Supports gender-specific variants, sound, chat type, language, and emotes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`entry`](#f-entry) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`male_text`](#f-male_text) | longtext |  | YES |  |  |
| [`female_text`](#f-female_text) | longtext |  | YES |  |  |
| [`chat_type`](#f-chat_type) | tinyint(3) unsigned |  | NO | 0 |  |
| [`sound_id`](#f-sound_id) | smallint(5) unsigned |  | NO | 0 |  |
| [`language_id`](#f-language_id) | tinyint(3) unsigned |  | NO | 0 |  |
| [`emote_id1`](#f-emote_id1) | smallint(5) unsigned |  | NO | 0 |  |
| [`emote_id2`](#f-emote_id2) | smallint(5) unsigned |  | NO | 0 |  |
| [`emote_id3`](#f-emote_id3) | smallint(5) unsigned |  | NO | 0 |  |
| [`emote_delay1`](#f-emote_delay1) | mediumint(8) unsigned |  | NO | 0 |  |
| [`emote_delay2`](#f-emote_delay2) | mediumint(8) unsigned |  | NO | 0 |  |
| [`emote_delay3`](#f-emote_delay3) | mediumint(8) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-entry"></a>**`entry`** - Primary Key. Unique text ID. IDs ≥ 100000 are custom.
- <a id="f-male_text"></a>**`male_text`** - Text spoken with a male voice.
- <a id="f-female_text"></a>**`female_text`** - Text spoken with a female voice.
- <a id="f-chat_type"></a>**`chat_type`** - Output channel:
  - `0` - Say
  - `1` - Yell
  - `2` - Text Emote
  - `3` - Boss Emote
  - `4` - Whisper
  - `5` - Boss Whisper
  - `6` - Zone Yell
  - `7` - Zone Emote
- <a id="f-sound_id"></a>**`sound_id`** - Sound to play from [`sound_entries`](sound_entries.md).id.
- <a id="f-language_id"></a>**`language_id`** - Language the line is spoken in (language skill gating). (see `Languages.dbc`)
- <a id="f-emote_id1"></a>**`emote_id1`** - Up to three emotes performed while speaking the line.
- <a id="f-emote_id2"></a>**`emote_id2`** - Up to three emotes performed while speaking the line.
- <a id="f-emote_id3"></a>**`emote_id3`** - Up to three emotes performed while speaking the line.
- <a id="f-emote_delay1"></a>**`emote_delay1`** - Delay (ms) before each corresponding emote fires.
- <a id="f-emote_delay2"></a>**`emote_delay2`** - Delay (ms) before each corresponding emote fires.
- <a id="f-emote_delay3"></a>**`emote_delay3`** - Delay (ms) before each corresponding emote fires.
*Referenced by: [`npc_text`](npc_text.md) and [`gossip_menu_option`](gossip_menu_option.md).*
