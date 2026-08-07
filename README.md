# galicia-surf-data

Published forecast bundles for the **Galicia Surf Decision Engine**.

This repository contains **only generated data**. It is public because the
consuming Claude skill fetches these files over plain HTTPS and cannot
authenticate. Nothing here is hand-written and nothing here is personal — it is
wave, wind and tide numbers derived from Open-Meteo and Wisuki.

The pipeline source, spot knowledge base and skill body live in
[galicia-surf-forecast](https://github.com/RomanVazquezL/galicia-surf-forecast),
which is private.

## Files

| Path | Contents |
|---|---|
| `today_summary.json` | Per-spot, per-window aggregates with model-agreement labels. **Primary consumer input.** |
| `archive_summary/{YYYY-MM-DD}.json` | Dated copy of the above. Preferred — the dated path defeats `web_fetch` caching. |
| `today.json` | Raw multi-model bundle (3 wave + 3 wind models per spot). |
| `archive/{YYYY-MM-DD}.json` | Dated copy of the raw bundle, unslimmed. |

Refreshed twice daily by a GitHub Actions cron in the source repository.
Commits here are made by `forecast-bot` via a write-scoped deploy key.
