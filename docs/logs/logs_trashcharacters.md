# logs_trashcharacters Table

Characters flagged as trash/farm bots by detection systems.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`guid`](#f-guid) | int(10) unsigned | PRI | NO |  |  |
| [`data`](#f-data) | varchar(255) |  | NO |  |  |
| [`cluster`](#f-cluster) | tinyint(3) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-guid"></a>**`guid`** - Primary Key. Character flagged by detection systems.
- <a id="f-data"></a>**`data`** - Detection score/payload.
- <a id="f-cluster"></a>**`cluster`** - Cluster/grouping tag of the detection run.
