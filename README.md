# IntroDB open data

A daily export of every live timestamp in IntroDB. It contains the community result for each episode and nothing about the people who submitted it.

- Latest: https://data.introdb.app/latest/manifest.json
- Daily snapshots: `https://data.introdb.app/snapshots/YYYY-MM-DD/`, kept for 90 days

## Files

### segments.csv.gz

One row per live segment.

| column | meaning |
| --- | --- |
| imdb_id | IMDb id of the series or movie (`tt…`) |
| is_movie | `t` for movies, which use season `0` and episode `0` |
| season, episode | episode numbering |
| segment | `intro`, `recap`, `outro` or `post-credits` |
| start_ms, end_ms | start and end in milliseconds from the start of the episode |
| confidence | 0 to 1, how closely submissions agree |
| submission_count | number of submissions behind this result |
| updated_at | last change, UTC |

### segmentless.csv.gz

Episodes marked as having no intro, recap or outro.
Columns: `imdb_id, is_movie, season, episode, segment, updated_at`.

### manifest.json

When the export was made, the license, and the row count, size and sha256 of each file.

## License

This data is available under the [Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/).
You can use it for anything, including commercial projects, as long as you:

- credit IntroDB with "Contains data from IntroDB (introdb.app), available under the ODbL."
- release any database you publish that's built from this one under the ODbL as well
- offer an unrestricted copy if you distribute it in a restricted form

The API at https://api.introdb.app is for looking up single episodes. If you need everything, download these files rather than crawling the API.
