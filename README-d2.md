# D2 — National daily fuel price statistics from live station feeds

> Copy of https://www.fuel-prices.eu/research/data/d2-national-daily/README.md , adapted to the files of this copy (sections "File formats" and "How to cite").

Version 2026-09.5 · data built 2026-09-26T15:58Z · https://www.fuel-prices.eu/research/

Daily statistics per market and fuel, computed by fuel-prices.eu from the official or statutory national fuel-price feeds it collects
as often as each national feed updates, from every 30 minutes to once a day. **Our statistics are CC BY 4.0. The underlying source data keep their own terms** (column `source_terms`).

| | |
|---|---|
| Period | 2021-09-02 to 2026-09-26 (each market starts on its own date, see table below) |
| Markets | 17 |
| Rows | 8,283 |
| Frequency | daily |
| Licence | fuel-prices.eu statistics: CC BY 4.0. Source data: see `source_terms` |

## Markets

| code | market | first day in the file | last day | days in the file | national coverage from | basis | source | source terms |
|---|---|---|---|---|---|---|---|---|
| AT | Austria | 2026-07-21 | 2026-09-26 | 68 | 2026-07-22 | stations | E-Control Spritpreisrechner | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| BA | Bosnia and Herzegovina | 2026-06-25 | 2026-09-26 | 94 | 2026-06-25 | single national price | National average retail price, Bosnia and Herzegovina | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| DK | Denmark | 2026-07-10 | 2026-09-26 | 78 | 2026-07-10 | stations | Per-station price APIs of the fuel brands (BEK 1351/2025 §16a) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| ES | Spain | 2026-06-26 | 2026-09-26 | 92 | 2026-06-26 | stations | Geoportal de Hidrocarburos, MITECO | Reuse conditions of Royal Decree 1495/2011 (credit the source and give the date of the last update) |
| FR | France | 2026-06-06 | 2026-09-26 | 105 | 2026-06-06 | stations | prix-carburants.gouv.fr | Licence Ouverte 2.0 (Etalab) |
| GB | United Kingdom | 2026-06-26 | 2026-09-26 | 93 | 2026-06-26 | stations | UK Fuel Finder open data scheme (Department for Energy Security and Net Zero) | Open Government Licence v3.0 (https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/); attribution: Contains public sector information licensed under the Open Government Licence v3.0 |
| GR | Greece | 2024-07-03 | 2026-09-24 | 170 | 2024-07-03 | prefecture averages published by the source | Fuel Price Observatory, Ministry of Development (prefecture averages) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| HR | Croatia | 2026-08-05 | 2026-09-26 | 53 | 2026-08-05 | stations | Ministry of Economy (MINGO), mzoe-gor.hr | Open data of the Ministry of Economy (MINGO), attribution required |
| IS | Iceland | 2025-06-02 | 2026-09-26 | 149 | 2025-06-02 | stations | Gasvaktin (gasvaktin.is) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| IT | Italy | 2026-06-24 | 2026-09-26 | 95 | 2026-06-25 | stations | Osservaprezzi Carburanti, MIMIT | Italian Open Data License 2.0 (IODL 2.0) |
| LT | Lithuania | 2026-04-08 | 2026-09-25 | 120 | 2026-04-08 | stations | Lietuvos energetikos agentura (LEA, ena.lt) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| MD | Moldova | 2021-09-02 | 2026-09-25 | 1282 | 2021-09-02 | single national price | ANRE (anre.md) national reference price | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| ME | Montenegro | 2026-06-25 | 2026-09-26 | 94 | 2026-06-25 | single national price | Government of Montenegro regulated maximum price | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| MK | North Macedonia | 2026-06-25 | 2026-09-26 | 94 | 2026-06-25 | single national price | Energy Regulatory Commission (ERC) maximum retail price | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| RO | Romania | 2026-05-21 | 2026-09-26 | 128 | 2026-05-21 | stations | Monitorul Prețurilor Carburanților (Consiliul Concurenței) | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| RS | Serbia | 2026-06-24 | 2026-09-26 | 95 | 2026-06-24 | single national price | Ministry of Internal and Foreign Trade, national maximum retail price | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| SI | Slovenia | 2026-08-05 | 2026-09-26 | 53 | 2026-08-05 | stations | goriva.si (Ministry of Economy) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |

**First day, last day and days** are counted on the same set: every day published in the file, including days flagged `low_coverage`, so `days` ≤ last − first + 1 (a smaller number means days without data). **National coverage from** = the first day on which `n` reached 50% of the market's usual number of stations (no `low_coverage` flag); the same start date is used on /press/ (records) and /news/.
**Excluded:** Portugal and Andorra (the Portuguese source forbids commercial use; the Andorran source reserves all rights). Germany is not part of the live-feed datasets.
**Australia, Türkiye and Sweden are excluded pending licence review** (since version 2026-09.5); they may return in a later version once the terms of their sources are verified.
Single-price markets (MD, RS, MK, ME, BA) publish one national reference or maximum price per day: `mean` and `median` equal that price, `p10`/`p90` are empty.

## Columns

