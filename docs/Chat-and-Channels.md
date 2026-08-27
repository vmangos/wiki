# Chat & Channels

How the chat pipeline and player-managed channels work
(`src/game/Chat/Channel*`, `ChatHandler`, `src/game/Handlers/ChatHandler.cpp`).

---

## Built-in Channels

- **General / Trade / LocalDefense / LFG** join automatically per zone/city as on retail 1.12;
  membership follows zone changes.
- World-defence and trade behaviour differs per faction; LFG channel is global since patch
  1.7 timelines (progression-aware).

## Custom Channels

Player-created channels (`/join name [password]`) are in-memory only: **no database table**
backs them, so they vanish on restart. Ownership/moderation model:

| Role | Capability |
| :--- | :--- |
| Owner | initial creator; can transfer ownership |
| Moderator | kick/ban/mute within the channel (when moderation is on) |
| Banned list | per-channel ban entries |

Moderation verbs are driven by standard client commands (`/channelpassword`,
`/channelmoderator`, `/channelban`, `/channelkick`, `/channelinvite`, …) which map to
`CMSG_CHANNEL_*` opcodes handled by `ChannelMgr`.

All lifecycle notices (joined/left/password changed/kicked…) are the `CHAT_*_NOTICE` codes in
`Channel.h`.

---

## Server-Side Protections

From `mangosd.conf`:

| Setting | Purpose |
| :--- | :--- |
| `ChatFlood.MessageCount` / `.MessageDelay` / `.MuteTime` | flood detection: N messages faster than delay → temporary mute |
| `ChatFakeMessagePreventing` | strip fake system-style messages |
| `ChatStrictLinkChecking.Severity/.Kick` | validate `[item]` link payloads to block crafted-link exploits |

Mutes issued by flood control or GMs persist through [`account`](realmd/account.md).mutetime
([realmd](realmd/account.md)).

---

## GM Chat Tools

- `.send message <name> <text>` - whisper a player.
- `.send mass mail/money/items …` - server-wide notices.
- `gm chat` toggle - speak in the GM chat badge channel.
- Channel announcements (`CHAT_ANNOUNCEMENTS_ON/OFF`) are player-facing toggles, independent of
  these.

See [GM Commands Reference](GM-Commands.md) for the full trees.

---

## Related Pages

- [Security & RBAC](Security-RBAC.md)
- [Tickets & Player Support](Tickets.md)
