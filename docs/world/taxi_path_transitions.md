# taxi_path_transitions Table

Defines transitions between taxi paths - connects paths and nodes.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`in_path`](#f-in_path) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`out_path`](#f-out_path) | mediumint(8) unsigned | PRI | NO | 0 |  |
| [`in_node`](#f-in_node) | mediumint(8) unsigned |  | NO | 0 |  |
| [`out_node`](#f-out_node) | mediumint(8) unsigned |  | NO | 0 |  |
| [`comment`](#f-comment) | text |  | YES |  |  |
| [`build_min`](#f-build_min) | smallint(4) unsigned |  | NO | 0 |  |

---

## Field Breakdown

- <a id="f-in_path"></a>**`in_path`** - Primary Key. Incoming taxi path id (from `TaxiPath.dbc`).
- <a id="f-out_path"></a>**`out_path`** - Primary Key. Outgoing taxi path id (from `TaxiPath.dbc`).
- <a id="f-in_node"></a>**`in_node`** - Node id in the incoming path where the transition occurs.
- <a id="f-out_node"></a>**`out_node`** - Destination node ([`taxi_nodes`](taxi_nodes.md)).
- <a id="f-comment"></a>**`comment`** - Description.
- <a id="f-build_min"></a>**`build_min`** - Minimum build.
