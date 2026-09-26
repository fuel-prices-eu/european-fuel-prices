# D2 — National daily fuel price statistics from live station feeds

> Copy of https://www.fuel-prices.eu/research/data/d2-national-daily/README.md . Links to `CITATION.cff` "in the parent folder" refer to the site; this copy has its own `CITATION.cff` with the Zenodo DOI.

Version 2026-09.4 · built 2026-09-26T15:03Z · https://www.fuel-prices.eu/research/

Daily statistics per market and fuel, computed by fuel-prices.eu from the official or statutory national fuel-price feeds it collects
as often as each national feed updates, from every 30 minutes to once a day. **Our statistics are CC BY 4.0. The underlying source data keep their own terms** (column `source_terms`).

| | |
|---|---|
| Period | 2008-09-01 to 2026-09-26 (each market starts on its own date, see table below) |
| Markets | 20 |
| Rows | 22,130 |
| Frequency | daily |
| Licence | fuel-prices.eu statistics: CC BY 4.0. Source data: see `source_terms` |

## Markets

| code | market | first day in the file | last day | days in the file | national coverage from | basis | source | source terms |
|---|---|---|---|---|---|---|---|---|
| AT | Austria | 2026-07-21 | 2026-09-26 | 68 | 2026-07-22 | stations | E-Control Spritpreisrechner | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| AU | Australia (NSW, VIC, WA, TAS, NT feeds) | 2026-07-13 | 2026-09-26 | 76 | 2026-08-03 | stations | State fuel-price schemes: NSW FuelCheck, VIC Servo Saver, WA FuelWatch, TAS FuelCheck, NT MyFuel | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| BA | Bosnia and Herzegovina | 2026-06-25 | 2026-09-26 | 94 | 2026-06-25 | single national price | National average retail price, Bosnia and Herzegovina | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| DK | Denmark | 2026-07-10 | 2026-09-26 | 78 | 2026-07-10 | stations | Per-station price APIs of the fuel brands (BEK 1351/2025 §16a) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| ES | Spain | 2026-06-26 | 2026-09-26 | 92 | 2026-06-26 | stations | Geoportal de Hidrocarburos, MITECO | Reuse conditions of Royal Decree 1495/2011 (credit the source and give the date of the last update) |
| FR | France | 2026-06-06 | 2026-09-26 | 105 | 2026-06-06 | stations | prix-carburants.gouv.fr | Licence Ouverte 2.0 (Etalab) |
| GB | United Kingdom | 2026-06-26 | 2026-09-26 | 93 | 2026-06-26 | stations | UK Fuel Finder open data scheme | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
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
| SE | Sweden (chain LIST prices) | 2008-09-01 | 2026-09-26 | 6600 | 2008-09-01 | chain list prices | List prices published by the fuel chains (Preem, Circle K) | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |
| SI | Slovenia | 2026-08-05 | 2026-09-26 | 53 | 2026-08-05 | stations | goriva.si (Ministry of Economy) | No licence published by the source; fuel-prices.eu publishes only its own aggregate statistics |
| TR | Türkiye | 2026-06-24 | 2026-09-26 | 92 | 2026-06-24 | province prices | Petrol Ofisi province price lists | Licence not verified by fuel-prices.eu; fuel-prices.eu publishes only its own aggregate statistics |

**First day, last day and days** are counted on the same set: every day published in the file, including days flagged `low_coverage`, so `days` ≤ last − first + 1 (a smaller number means days without data). **National coverage from** = the first day on which `n` reached 50% of the market's usual number of stations (no `low_coverage` flag); the same start date is used on /press/ (records) and /news/.
**Excluded:** Portugal and Andorra (the Portuguese source forbids commercial use; the Andorran source reserves all rights). Germany is not part of the live-feed datasets.
**Sweden** contains the chains' published **list prices** (Preem since 2008, Circle K since September 2026), not pump prices.
Single-price markets (MD, RS, MK, ME, BA) publish one national reference or maximum price per day: `mean` and `median` equal that price, `p10`/`p90` are empty.

## Columns

| column | meaning |
|---|---|
| date | calendar day (ISO 8601) of the daily snapshot |
| country_code, country_name | market (ISO 3166-1 alpha-2) |
| fuel | fuel code as used by fuel-prices.eu (`sp95`, `e10`, `e5`, `sp98`, `diesel`, `gpl`, `e85`, `hvo`, `petrol95`, `petrol_premium`, `diesel_premium`, `lpg`) — **the meaning of a code depends on the market; always read `fuel_label`** (e.g. in the UK `sp98` = premium diesel; in Australia `sp95` = unleaded 91) |
| fuel_label | English name of the fuel in that market |
| basis | what one observation is: `stations`, `province prices`, `prefecture averages published by the source`, `single national price`, `chain list prices` |
| n | number of observations (stations, provinces, prefectures or chains) after cleaning |
| n_excluded | observations removed as implausible (below 0.5× or above 2× the day's median for that market and fuel) |
| share_changed_7d | share of stations whose price changed at least once in the previous 7 days of our snapshots — a staleness indicator (stations only) |
| mean_eur, median_eur, p10_eur, p90_eur | statistics in EUR per litre |
| currency | national currency |
| mean_local … p90_local | the same statistics in national currency per litre |
| eur_rate | units of national currency per 1 EUR used for the conversion |
| eur_rate_date | date of the ECB fixing used (the day itself, or the last fixing before it) |
| eur_rate_source | `ECB euro foreign exchange reference rate`, `fixed parity` (BAM) or none (RSD, MKD, MDL have no ECB rate: EUR columns are empty) |
| flag | `low_coverage` when n is between 25% and 50% of the market's usual number of stations |
| source | the national feed |
| source_terms | the terms of the source data, as verified by fuel-prices.eu |

## Method

- **Daily snapshot.** Each day we keep, for every station and fuel, the price the source lists as current. Station feeds are stored in EUR at the ECB rate of the collection day (GB, DK, IS, AU); national-currency values for those markets are reconstructed with the ECB rate of the day (differences of ±0.001 are rounding). Romania, Türkiye and the single-price markets are stored in national currency and converted to EUR.
- **Freshness.** A station price counts on a day only if fuel-prices.eu read it from the source feed in the 48 hours before that day's snapshot (France 6 hours from 24 September 2026, United Kingdom 168, Lithuania 96 hours). A station that leaves a feed therefore drops out of the statistics within that window; until version 2026-09.3 its last price was carried forward day after day, which pulled averages and the 10th percentile down in France, Italy, Spain and Austria (see the changelog). The live pages of fuel-prices.eu additionally drop prices whose source timestamp is older than 7 days, so their averages can still differ from this file by a few cents. Use `share_changed_7d` to judge how recently stations changed their prices.
- **Cleaning.** Prices ≤ 0 and prices outside 0.5×–2× of the day's median (market, fuel) are removed and counted in `n_excluded`. Duplicates cannot occur: the snapshot keeps one price per station, fuel and day.
- **Coverage.** A day is published only if `n` reaches 25% of the market's usual number of stations (median of the last 60 days); earlier isolated records (1–5 stations) are not national statistics and are left out. Missing days are simply absent (no interpolation).
- **Percentiles** are linear-interpolated (pandas `quantile`, method `linear`).
- CNG and LNG (sold per kg) are not in D2/D3; they are in the Italian station files (D4).

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

> fuel-prices.eu (2026). *National daily fuel price statistics* (Version 2026-09.4) [Data set]. https://www.fuel-prices.eu/research/

Short credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

A `CITATION.cff` file is in the parent folder: https://www.fuel-prices.eu/research/data/CITATION.cff

