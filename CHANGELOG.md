# Changelog — mirror of https://www.fuel-prices.eu/research/

This copy contains D1–D3 only. The entries below are the changelog of the source, https://www.fuel-prices.eu/research/data/CHANGELOG.md (entries about station-level data, D4, do not apply to this copy).

Versions are named `YYYY-MM` (a suffix such as `.1` marks a revision within the month). Within a month, files are rebuilt on schedule (D1 weekly, D2/D3 daily, D4 monthly); the version changes when
the method or the coverage changes. Every change of method is listed here.

## 2026-09.5 — licences of the sources, fuel codes, method notes (26 September 2026, night)

- **Australia, Türkiye and Sweden are excluded from D2 and D3 pending licence review.** Their rows are no longer in the files
  (Australia 371 D2 rows and 1,448 D3 rows; Türkiye 276 D2 rows and 22,632 D3 rows; Sweden 13,200 D2 rows, as of 26 September 2026). They may return in a later version once the terms of their sources are verified; the live pages of fuel-prices.eu are not affected.
- **United Kingdom:** `source_terms` now states the licence of the UK Fuel Finder data, the Open Government Licence v3.0, with the attribution statement it
  requires ("Contains public sector information licensed under the Open Government Licence v3.0"); it wrongly said "No licence published by the source".
- **Fuel codes no longer cross fuel families:** UK premium diesel is now `diesel_premium` (was `sp98`). New column **`fuel_family`**
  (`petrol`, `diesel`, `lpg`, `ethanol_e85`) in D2 and D3, for comparisons across markets. Figures unchanged.
- **D3:** new column `flag` = `few_stations` when a region-day rests on 3 to 9 stations.
- **Method notes** in the READMEs and CSV footers: the statistics are **unweighted** (arithmetic mean of the stations), and the snapshot time of
  each feed is given in Bucharest time (`date` = calendar day in Europe/Bucharest).
- The citation recommended for D1–D3 is now the Zenodo DOI 10.5281/zenodo.22978599. D4 files are unchanged and still carry version 2026-09.4.

## 2026-09.4 — spreadsheet-safe text cells in the CSV files (26 September 2026, evening)

- In the CSV and ZIP files, a text cell that begins with `=`, `+`, `-`, `@`, a tab or a carriage return now starts with an apostrophe (`'`),
  so that Excel or LibreOffice do not run it as a formula (OWASP "CSV injection"). Numbers, including negative ones, are never changed.
- It matters for D4 Spain, where some station brands are `-` or start with `+` (for example `+B Energias`). The Parquet files keep the raw text.
- No figure changed.

## 2026-09.3 — stations that left a feed are no longer carried forward (26 September 2026, night)

- **Rule.** A station price enters the daily snapshot only if fuel-prices.eu read it from the source feed in the 48 hours before
  the snapshot (France 6 hours from 24 September 2026, United Kingdom 168, Lithuania 96 hours). The anchor point on the day the source says the price was set is kept (it is real history).
  Why the exceptions: the UK importer moves its read time only when the price in EUR changes, so an unchanged price looks
  about 66 hours old on a Monday morning and about 114 hours old after Easter; Lithuania publishes on working days only.
  France is tighter: its feed has been re-read in full every 72 minutes since 23 September 2026, and stations often drop a fuel
  (out of stock, or SP95-E5 withdrawn); with 48 hours, 101 SP95 prices that were no longer in the feed still counted on 26 September
  (10th percentile 1.990 instead of about 2.12). For France, 48 hours applies up to 23 September 2026 (the feed was then read every 10–18 hours).
- **Before,** every price ever seen got a new daily row, so stations that had dropped out of a feed months earlier kept their last
  price in the history. Those copied rows were removed from the station histories (D2, D3 and D4 rebuilt from them):

  | market | rows removed |
  |---|---|
  | AT | 27,939 |
  | AU | 11,200 |
  | DK | 131 |
  | ES | 93,600 |
  | FR | 112,581 |
  | GB | 154 |
  | HR | 222 |
  | IT | 160,468 |
  | LT | 126 |
  | SI | 100 |

  Portugal and Andorra were cleaned too but are not in these files. Limitation: a station that left a feed and came back before
  26 September 2026 keeps the copied rows of its absence; they cannot be told apart from real prices after the fact.
