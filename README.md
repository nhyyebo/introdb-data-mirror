<p align="center">
  <a href="https://introdb.app"><img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/logo.svg" alt="IntroDB" width="104" height="104"></a>
</p>

<h1 align="center">IntroDB open data</h1>

<p align="center">
  Intro, recap, outro and post-credits timestamps for TV and movies, exported daily.
</p>

<p align="center">
  <a href="https://opendatacommons.org/licenses/odbl/1-0/"><img src="https://img.shields.io/badge/license-ODbL%201.0-cba6f7?style=flat-square" alt="License: ODbL 1.0"></a>
  <a href="https://data.introdb.app/latest/manifest.json"><img src="https://img.shields.io/badge/export-daily-89b4fa?style=flat-square" alt="Exported daily"></a>
  <a href="https://github.com/nhyyebo/introdb-data-mirror/releases"><img src="https://img.shields.io/badge/mirror-weekly-89b4fa?style=flat-square" alt="Mirrored weekly"></a>
  <img src="https://img.shields.io/badge/format-csv.gz-6c7086?style=flat-square" alt="Format: gzipped CSV">
</p>

<p align="center">
  <a href="https://introdb.app"><img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/globe.svg" width="16" height="16" alt=""> introdb.app</a>
  &nbsp;&middot;&nbsp;
  <a href="https://api.introdb.app"><img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/code-xml.svg" width="16" height="16" alt=""> API docs</a>
  &nbsp;&middot;&nbsp;
  <a href="https://introdb.app/discord">Discord</a>
</p>

A daily export of every live timestamp in IntroDB. It contains the community result for each episode and nothing about the people who submitted it.

## <img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/download.svg" width="22" height="22" alt=""> Download

- Latest: https://data.introdb.app/latest/manifest.json
- Daily snapshots: `https://data.introdb.app/snapshots/YYYY-MM-DD/`, kept for 90 days
- Weekly copies: [GitHub releases](https://github.com/nhyyebo/introdb-data-mirror/releases)

```sh
curl -sO https://data.introdb.app/latest/segments.csv.gz
gzip -dc segments.csv.gz | head
```

## <img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/database.svg" width="22" height="22" alt=""> Files

### <img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/file-spreadsheet.svg" width="18" height="18" alt=""> segments.csv.gz

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

### <img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/file-x.svg" width="18" height="18" alt=""> segmentless.csv.gz

Episodes marked as having no intro, recap or outro.
Columns: `imdb_id, is_movie, season, episode, segment, updated_at`.

### <img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/file-json.svg" width="18" height="18" alt=""> manifest.json

When the export was made, the license, and the row count, size and sha256 of each file.

## <img src="https://raw.githubusercontent.com/nhyyebo/introdb-data-mirror/main/assets/icons/scale.svg" width="22" height="22" alt=""> License

This data is available under the [Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/).
You can use it for anything, including commercial projects, as long as you:

- credit IntroDB with "Contains data from IntroDB (introdb.app), available under the ODbL."
- release any database you publish that's built from this one under the ODbL as well
- offer an unrestricted copy if you distribute it in a restricted form

The API at https://api.introdb.app is for looking up single episodes. If you need everything, download these files rather than crawling the API.

<sub>Icons from [Lucide](https://lucide.dev) (ISC).</sub>
