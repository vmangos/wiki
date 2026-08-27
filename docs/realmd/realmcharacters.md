# realmcharacters Table

How many characters each account has per realm (enforces character-per-realm limit).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`realmid`](#f-realmid) | int(11) unsigned | PRI | NO | 0 |  |
| [`acctid`](#f-acctid) | bigint(20) unsigned | PRI | NO |  |  |
| [`numchars`](#f-numchars) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-realmid"></a>**`realmid`** - Primary Key. Realm id.
- <a id="f-acctid"></a>**`acctid`** - Primary Key. Account id ([`account`](account.md).id).
- <a id="f-numchars"></a>**`numchars`** - Characters this account owns on that realm (enforces per-realm limit).