- **Effect on 26 September 2026** (EUR per litre; old = version 2026-09.2, new = this version):

  | market | fuel | n old | n new | mean old | mean new | median old | median new | p10 old | p10 new | p90 old | p90 new |
  |---|---|---|---|---|---|---|---|---|---|---|---|
  | AT | Diesel | 2,298 | 1,412 | 2.1964 | 2.2319 | 2.2180 | 2.2290 | 2.0550 | 2.1820 | 2.2690 | 2.2838 |
  | AT | Super 95 (E10) | 2,085 | 1,332 | 1.9142 | 1.9332 | 1.9190 | 1.9290 | 1.8490 | 1.8890 | 1.9790 | 1.9878 |
  | ES | Diesel | 12,047 | 11,289 | 1.9164 | 1.9304 | 1.9590 | 1.9690 | 1.7490 | 1.7800 | 2.0490 | 2.0490 |
  | ES | LPG | 1,015 | 996 | 1.0940 | 1.0963 | 1.1250 | 1.1250 | 0.9390 | 0.9390 | 1.1890 | 1.1890 |
  | ES | Petrol 95 | 11,292 | 10,933 | 1.9201 | 1.9311 | 1.9690 | 1.9790 | 1.7651 | 1.7890 | 2.0540 | 2.0540 |
  | ES | Petrol 98 | 5,626 | 5,494 | 2.0814 | 2.0885 | 2.1390 | 2.1390 | 1.8590 | 1.8990 | 2.1990 | 2.1990 |
  | FR | Diesel | 9,919 | 9,031 | 2.3818 | 2.3961 | 2.3990 | 2.3990 | 2.2500 | 2.2500 | 2.4990 | 2.4990 |
  | FR | Petrol 95 (SP95-E10) | 8,044 | 7,127 | 2.1471 | 2.1659 | 2.1650 | 2.1720 | 1.9900 | 1.9900 | 2.2790 | 2.2810 |
  | FR | E85 (superethanol) | 4,085 | 3,894 | 0.8947 | 0.8953 | 0.8690 | 0.8690 | 0.8480 | 0.8490 | 0.9970 | 0.9970 |
  | FR | LPG | 1,643 | 1,505 | 1.0514 | 1.0498 | 1.0390 | 1.0390 | 0.9690 | 0.9690 | 1.1528 | 1.1512 |
  | FR | Petrol 95 (SP95, E5) | 3,583 | 2,783 | 2.1754 | 2.2221 | 2.2190 | 2.2330 | 1.9900 | 2.1300 | 2.2990 | 2.2990 |
  | FR | Petrol 98 (SP98) | 8,421 | 7,170 | 2.2313 | 2.2687 | 2.2690 | 2.2800 | 1.9900 | 1.9900 | 2.3790 | 2.3900 |
  | IT | Diesel | 22,104 | 21,135 | 2.3267 | 2.3403 | 2.3440 | 2.3480 | 2.2880 | 2.2980 | 2.3970 | 2.3980 |
  | IT | LPG | 4,740 | 4,568 | 0.7565 | 0.7564 | 0.7490 | 0.7490 | 0.6890 | 0.6890 | 0.8490 | 0.8490 |
  | IT | Petrol 95 | 22,032 | 21,064 | 2.1437 | 2.1569 | 2.1570 | 2.1590 | 2.1090 | 2.1190 | 2.1990 | 2.1990 |
  | IT | Petrol 98 | 1,374 | 1,303 | 2.2479 | 2.2634 | 2.2890 | 2.2960 | 1.9990 | 2.0800 | 2.3890 | 2.3890 |

- **D1:** the fixed conversion rate is applied from the day it was fixed: HRK 7.53450 from 12 July 2022 (3 January – 11 July 2022
  now use the ECB HRK reference rate of the bulletin date), BGN 1.95583 from 8 July 2025 (before: the ECB BGN rate, 1.9558).
  Only `eur_rate` and the national-currency columns of those weeks change; the EUR prices are the Commission's and are unchanged.
- **D2 market table** (README, /research/, `manifest.json` `market_list`): first day, last day and number of days now come from the
  same set of days (all published days, including `low_coverage`); the first day with national coverage is a separate column (`f_cov`).
- **D2 preview** on /research/: ranked in EUR only among markets with an ECB euro rate or a fixed parity, without Sweden's list prices.

## 2026-09.2 — ZIP downloads (26 September 2026, evening)

- Data unchanged. **Every CSV is now also published as a `.zip`** (one CSV inside, same content as the `.csv.gz`), because
  macOS Archive Utility cannot open the `.csv.gz` files ("Error 79": it mistakes the CSV for an mtree archive listing).
  On a Mac or PC, download the ZIP; `.csv.gz` and Parquet stay at the same URLs for scripts (pandas, R, Python).
- The gzip header of every `.csv.gz` now carries the final file name (`….csv`) instead of a temporary one (`….csv.tmp`).
  The decompressed content is byte-identical, so the SHA-256 of the `.csv.gz` files changed but the data did not.
- `manifest.json`: each file entry has a new `zip` key next to `csv` and `parquet`.

## 2026-09.1 — bulletin aligned with the Commission history file (26 September 2026, evening)

- **D1 now matches the European Commission's history file cell by cell**, and the build fails if a single cell differs
  (29,363 country-weeks and 2,170 weighted averages checked at build time). A weekly job re-aligns the last 52 weeks after each
  bulletin, so later revisions by the Commission reach the file within a week.
