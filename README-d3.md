# D3 — Regional daily fuel price statistics

> Copy of https://www.fuel-prices.eu/research/data/d3-regional-daily/README.md , adapted to the files of this copy (sections "File formats" and "How to cite").

Version 2026-11.3 · data built 2026-11-12T04:40Z · https://www.fuel-prices.eu/research/

**Version note (2026-11.2):** UK and Romania regional aggregates removed (source licence review, 8 Nov 2026). Their national daily
statistics remain in D2. Details in the changelog.

The D2 statistics per region, where the source lets us place a station in a region. Same method (unweighted statistics, the same daily
snapshot times in Bucharest time), same exclusions (listed in the D2 README) and the
same column meanings as D2 (see that README), plus `region_type`, `region` and `flag` (`few_stations` = 3 to 9 stations that day: the regional
figure rests on very few prices). **Our statistics are CC BY 4.0; the source data keep their terms.**

| | |
|---|---|
| Period | 2024-07-03 to 2026-11-11 |
| Countries | 4 |
| Regions | 305 |
| Rows | 208,528 |
| Frequency | daily |

## Regions

| code | region type | regions | first day | how the region is assigned |
|---|---|---|---|---|
| ES | province | 52 | 2026-06-26 | province from the postal code (INE code) |
| FR | département | 96 | 2026-06-06 | département from the station postal code |
| GR | prefecture (regional unit) | 51 | 2024-07-03 | published by the source per prefecture |
| IT | province | 106 | 2026-06-24 | province (sigla) from MIMIT station register |

A region-day is published only with at least **3 stations** (station markets). Greece: the source publishes one average per prefecture (`n` empty).
Other markets (DK, HR, IS, SI) have no reliable regional key in the feeds and are only in D2. The United Kingdom (nations) and Romania
(counties) are only in D2 from version 2026-11.2: their regional aggregates were removed from D3 on 8 November 2026 (source licence review).
Lithuania (municipalities) was removed from D2 and D3 in version 2026-09.9 and withdrawn from fuel-prices.eu on 1 October 2026 (reason in the D2 README).

**Source terms.** Every row states the terms of its source in `source_terms`; the sources and their terms are listed in the D2 README.

## File formats

This repository holds **samples only** (`sample/*.csv`, a few hundred rows of each table). The full files (`.zip`, `.csv.gz`, `.parquet`) are on https://www.fuel-prices.eu/research/data/ and, as `.zip` + `.parquet`, in the Zenodo record (DOI in the main README).

## How to cite

> fuel-prices.eu (2026). *European fuel prices: EU Weekly Oil Bulletin panel (2005–) and daily national and regional averages* (Version 2026-11.3) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.23875812

This file describes one table of that record. Please cite the DOI, so that citations are not split between copies.

Short credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

A `CITATION.cff` file is included in this copy.
