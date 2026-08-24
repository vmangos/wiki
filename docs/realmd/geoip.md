# geoip Table

IP range to country mapping cache used by the login server.

---

## Schema Summary

| Field | Type | Key | Null | Default | Extra |
| :---- | :---- | :--- | :--- | :------ | :---- |
| [`network_start_integer`](#f-network_start_integer) | int(11) | MUL | YES |  |  |
| [`network_last_integer`](#f-network_last_integer) | int(11) | MUL | YES |  |  |
| [`geoname_id`](#f-geoname_id) | text |  | YES |  |  |
| [`registered_country_geoname_id`](#f-registered_country_geoname_id) | text |  | YES |  |  |
| [`represented_country_geoname_id`](#f-represented_country_geoname_id) | text |  | YES |  |  |
| [`is_anonymous_proxy`](#f-is_anonymous_proxy) | int(11) |  | YES |  |  |
| [`is_satellite_provider`](#f-is_satellite_provider) | int(11) |  | YES |  |  |
| [`postal_code`](#f-postal_code) | text |  | YES |  |  |
| [`latitude`](#f-latitude) | double |  | YES |  |  |
| [`longitude`](#f-longitude) | double |  | YES |  |  |
| [`accuracy_radius`](#f-accuracy_radius) | int(11) |  | YES |  |  |

---

## Field Breakdown

- <a id="f-network_start_integer"></a>**`network_start_integer`** - Numeric IP range boundaries for the network block.
- <a id="f-network_last_integer"></a>**`network_last_integer`** - Numeric IP range boundaries for the network block.
- <a id="f-geoname_id"></a>**`geoname_id`** - Country GeoName resolved for this range.
- <a id="f-registered_country_geoname_id"></a>**`registered_country_geoname_id`** - Registered (as opposed to routed) country.
- <a id="f-represented_country_geoname_id"></a>**`represented_country_geoname_id`** - Military/embassy representative country if any.
- <a id="f-is_anonymous_proxy"></a>**`is_anonymous_proxy`** - Classification flags from the GeoIP dataset.
- <a id="f-is_satellite_provider"></a>**`is_satellite_provider`** - Classification flags from the GeoIP dataset.
- <a id="f-postal_code"></a>**`postal_code`** - Postal code when known.
- <a id="f-latitude"></a>**`latitude`** - Approximate location and radius (km).
- <a id="f-longitude"></a>**`longitude`** - Approximate location and radius (km).
- <a id="f-accuracy_radius"></a>**`accuracy_radius`** - Approximate location and radius (km).