- **Corrected values** (27 cells revised by the Commission after first publication, which our archive had kept), in EUR/L, old → new:
  - DK 2025-12-29 diesel: 1.855 → 1.700
  - DK 2025-12-29 petrol: 1.922 → 1.885
  - HU 2025-12-29 diesel: 1.479 → 1.452
  - HU 2025-12-29 petrol: 1.448 → 1.423
  - RO 2026-01-05 diesel: 1.528 → 1.472
  - RO 2026-01-05 petrol: 1.489 → 1.424
  - DK 2026-02-16 diesel: 1.873 → 1.727
  - DK 2026-02-16 petrol: 1.962 → 1.911
  - HU 2026-03-16 diesel: 1.638 → 1.613
  - HU 2026-03-16 petrol: 1.537 → 1.534
  - DK 2026-04-06 diesel: 2.559 → 2.369
  - DK 2026-04-06 petrol: 2.323 → 2.272
  - BG 2026-04-20 diesel: 1.756 → 1.774
  - BG 2026-04-20 petrol: 1.470 → 1.478
  - NL 2026-05-11 diesel: 2.309 → 2.288
  - NL 2026-05-11 petrol: 2.341 → 2.378
  - EE 2026-06-01 diesel: 1.802 → 1.799
  - EE 2026-06-01 petrol: 1.812 → 1.785
  - BG 2026-06-08 diesel: 1.666 → 1.588
  - BG 2026-06-08 petrol: 1.530 → 1.518
  - NL 2026-07-06 diesel: 2.021 → 2.072
  - NL 2026-07-06 petrol: 2.203 → 2.245
  - RO 2026-07-06 diesel: 1.813 → 1.814
  - RO 2026-07-13 diesel: 1.806 → 1.800
  - RO 2026-07-13 petrol: 1.652 → 1.651
  - RO 2026-07-20 diesel: 1.888 → 1.821
  - RO 2026-07-20 petrol: 1.721 → 1.666
- **Rounding:** 1,604 older cells were 0.001 EUR/L too high (the import rounded twice: 1.2345 → 1.235); now rounded half-up once, like the Commission's EUR/1000 L ÷ 1000.
- **Added:** Spain 2013-04-08 (diesel 1.374), which was missing.
- **Portugal added** to D1 (Commission data, CC BY 4.0; 1,085 weeks). Portugal stays excluded from D2–D4 (its live source restricts reuse).
- **United Kingdom 2005–2020 added** from the Commission file (790 weeks), with a new column `in_eu` (false from 1 February 2020). The four empty
  UK weeks of 2026 were removed (they were not bulletin data).
- **Currencies:** Bulgaria is in EUR from the first bulletin of 2026 (was BGN until 2 March 2026); Croatia is in HRK until 2022 (was EUR);
  Slovenia, Cyprus, Malta, Slovakia, Estonia, Latvia and Lithuania carry their former currency before the euro. Fixed parities are used where they
  apply (BGN 1.95583; HRK 7.53450 in 2022; the irrevocable conversion rates from the day they were fixed); otherwise the ECB rate of the bulletin date.
- **D4:** implausible prices (placeholders such as 8.888, 4.999, 0.01) are removed with the site's price floor and the D2 rule; the count per file is in the D4 README.

## 2026-09 — metadata revision (26 September 2026, afternoon)

- D2/D3 data unchanged. The start date of each market in the D2 README, the market table on /research/ and `manifest.json` (`market_list[].f`)
  is now the **first day with national coverage** (no `low_coverage` flag), the same definition used on /press/ (records) and /news/.
  Changed: Austria 21 Jul → 22 Jul 2026, Italy 24 Jun → 25 Jun 2026, Australia 13 Jul → 3 Aug 2026 (the earlier days stay in the file, flagged `low_coverage`; see `f_any`).
- Wording: the national feeds are collected as often as each feed updates, from every 30 minutes to once a day (was: "several times a day").

## 2026-09 — first release (26 September 2026)

- D1 EU Weekly Oil Bulletin panel, 2005-01-03 to 2026-09-21, 26 countries with prices (Portugal excluded) and 4 empty UK weeks, plus the Commission's EU27 and euro-area weighted averages.
- D2 national daily statistics for 17 markets; D3 regional daily statistics for 7 countries; D4 station-level monthly files for France, Italy, Spain and Croatia.
- Excluded from all files: Portugal, Andorra. Germany appears only as bulletin rows in D1.
- Exchange rates: ECB euro reference rates (daily fixing of the date, or the last fixing before it). The bulletin exchange rates stored in our
  database were **not** used: for older weeks they are stored with only 3 decimals (e.g. HUF 0.002 EUR), which would distort national-currency prices.

### Known gaps

- Station-level daily snapshots cover the whole national network only from: AT 2026-07-22, DK 2026-07-10, ES 2026-06-26, FR 2026-06-06, GB 2026-06-26, HR 2026-08-05, IS 2025-06-02, IT 2026-06-25, LT 2026-04-08, RO 2026-05-21, SI 2026-08-05. Earlier isolated records are not published.
- Regional statistics for France, Italy and Spain start later than the national ones (ES 2026-06-26, FR 2026-06-06, IT 2026-06-24), because older snapshots refer to station
  identifiers that the feeds have since replaced.
- `source_updated_at` and `collected_at` (D4) exist from 26 September 2026 onward.
- Days on which a feed failed are missing (no interpolation); days with 25–50% of the usual stations carry `flag = low_coverage` in D2.
- France: the feed does not publish brands.
- Serbia, North Macedonia, Moldova: no ECB reference rate, so EUR columns are empty.
