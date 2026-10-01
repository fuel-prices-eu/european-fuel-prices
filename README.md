# European fuel prices: EU Weekly Oil Bulletin panel (2005–) and daily national and regional averages

Source: fuel-prices.eu — https://www.fuel-prices.eu/research/

DOI: [10.5281/zenodo.22978599](https://doi.org/10.5281/zenodo.22978599) (this version) · all versions: [10.5281/zenodo.22978598](https://doi.org/10.5281/zenodo.22978598)

This repository holds the documentation and small samples; it **supplements** (IsSupplementTo) the Zenodo record `10.5281/zenodo.22978599`, which holds the full files. Please cite the DOI, not this repository.

Free fuel price data for research from [fuel-prices.eu](https://www.fuel-prices.eu/research/): the European Commission's Weekly Oil Bulletin as one weekly panel since 2005 (D1), and daily national (D2) and regional (D3) statistics of pump prices computed from official national station feeds. Version **2026-10.1**, documentation built 2026-10-01T18:00Z (the build time of each table is in its README). The same files are published on https://www.fuel-prices.eu/research/ (with station-level data, D4, which is not included here).

## Data sets

| set | content | period | rows | licence |
|---|---|---|---|---|
| D1 | EU Weekly Oil Bulletin panel: weekly national average prices of Euro-super 95 and diesel, all taxes included, 27 EU member states + United Kingdom (2005–2020) | 2005-01-03 to 2026-09-28 | 29,390 | CC BY 4.0 (European Commission data) |
| D1 | EU27 and euro-area weighted averages (European Commission) | 2005-01-03 to 2026-09-28 | 2,172 | CC BY 4.0 (European Commission data) |
| D2 | Daily national statistics (mean, median, p10, p90) from official national fuel-price feeds, 11 markets | 2024-07-03 to 2026-10-01 | 4,340 | our statistics CC BY 4.0; source data keep their own terms (column `source_terms`) |
| D3 | The same daily statistics per region, 351 regions in 6 countries | 2024-07-03 to 2026-10-01 | 182,615 | our statistics CC BY 4.0; source data keep their own terms (column `source_terms`) |

## Files

| table | Parquet | CSV |
|---|---|---|
| D1 EU Weekly Oil Bulletin panel | [fp-d1-eu-weekly-panel.parquet](https://www.fuel-prices.eu/research/data/d1-eu-weekly-bulletin/fp-d1-eu-weekly-panel.parquet) | [fp-d1-eu-weekly-panel.zip](https://www.fuel-prices.eu/research/data/d1-eu-weekly-bulletin/fp-d1-eu-weekly-panel.zip) · sample: `sample/fp-d1-eu-weekly-panel_sample.csv` |
| D1 EU27 and euro-area weighted averages | [fp-d1-eu-weighted-average.parquet](https://www.fuel-prices.eu/research/data/d1-eu-weekly-bulletin/fp-d1-eu-weighted-average.parquet) | [fp-d1-eu-weighted-average.zip](https://www.fuel-prices.eu/research/data/d1-eu-weekly-bulletin/fp-d1-eu-weighted-average.zip) · sample: `sample/fp-d1-eu-weighted-average_sample.csv` |
| D2 national daily statistics | [fp-d2-national-daily.parquet](https://www.fuel-prices.eu/research/data/d2-national-daily/fp-d2-national-daily.parquet) | [fp-d2-national-daily.zip](https://www.fuel-prices.eu/research/data/d2-national-daily/fp-d2-national-daily.zip) · sample: `sample/fp-d2-national-daily_sample.csv` |
| D3 regional daily statistics | [fp-d3-regional-daily.parquet](https://www.fuel-prices.eu/research/data/d3-regional-daily/fp-d3-regional-daily.parquet) | [fp-d3-regional-daily.zip](https://www.fuel-prices.eu/research/data/d3-regional-daily/fp-d3-regional-daily.zip) · sample: `sample/fp-d3-regional-daily_sample.csv` |

This repository holds only documentation and samples. Full files: the links above (fuel-prices.eu) and the Zenodo record (DOI above). Integrity: SHA-256 of every file on the site in https://www.fuel-prices.eu/research/data/checksums.txt

Each table comes as CSV and Parquet with identical content. The CSV ends with a few comment lines starting with `#` that name the source: `pandas.read_csv(path, comment="#")` skips them.

## Method in short

- **D1** comes from the European Commission. The EU27 and euro-area averages in `d1_eu_weighted_average` are the Commission's **consumption-weighted** averages.
- **D2 and D3 are unweighted**: `mean` is the arithmetic mean of the station prices of the day (every station counts once; Greece: mean of the prefecture averages published by the source), `median`, `p10`, `p90` over the same observations.
- **Time:** `date` is a calendar day in Bucharest time (Europe/Bucharest, UTC+2/UTC+3). Station feeds are snapshotted once a day between 09:35 and 10:00 Bucharest time; Romania = last price read that day; Greece = day of the source bulletin. Details per market: `README-d2.md`.
- **Fuels:** filter on `fuel_family` (`petrol`, `diesel`, `lpg`, `ethanol_e85`) to compare markets; `fuel_label` names the exact grade.

## Licence and attribution

- **D1** (panel and weighted averages): *EU Weekly Oil Bulletin, European Commission; compiled by fuel-prices.eu.* Commission data, reused under CC BY 4.0 (Commission Decision 2011/833/EU, legal notice https://commission.europa.eu/legal-notice_en). The changes made by fuel-prices.eu are listed in the D1 README.
- **D2 and D3**: statistics computed by fuel-prices.eu, licensed CC BY 4.0. The underlying national source data keep their own terms, stated on every row in the column `source_terms` and in the D2 README.
- **United Kingdom rows of D2 and D3** (UK Fuel Finder, Department for Energy Security and Net Zero): *Contains public sector information licensed under the Open Government Licence v3.0* (https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/). Keep this statement when you reuse them.
- **Markets in D2** (11): Austria, Croatia, Denmark, France, Greece, Iceland, Italy, Romania, Slovenia, Spain and United Kingdom. D3 holds the regions of those markets whose feed places a station in a region (README-d3.md). Terms of the source data, as stated on every row (`source_terms`) and on https://www.fuel-prices.eu/sources/ :

  | market | terms of the source data |
  |---|---|
  | Austria | No licence published by the source; aggregates computed by fuel-prices.eu (mean, median, p10, p90, number of stations); no station-level prices republished |
  | Croatia | Open data of the Ministry of Economy (MINGO), attribution required |
  | Denmark | No licence published by the source; aggregates computed by fuel-prices.eu (mean, median, p10, p90, number of stations); no station-level prices republished |
  | France | Licence Ouverte 2.0 (Etalab) |
  | Greece | CC BY 4.0 (Ministry of Economy and Development, Fuel Price Observatory fuelprices.gr, as licensed on data.gov.gr: https://data.gov.gr/dataset/parathrhthrio-timwn-ygrwn-kaysimwn) |
  | Iceland | No licence published by the source; aggregates computed by fuel-prices.eu (mean, median, p10, p90, number of stations); no station-level prices republished |
  | Italy | Italian Open Data License 2.0 (IODL 2.0) |
  | Romania | No licence published by the source; aggregates computed by fuel-prices.eu (mean, median, p10, p90, number of stations); no station-level prices republished |
  | Slovenia | No licence published by the source; aggregates computed by fuel-prices.eu (mean, median, p10, p90, number of stations); no station-level prices republished |
  | Spain | Reuse conditions of Royal Decree 1495/2011 (credit the source and give the date of the last update) |
  | United Kingdom | Open Government Licence v3.0 (https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/); attribution: Contains public sector information licensed under the Open Government Licence v3.0 |

  Where the source publishes no licence, the rows are aggregates computed by fuel-prices.eu (mean, median, p10, p90, number of stations); no station-level prices are republished.
- **Withdrawn from fuel-prices.eu on 1 October 2026** (their sources do not allow republication): Portugal, Andorra, Türkiye, Lithuania, Moldova, Serbia, North Macedonia, Montenegro and Bosnia and Herzegovina. None of them is in D2/D3. Portugal and Andorra were never in D2/D3; the D2/D3 rows of the others, published in versions 2026-09.4 to 2026-09.8, were also removed from the earlier commits of the Hugging Face and GitHub copies. (Portugal and Lithuania remain in D1: European Commission data.)
- Australia and Sweden are **excluded pending licence review** (reasons in README-d2.md); they are not in these files.
- Station-level prices (D4 on the site) are **not** part of this copy; they are on https://www.fuel-prices.eu/research/ under the licence of each national source.

Credit line: **Source: fuel-prices.eu (https://www.fuel-prices.eu/research/)**

## How to cite

> fuel-prices.eu (2026). *European fuel prices: EU Weekly Oil Bulletin panel (2005–) and daily national and regional averages* (Version 2026-10.1) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22978599

A `CITATION.cff` file is included. Per-set details (columns, method, markets, sources): `README-d1.md`, `README-d2.md`, `README-d3.md`; changes and corrections: `CHANGELOG.md`.

## Updates

- D1 weekly, after each Weekly Oil Bulletin (builds on Thursday 21:00 and Friday 14:00, Bucharest time); D2/D3 daily (06:40 Bucharest time).
- Kaggle and Hugging Face follow these builds; Zenodo gets a new version once a month (same concept DOI).
- The version name (`YYYY-MM`, suffix `.1`, `.2` for revisions) changes when the method or the coverage changes; see `CHANGELOG.md`.

Contact: hi@fuel-prices.eu · https://www.fuel-prices.eu/research/
