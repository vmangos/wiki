# petition_sign Table

Signatures collected on a petition.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`owner_guid`](#f-owner_guid) | int(10) unsigned | MUL | NO |  |  |
| [`petition_guid`](#f-petition_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`player_guid`](#f-player_guid) | int(11) unsigned | PRI | NO | 0 |  |
| [`player_account`](#f-player_account) | int(11) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-owner_guid"></a>**`owner_guid`** - Charter holder.
- <a id="f-petition_guid"></a>**`petition_guid`** - Primary Key. Charter item guid being signed.
- <a id="f-player_guid"></a>**`player_guid`** - Primary Key. Signer.
- <a id="f-player_account"></a>**`player_account`** - Signer's account (one signature per account rule).
