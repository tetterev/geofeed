# Contributing

## Who Maintains This Feed

The `geofeed.csv` file is maintained exclusively by **Allianz Technology SE — Network Engineering**. Only members of the `@Allianz/network-team` GitHub team can submit changes to the feed data. This ensures the geofeed remains authoritative and accurate.

## Reporting Incorrect or Missing Mappings

If you are a geolocation provider, partner, or user and you believe an IP prefix is mapped to the wrong location — or is missing from the feed — please [open an issue](https://github.com/Allianz/geofeed/issues/new?template=incorrect-mapping.md) using the provided template.

To help us resolve the report efficiently, please include:

- The IP prefix or address affected
- The current (incorrect) location you are observing in your database
- The correct location (country, region, city) with supporting evidence (e.g. RIR allocation data, official documentation)
- Your contact information (optional, for follow-up)

The network team reviews incoming reports and updates the feed as appropriate.

## Pull Requests

Direct pull requests to modify `geofeed.csv` from outside the network team will not be accepted. If you have a correction, please open an issue instead.

Pull requests for documentation improvements (README, CONTRIBUTING, SECURITY) are welcome.

All changes to `geofeed.csv` require a review from `@Allianz/network-team` as enforced by [CODEOWNERS](.github/CODEOWNERS).
