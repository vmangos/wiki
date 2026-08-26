# ip2nation Table

Mapping of IP ranges to country codes. Not read or written by core (all geolocking uses [`geoip`](geoip.md)).

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`ip`](#f-ip) | int(11) unsigned | MUL | NO | 0 |  |
| [`country`](#f-country) | char(2) |  | NO | '' |  |
