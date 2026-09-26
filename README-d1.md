# D1 — EU Weekly Oil Bulletin, weekly panel

> Copy of https://www.fuel-prices.eu/research/data/d1-eu-weekly-bulletin/README.md , adapted to the files of this copy (sections "File formats" and "How to cite").

Version 2026-09.5 · data built 2026-09-26T15:58Z · https://www.fuel-prices.eu/research/

National average consumer prices of Euro-super 95 petrol and automotive diesel, **all taxes included**, as reported every week
by each EU member state to the European Commission (DG ENER) in the Weekly Oil Bulletin, compiled into one panel by fuel-prices.eu.
Every cell is checked against the Commission's history file (`Weekly_Oil_Bulletin_Prices_History`) when the file is built;
a single difference stops the build. Weeks the Commission revises after publication are updated in the next weekly run.

| | |
|---|---|
| Period | 2005-01-03 to 2026-09-21 (bulletin price dates, Mondays) |
| Countries | 27 EU member states (AT, BE, BG, CY, CZ, DE, DK, EE, ES, FI, FR, GR, HR, HU, IE, IT, LT, LU, LV, MT, NL, PL, PT, RO, SE, SI, SK) + United Kingdom (2005 to 2020, `in_eu` = false from 1 February 2020) |
| Rows | 29,363 |
| Frequency | weekly |
| Licence | CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/ (European Commission, Decision 2011/833/EU) |
| Attribution | "EU Weekly Oil Bulletin, European Commission; compiled by fuel-prices.eu" |

## Files

- `fp-d1-eu-weekly-panel.zip` / `.csv.gz` / `.parquet` (on the site; samples in `sample/`) — one row per country and week.
- `fp-d1-eu-weighted-average.zip` / `.csv.gz` / `.parquet` (on the site; samples in `sample/`) — the Commission's own consumption-weighted averages for the EU27 and the euro area (2005-01-03 to 2026-09-21, 2,170 rows).

## Columns — `fp-d1-eu-weekly-panel`

| column | type | meaning |
|---|---|---|
| country_code | text | ISO 3166-1 alpha-2 as used by the bulletin (`UK` = United Kingdom) |
| country_name | text | English name |
| week | date (ISO 8601) | bulletin price date (Monday of the reference week) |
| in_eu | boolean | the country was an EU member state that week (false only for the United Kingdom from 1 February 2020) |
| euro95_eur_l | number | Euro-super 95 petrol, EUR per litre, all taxes |
| diesel_eur_l | number | automotive diesel, EUR per litre, all taxes |
| currency | text | national currency of that week (ISO 4217). Euro changeovers: SI 1 Jan 2007 (SIT), CY and MT 1 Jan 2008 (CYP, MTL), SK 1 Jan 2009 (SKK), EE 1 Jan 2011 (EEK), LV 1 Jan 2014 (LVL), LT 1 Jan 2015 (LTL), HR 1 Jan 2023 (HRK), BG 1 Jan 2026 (BGN) |
| eur_rate | number | units of national currency per 1 EUR. A fixed parity from the day the irrevocable conversion rate was fixed: BGN 1.95583 from 8 Jul 2025, HRK 7.53450 from 12 Jul 2022, SIT 239.640 from 11 Jul 2006, CYP 0.585274 and MTL 0.429300 from 10 Jul 2007, SKK 30.1260 from 8 Jul 2008, EEK 15.6466 from 13 Jul 2010, LVL 0.702804 from 9 Jul 2013, LTL 3.45280 from 23 Jul 2014 (before those days, and in all other cases: the ECB euro reference rate of the bulletin date, or the last fixing before it — the rate the Commission itself uses). 1 for EUR |
| eur_rate_date | date | date of the ECB fixing used (empty for EUR; `fixed parity` where a parity applies) |
| euro95_local_l, diesel_local_l | number | national-currency price per litre = EUR price × eur_rate (rounded to 3 decimals) |

## Columns — `fp-d1-eu-weighted-average`

| column | meaning |
|---|---|
| scope | `EU27` or `EURO_AREA` |
| week | bulletin price date |
| euro95_eur_l, diesel_eur_l | Commission weighted average, EUR per litre, all taxes (the bulletin publishes EUR per 1000 L; divided by 1000) |

## Changes made by fuel-prices.eu (CC BY 4.0 requires us to indicate them)

- Weeks for which the Commission file has no price for a country are **not in the file** (no row; for example Croatia before 2013, Bulgaria and Romania before 2008, the United Kingdom after 2020). Where one of the two fuels is missing in a week, that cell is **empty, never 0**.
- The Commission publishes EUR per 1000 L; we divide by 1000 and round half-up to 3 decimals (EUR per litre).
- National-currency prices are **derived** with `eur_rate` (see above); the bulletin's own national-currency tables can differ in the last decimal.
- The **United Kingdom** (2005-01-03 to 2020-12-21) is taken directly from the Commission file. It left the EU on 31 January 2020; the Commission kept
  publishing UK prices during the transition period, so the last 46 weeks have `in_eu` = false. These UK rows are not used in the EU averages
  shown on fuel-prices.eu.
- **Portugal** is included: these are Commission data under CC BY 4.0. (Portugal is excluded only from the live-feed datasets D2–D4, whose Portuguese source restricts reuse.)
- Norway is not in the bulletin and is not in this file.

## File formats

This repository holds **samples only** (`sample/*.csv`, a few hundred rows of each table). The full files (`.zip`, `.csv.gz`, `.parquet`) are on https://www.fuel-prices.eu/research/data/ and, as `.zip` + `.parquet`, in the Zenodo record (DOI in the main README).

## How to cite

> fuel-prices.eu (2026). *European fuel prices: EU Weekly Oil Bulletin panel (2005–) and daily national and regional averages* (Version 2026-09.5) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22978599

This file describes one table of that record. Please cite the DOI, so that citations are not split between copies.

Short credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

A `CITATION.cff` file is included in this copy.
