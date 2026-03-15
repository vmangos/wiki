# The broadcast_text table

Contains various game texts used in scripts and the `npc_text` and `gossip_menu_option` tables.

## Structure

### 1. entry - mediumint(8) unsigned, primary key

Unique id for this text. This is a sniffed field and should not be edited. Ids above 100000 are custom.

### 2. male_text - longtext

Text that is shown to male characters. This is a sniffed field and should not be edited.

### 3. female_text - longtext

Text that is shown to female characters. This is a sniffed field and should not be edited.

### 4. sound_id - mediumint(8) unsigned

Sound id from the `sound_entries` table that will be played when the text is shown.

### 5. chat_type - mediumint(8) unsigned

Chat type to be used when the text is said.
```
0 - Say
1 - Yell
2 - Text Emote
3 - Zone Emote
4 - Whisper
5 - Boss Whisper
6 - Zone Yell
```

### 6. language_id - mediumint(8) unsigned

Language id from Languages.dbc. This is a sniffed field and should not be edited.

### 7. emote_id1 - mediumint(8) unsigned

Emote id from Emotes.dbc to be played when the text is shown. This is a sniffed value for gossip texts used in the `npc_text` table.

### 8. emote_id2 - mediumint(8) unsigned

Emote id from Emotes.dbc to be played when the text is shown. This is a sniffed value for gossip texts used in the `npc_text` table.

### 9. emote_id3 - mediumint(8) unsigned

Emote id from Emotes.dbc to be played when the text is shown. This is a sniffed value for gossip texts used in the `npc_text` table.

### 10. emote_delay1 - mediumint(8) unsigned

Delay in milliseconds before showing the first emote. This is a sniffed value for gossip texts used in the `npc_text` table.

### 11. emote_delay2 - mediumint(8) unsigned

Delay in milliseconds before showing the second emote. This is a sniffed value for gossip texts used in the `npc_text` table.

### 12. emote_delay3 - mediumint(8) unsigned

Delay in milliseconds before showing the third emote. This is a sniffed value for gossip texts used in the `npc_text` table.
