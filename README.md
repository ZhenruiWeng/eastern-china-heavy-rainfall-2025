# 2025 Eastern China Heavy Rainfall Dataset (92 Days)

**92 days of daily reanalysis weather data over Eastern China, built for binary
heavy-rain-day classification.** Eastern China 2025 weather dataset for rainfall
forecasting: one row per day from 2025-07-01 to 2025-09-30, each carrying the
ERA5-style surface variables that drive monsoon-season rain, plus a binary
heavy-rain label.

Kaggle mirror: [2025 Eastern China Heavy Rainfall Dataset(92 Days)](https://www.kaggle.com/datasets/zhenruiweng/2025-eastern-china-heavy-rainfall-dataset92-days)
(Kaggle **Datasets bronze medal**, usability 10.0 / 10.0, Apache-2.0).
Upstream source as stated on the Kaggle page: the
[Climate Data Store (CDS)](https://cds.climate.copernicus.eu/) / Copernicus
Climate Change Service (C3S), 2025 reanalysis data.

## Quick facts

| | |
|---|---|
| Rows | **92** (one per day, 2025-07-01 → 2025-09-30) |
| Columns | **8** (1 timestamp + 6 weather variables + 1 label) |
| Label | `heavy_rain_day` — 57 positive / 92 days = **62.0%** |
| Spatial extent (per Kaggle page) | North 36°, West 102°, South 20°, East 125° |
| Season | Peak Eastern-China rainy season (Meiyu tail + typhoon months) |
| Source | Copernicus CDS/C3S reanalysis, self-processed |
| License | Apache-2.0 |

## Column dictionary

| Column | Unit (as published) | Description |
|---|---|---|
| `valid_time` | date | Day of the record (UTC reanalysis convention) |
| `u10` | m/s | 10 m wind, u (east–west) component |
| `v10` | m/s | 10 m wind, v (north–south) component |
| `d2m` | **K** | 2 m dewpoint temperature |
| `t2m` | **°C** | 2 m temperature |
| `msl` | Pa | Mean sea-level pressure |
| `vimd` | — | ERA5 vertical integral of mass divergence; negative values = net mass/moisture convergence, the dynamical precursor of precipitation |
| `heavy_rain_day` | 0/1 | Binary label — whether the day qualifies as a heavy-rain day |

Observed ranges (daily means over the 92 days):

| Variable | min | mean | max |
|---|---:|---:|---:|
| u10 | −1.85 | −0.59 | 0.72 |
| v10 | −2.09 | +0.39 | 1.91 |
| d2m | 290.60 K | 294.23 K | 296.11 K |
| t2m | 21.15 °C | 25.03 °C | 27.99 °C |
| msl | 99,986 Pa | 100,781 Pa | 101,685 Pa |
| vimd | −0.594 | −0.150 | +0.096 |

## Notes for users

- **Mixed temperature units, preserved as published.** `d2m` is in Kelvin while
  `t2m` is in Celsius. Convert `d2m` (subtract 273.15) before computing
  humidity proxies such as spread `t2m − d2m`. The mixture is kept verbatim so
  this copy stays drop-in compatible with the Kaggle version.
- **A 92-row dataset is a small-sample benchmark, not a production corpus.** It
  is sized for method prototyping — imbalanced-classification baselines,
  small-sample exercise of rainfall forecasting pipelines, feature-importance
  studies — where every row is interpretable. For robust evaluation prefer
  leave-one-out or repeated CV over a single split.
- `vimd` is left in its native reanalysis sign convention: negative
  (convergence) dominates the season, matching the 62% heavy-rain-day base rate.
- The Kaggle page lists 2 companion notebooks
  ([Code tab](https://www.kaggle.com/datasets/zhenruiweng/2025-eastern-china-heavy-rainfall-dataset92-days/code)).

## Files

```
├── data/2025_Eastern_China_HeavyRain_Dataset.csv   # complete dataset (92 rows × 8 columns)
├── README.md
└── LICENSE                                         # Apache-2.0
```

## Citation / acknowledgment

- Upstream: **Copernicus Climate Change Service (C3S) Climate Data Store** —
  2025 reanalysis data, retrieved via CDS as described on the Kaggle page.
  Please credit C3S/CDS for any scientific use of the underlying reanalysis.
- Kaggle mirror: [zhenruiweng/2025-eastern-china-heavy-rainfall-dataset92-days](https://www.kaggle.com/datasets/zhenruiweng/2025-eastern-china-heavy-rainfall-dataset92-days).

## License

[Apache-2.0](LICENSE) — identical to the license declared on the Kaggle dataset page.