| column | meaning |
|---|---|
| date | calendar day (ISO 8601) of the daily snapshot |
| country_code, country_name | market (ISO 3166-1 alpha-2) |
| fuel | fuel code as used by fuel-prices.eu (`sp95`, `e10`, `e5`, `sp98`, `petrol95`, `petrol_premium`, `diesel`, `diesel_premium`, `hvo`, `gpl`, `lpg`, `e85`). A code never crosses fuel families (since 2026-09.5: UK premium diesel = `diesel_premium`, no longer `sp98`), but the exact grade behind a code can differ between markets — read `fuel_label` |
| fuel_family | `petrol`, `diesel`, `lpg` or `ethanol_e85` — filter on this column to compare markets (`gpl` and `lpg` are both `lpg`; `sp95`, `e10` and `petrol95` are all `petrol`) |
| fuel_label | English name of the fuel in that market |
| basis | what one observation is: `stations`, `prefecture averages published by the source` or `single national price` |
| n | number of observations (stations, prefectures or national prices) after cleaning |
| n_excluded | observations removed as implausible (below 0.5× or above 2× the day's median for that market and fuel) |
| share_changed_7d | share of stations whose price changed at least once in the previous 7 days of our snapshots — a staleness indicator (stations only) |
| mean_eur, median_eur, p10_eur, p90_eur | statistics in EUR per litre |
| currency | national currency |
| mean_local … p90_local | the same statistics in national currency per litre |
| eur_rate | units of national currency per 1 EUR used for the conversion |
| eur_rate_date | date of the ECB fixing used (the day itself, or the last fixing before it) |
| eur_rate_source | `ECB euro foreign exchange reference rate`, `fixed parity` (BAM) or none (RSD, MKD, MDL have no ECB rate: EUR columns are empty; the live pages of fuel-prices.eu show these markets in EUR with a commercial exchange rate, which is not used in this file) |
| flag | `low_coverage` when n is between 25% and 50% of the market's usual number of stations |
| source | the national feed |
| source_terms | the terms of the source data, as verified by fuel-prices.eu |

## Method

- **Unweighted statistics.** `mean` is the plain arithmetic mean of the observations of the day: every station counts once, whatever it sells
  (no weighting by volume or by region). Greece: mean of the prefecture averages published by the source (one per prefecture, unweighted).
  `median`, `p10` and `p90` are taken over the same observations. By contrast, the D1 EU27 and euro-area averages are the Commission's
  **consumption-weighted** averages.
- **Time of the snapshot and time zone.** `date` is a calendar day in Bucharest time (Europe/Bucharest, UTC+2 in winter, UTC+3 in summer).
  Station feeds are snapshotted once a day at these times, Bucharest time: France 09:35, United Kingdom 09:40, Spain 09:43, Italy 09:46,
  Denmark 09:49, Iceland 09:50, Austria 09:56, Croatia 09:58, Slovenia 10:00, Lithuania 13:05 (working days only). Romania: the last price
  read on that day (the feed is read every 2 hours). Greece: the day of the bulletin published by the source. Single-price markets: the day
  the national price was collected.
- **Daily snapshot.** Each day we keep, for every station and fuel, the price the source lists as current. Station feeds are stored in EUR at the ECB rate of the collection day (GB, DK, IS); national-currency values for those markets are reconstructed with the ECB rate of the day (differences of ±0.001 are rounding). Romania and the single-price markets are stored in national currency and converted to EUR.
- **Freshness.** A station price counts on a day only if fuel-prices.eu read it from the source feed in the 48 hours before that day's snapshot (France 6 hours from 24 September 2026, United Kingdom 168, Lithuania 96 hours). A station that leaves a feed therefore drops out of the statistics within that window; until version 2026-09.3 its last price was carried forward day after day, which pulled averages and the 10th percentile down in France, Italy, Spain and Austria (see the changelog). The live pages of fuel-prices.eu additionally drop prices whose source timestamp is older than 7 days, so their averages can still differ from this file by a few cents. Use `share_changed_7d` to judge how recently stations changed their prices.
- **Cleaning.** Prices ≤ 0 and prices outside 0.5×–2× of the day's median (market, fuel) are removed and counted in `n_excluded`. Duplicates cannot occur: the snapshot keeps one price per station, fuel and day.
- **Coverage.** A day is published only if `n` reaches 25% of the market's usual number of stations (median of the last 60 days); earlier isolated records (1–5 stations) are not national statistics and are left out. Missing days are simply absent (no interpolation).
- **Percentiles** are linear-interpolated (pandas `quantile`, method `linear`).
- CNG and LNG (sold per kg) are not in D2/D3; they are in the Italian station files (D4).

## Attribution required by the sources

- **United Kingdom** (UK Fuel Finder, Department for Energy Security and Net Zero): *Contains public sector information licensed under the
  Open Government Licence v3.0* — https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/ . Keep this statement when you reuse the UK rows.
- France, Italy, Spain and Croatia: credit the source named in `source` (Spain: also the date of the last update, which is the `date` column).
- All sources and their terms, with the date we checked them: `source_terms` and the table above.

## File formats

This repository holds **samples only** (`sample/*.csv`, a few hundred rows of each table). The full files (`.zip`, `.csv.gz`, `.parquet`) are on https://www.fuel-prices.eu/research/data/ and, as `.zip` + `.parquet`, in the Zenodo record (DOI in the main README).

## How to cite

> fuel-prices.eu (2026). *European fuel prices: EU Weekly Oil Bulletin panel (2005–) and daily national and regional averages* (Version 2026-09.5) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22978599

This file describes one table of that record. Please cite the DOI, so that citations are not split between copies.

Short credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

A `CITATION.cff` file is included in this copy.
