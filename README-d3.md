# D3 — Regional daily fuel price statistics

> Copy of https://www.fuel-prices.eu/research/data/d3-regional-daily/README.md . Links to `CITATION.cff` "in the parent folder" refer to the site; this copy has its own `CITATION.cff` with the Zenodo DOI.

Version 2026-09.4 · built 2026-09-26T15:03Z · https://www.fuel-prices.eu/research/

The D2 statistics per region, where the source lets us place a station in a region. Same method, same exclusions and the same column
meanings as D2 (see that README), plus `region_type` and `region`. **Our statistics are CC BY 4.0; the source data keep their terms.**

| | |
|---|---|
| Period | 2024-07-03 to 2026-09-26 |
| Countries | 9 |
| Regions | 495 |
| Rows | 219,565 |
| Frequency | daily |

## Regions

| code | region type | regions | first day | how the region is assigned |
|---|---|---|---|---|
| AU | state/territory | 5 | 2026-07-13 | state of the feed |
| ES | province | 52 | 2026-06-26 | province from the postal code (INE code) |
| FR | département | 96 | 2026-06-06 | département from the station postal code |
| GB | region / nation | 4 | 2026-06-26 | nation as published by the feed |
| GR | prefecture (regional unit) | 51 | 2024-07-03 | published by the source per prefecture |
| IT | province | 106 | 2026-06-24 | province (sigla) from MIMIT station register |
| LT | municipality | 57 | 2026-04-08 | municipality as published by the feed |
| RO | county (județ) | 42 | 2026-05-21 | county from the station municipality (SIRUTA), nearest locality as fallback |
| TR | province | 82 | 2026-06-24 | published by the source per province |

A region-day is published only with at least **3 stations** (station markets). Greece: the source publishes one average per prefecture (`n` empty).
Türkiye: one price per province (`n` empty). Other markets (AT, DK, HR, IS, SI and the single-price markets) have no reliable regional key in the feeds and are only in D2.

## File formats

Every table comes in three formats with identical content:

- **`.zip`** — one CSV inside; opens with a double-click on macOS and Windows. **On a Mac or PC, download the ZIP.**
- **`.csv.gz`** — the same CSV, gzip-compressed, for scripts (pandas, R, Python): `pandas.read_csv(url, comment="#")` reads it directly.
  macOS Archive Utility cannot open these files (it reports "Error 79"); use the ZIP instead.
- **`.parquet`** — for scripts; column types and the source notes are in the file metadata.

The CSV ends with a few comment lines starting with `#` that name the source.

In the CSV and ZIP only, a text cell that begins with `=`, `+`, `-`, `@`, a tab or a carriage return starts with an apostrophe (`'`),
so that spreadsheet software does not run it as a formula (OWASP "CSV injection"). Numbers are never changed. Example: the Spanish
brand `+B Energias` is `'+B Energias` in the CSV and `+B Energias` in the Parquet; strip a leading `'` if you need the raw text.

Download each file once; automated bulk downloading is rate-limited (bursts of more than 60 files in 10 minutes are blocked for an hour).
For bulk or scheduled access, write to hi@fuel-prices.eu.

## How to cite

> fuel-prices.eu (2026). *Regional daily fuel price statistics* (Version 2026-09.4) [Data set]. https://www.fuel-prices.eu/research/

Short credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

A `CITATION.cff` file is in the parent folder: https://www.fuel-prices.eu/research/data/CITATION.cff

