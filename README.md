# PCSO Lotto Results

This repository is a public, machine-readable mirror of historical Philippine
Charity Sweepstakes Office (PCSO) draw results for these games:

- Ultra Lotto 6/58
- Grand Lotto 6/55
- Super Lotto 6/49
- Mega Lotto 6/45
- Lotto 6/42

The source is the official [PCSO Lotto Results](https://www.pcso.gov.ph/searchlottoresult.aspx)
page. Files are updated by an automated ingestion and validation pipeline.

## Files

Results are split by game and calendar year. For example,
`results_655_2026.csv` contains 6/55 draws from 2026. Each CSV has this format:

```csv
date,n1,n2,n3,n4,n5,n6
2026-08-10,5,6,9,13,26,38
```

Numbers are stored in ascending order, regardless of the order in which PCSO
published them. `manifest.json` lists the available shards, row counts, latest
draw dates, and SHA-256 hashes used by clients to detect updated files.

Each results shard has a matching `meta_<game>_<year>.csv` containing:

```csv
date,jackpot,winners
2026-08-10,124014115.01,0
```

Jackpot and winner counts are kept separate so the core number files remain
small and stable. Metadata shards are also listed and hashed in the manifest.

## Expected date gaps

PCSO may officially suspend draws during Holy Week, Christmas, New Year, and
other holidays. These legitimate gaps differ between games because each game
has its own scheduled draw weekdays. Missing dates are therefore not, by
themselves, evidence of missing ingestion data.

## Historical records only

This dataset is provided only as a historical record. Lottery draws are
independent random events; past results do not reveal a predictable pattern and
cannot reliably predict future draws.
