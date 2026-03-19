# 🚕 NYC Yellow Taxi Trip Analysis

A full-stack data science project analysing 7.4 million NYC  yellow taxi trips from *January 2019* covering data engineering, exploratory analysis, geospatial visualisation, and machine learning.

## Overview

This project walks through the complete data science workflow using one of the most well-known public datasets in the field: the NYC TLC (Taxi & Limousine Commission) trip records. The goal is to understand the patterns of urban taxi demand across New York City, and build a model that predicts how much a passenger will tip.

The notebook is structured in five layers, each building on the last:

| Layer | Section | What happens here |
|-------|---------|-------------------|
| 0 | Setup | Import libraries, configure plot styling |
| 1 | Data Engineering | Load, clean, and enrich the raw data |
| 2 | Exploratory Analysis | Answer business questions with charts |
| 3 | Geospatial Analysis | Map pickup hotspots across 263 NYC zones |
| 4 | Machine Learning | Train and evaluate a tip-prediction model |
| 5 | Conclusions | Summarise findings in plain language |

## Download the Data

The dataset is too large to host on GitHub. Download the files manually and place them in a `data/` folder in the project root.

| File | Link |
|------|------|
| `yellow_tripdata_2019-01.csv` | [NYC TLC Trip Records](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) → Yellow Taxi → January 2019 |
| `taxi+_zone_lookup.csv` | [Taxi Zone Lookup](https://d37ci6vzurychx.cloudfront.net/misc/taxi+_zone_lookup.csv) |
| `taxi_zones/` (shapefile) | [Taxi Zone Shapefile](https://d37ci6vzurychx.cloudfront.net/misc/taxi_zones.zip) |


## Dataset

| File | Description |
|------|-------------|
| `data/yellow_tripdata_2019-01.csv` | 7.6M yellow taxi trips (January 2019) |
| `data/taxi+_zone_lookup.csv` | Maps zone IDs to borough and zone names |
| `data/taxi_zones/taxi_zones.shp` | NYC shapefile for geospatial plotting |

All data is publicly available from the  [NYC TLC Trip Record Data portal](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).


## Key Findings

- **Demand** peaks at 8–9 AM and 6–8 PM on weekdays; Fridays and Saturdays are the busiest days overall.
- **Manhattan** accounts for over 90% of all pickups and revenue. NYC yellow taxis are functionally a Manhattan transit system.
- The **median fare is $9.00** most trips are short, quick hops within a few blocks.
- **Tip amounts correlate more strongly with fare than with distance**, 
  suggesting passengers tip proportionally (roughly 15–20% of the meter).
- A **Random Forest model** using 5 features predicts tip amounts with meaningful accuracy. `fare_amount` is the dominant predictor.


## Project Structure
```
nyc-taxi-analysis/
│
├── data/
│   ├── yellow_tripdata_2019-01.csv    ← main trip records
│   ├── taxi+_zone_lookup.csv          ← zone → borough mapping
│   └── taxi_zones/                    ← shapefile for map plots
│       ├── taxi_zones.shp
│       └── ...
│
├── NYC_Taxi_Analysis.ipynb            ← main notebook
└── README.md
```


## Requirements

Install all dependencies with:
```bash
pip install pandas numpy matplotlib seaborn geopandas scikit-learn
```

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading and manipulation |
| `numpy` | Numerical operations |
| `matplotlib` | Base plotting |
| `seaborn` | Styled statistical charts |
| `geopandas` | Shapefile loading and choropleth maps |
| `scikit-learn` | Train/test split, Random Forest,evaluation metrics |

## How to Run

1. Clone or download this repository.
2. Download the dataset files (see **Download the Data** above) and place them in the `data/` folder.
3. Install the required libraries (see above).
4. Open `NYC_Taxi_Analysis.ipynb` in Jupyter and run all cells from top to bottom.

The notebook is designed to run sequentially, each section depends on the cleaned DataFrame produced by the section before it.


## Results

| Metric | Value |
|--------|-------|
| Trips analysed | 7,469,779 |
| Rows removed (cleaning) | 198,013 (2.6%) |
| Model | Random Forest (100 trees, 100k training sample) |
| Mean Absolute Error | ~$1.0–1.5 |
| Top predictive feature | `fare_amount` |


## Possible Extensions

- Add **payment type** as a feature (cash vs. card tippers behave very differently)
- Train on a **full year** of data to capture seasonal patterns
- Try **XGBoost or LightGBM** for a potential accuracy boost
- Build an **interactive Plotly dashboard** for the EDA charts
- Add a **dropoff borough** feature to capture zone-pair trip type

## Author
**Hassan** - feel free to reach out or connect:

[GitHub](https://github.com/hassan-akhter)

[LinkedIn](https://www.linkedin.com/in/hassanakhter122/)