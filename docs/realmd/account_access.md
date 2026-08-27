# account_access Table

GM level and realm assignment per account (console/GM permissions).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`id`](#f-id) | int(11) unsigned | PRI | NO |  |  |
| [`gmlevel`](#f-gmlevel) | tinyint(3) unsigned |  | NO |  |  |
| [`RealmID`](#f-RealmID) | int(11) | PRI | NO |  |  |

---

## Field Breakdown

- <a id="f-id"></a>**`id`** - Primary Key. Account id.
- <a id="f-gmlevel"></a>**`gmlevel`** - Security level 0-7 applied on this realm (see Security & RBAC page).
- <a id="f-RealmID"></a>**`RealmID`** - Primary Key. Realm the level applies to; `-1` = all realms.
