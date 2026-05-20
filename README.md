# Allianz Geofeed

This repository publishes Allianz's self-hosted IP geolocation feed in accordance with [RFC 8805 — A Format for Self-Published IP Geolocation Feeds](https://www.rfc-editor.org/rfc/rfc8805).

## Why This Exists

Allianz operates a large global IP address space. Geolocation service providers such as [MaxMind](https://www.maxmind.com/) and [IP2Location](https://www.ip2location.com/) maintain databases that map IP prefixes to geographic locations. These databases are consumed by SaaS providers — including Microsoft 365 and Citrix — to optimize service delivery: routing users to the nearest point of presence, applying region-specific policies, and unlocking performance features.

Inaccurate IP-to-location mappings cause suboptimal routing and degraded user experience. Publishing an authoritative geofeed enables providers to correct their databases and improve service quality for Allianz users worldwide.

## Geofeed URL

The geofeed is published at the following stable URL:

``` txt
https://raw.githubusercontent.com/Allianz/geofeed/main/geofeed.csv
```

Geolocation providers can fetch and ingest this file directly.

## File Format

The `geofeed.csv` file follows the RFC 8805 format: a CSV file with the following five columns.

| Column | Description | Example |
| --- | --- | --- |
| `ip_prefix` | CIDR-notation IPv4 or IPv6 prefix | `203.0.113.0/24` |
| `alpha2code` | ISO 3166-1 alpha-2 country code | `DE` |
| `region` | Full ISO 3166-2 region code (optional) | `DE-BY` |
| `city` | City name in ASCII (optional) | `Munich` |
| `postal_code` | Postal code (optional) | `80333` |

Lines beginning with `#` are comments and are ignored by parsers. The file begins with a required `# Geofeed <url>` self-reference comment as defined in RFC 8805 §2.2.

## For Geolocation Providers

To automatically discover this feed, the canonical URL is registered in the WHOIS/RDAP records for Allianz IP prefixes via the `remarks:` attribute in the RIR (Regional Internet Registry) objects, as specified in RFC 8805 §3.

You can verify discovery by querying the WHOIS record for any Allianz IP prefix and looking for:

``` txt
remarks: Geofeed https://raw.githubusercontent.com/Allianz/geofeed/main/geofeed.csv
```

## Reporting Incorrect Mappings

If you believe an IP prefix is mapped to the wrong location, please [open an issue](https://github.com/Allianz/geofeed/issues/new?template=incorrect-mapping.md) using the provided template. Include:

- The IP prefix or address affected
- The current (incorrect) mapping you are observing
- The correct location with supporting evidence

Issues are reviewed by the Allianz Network Engineering team.

## Maintenance

This feed is maintained by **Allianz Technology SE — IP Services Team**. Only team members can submit changes to `geofeed.csv`. See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## License

This data is released under the [CC0 1.0 Universal (Public Domain Dedication)](LICENSE). You are free to copy, modify, distribute, and use the data for any purpose without restriction.
