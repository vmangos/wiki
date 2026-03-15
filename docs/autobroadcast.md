# The autobroadcast table

Used to define messages that sent to all players periodically.

## Structure

### 1. delay - int(11) unsigned

Delay in seconds between announcements.

### 2. string_id - int(11)

Text id from the `mangos_string` table. This is the message that gets sent.

### 3. comment - varchar(255)

A description of this entry. This is not the actual text that will be sent!

