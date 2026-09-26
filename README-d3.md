# D3 — Regional daily fuel price statistics

> Copy of https://www.fuel-prices.eu/research/data/d3-regional-daily/README.md , adapted to the files of this copy (sections "File formats" and "How to cite").

Version 2026-09.5 · data built 2026-09-26T15:58Z · https://www.fuel-prices.eu/research/

The D2 statistics per region, where the source lets us place a station in a region. Same method (unweighted statistics, the same daily
snapshot times in Bucharest time), same exclusions (Australia and Türkiye are excluded pending licence review since version 2026-09.5) and the
same column meanings as D2 (see that README), plus `region_type`, `region` and `flag` (`few_stations` = 3 to 9 stations that day: the regional
figure rests on very few prices). **Our statistics are CC BY 4.0; the source data keep their terms.**

| | |
|---|---|
| Period | 2024-07-03 to 2026-09-26 |
| Countries | 7 |
| Regions | 408 |
| Rows | 195,485 |
| Frequency | daily |

## Regions

| code | region type | regions | first day | how the region is assigned |
|---|---|---|---|---|
| ES | province | 52 | 2026-06-26 | province from the postal code (INE code) |
| FR | département | 96 | 2026-06-06 | département from the station postal code |
| GB | region / nation | 4 | 2026-06-26 | nation as published by the feed |
| GR | prefecture (regional unit) | 51 | 2024-07-03 | published by the source per prefecture |
| IT | province | 106 | 2026-06-24 | province (sigla) from MIMIT station register |
| LT | municipality | 57 | 2026-04-08 | municipality as published by the feed |
| RO | county (județ) | 42 | 2026-05-21 | county from the station municipality (SIRUTA), nearest locality as fallback |

A region-day is published only with at least **3 stations** (station markets). Greece: the source publishes one average per prefecture (`n` empty).
Other markets (AT, DK, HR, IS, SI and the single-price markets) have no reliable regional key in the feeds and are only in D2.

## File formats

This repository holds **samples only** (`sample/*.csv`, a few hundred rows of each table). The full files (`.zip`, `.csv.gz`, `.parquet`) are on https://www.fuel-prices.eu/research/data/ and, as `.zip` + `.parquet`, in the Zenodo record (DOI in the main README).

## How to cite

> fuel-prices.eu (2026). *European fuel prices: EU Weekly Oil Bulletin panel (2005–) and daily national and regional averages* (Version 2026-09.5) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22978599

This file describes one table of that record. Please cite the DOI, so that citations are not split between copies.

Short credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

A `CITATION.cff` file is included in this copy.
