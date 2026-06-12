# Household Power Consumption — Big Data Analysis

End-to-end big data pipeline analyzing 2M+ minute-level household electricity readings using PySpark, from raw ingestion to machine learning prediction.

**Dataset:** UCI Individual Household Electric Power Consumption (2006–2010)

---

## Pipeline Structure

The notebook follows a structured 5-phase pipeline:

| Phase | Description |
|---|---|
| 1. Acquire | Download UCI dataset, initialize SparkSession (4GB driver) |
| 2. Prepare | Type casting, null handling, feature engineering, sanity checks |
| 3. Analyze | Aggregations, peak/off-peak analysis, sub-metering breakdown |
| 4. Report | Visualizations — hourly trends, heatmaps, correlation matrix |
| 5. Predict | Regression models comparing Linear Regression vs Random Forest |

---

## Key Findings

- **2,049,280 records** retained after null removal (98.75% retention rate)
- **Weekend consumption 33% higher** than weekdays (1.89 kW vs 1.42 kW)
- **Evening peak (6–9 PM) loads 2× more** than off-peak periods
- **Water heater + AC circuit dominates** sub-metering at 7.38 Wh/min
- **Sub_metering_3** is the strongest ML feature (~39% Random Forest importance)
- Voltage stable at 240.91V ± 3.46V across all readings

---

## ML Models

| Model | Features | Notes |
|---|---|---|
| Linear Regression | 7 features | Baseline (OLS) |
| Random Forest | 7 features | 100 trees, max depth 12 |

**Features used:** Global reactive power, Voltage, Sub-metering 1/2/3, Hour, Day of week  
**Target:** Global active power  
**Split:** 80/20 (35,710 train / 8,928 test)  
**Note:** Global Intensity excluded to prevent data leakage (P = V × I)

---

## Tech Stack

PySpark · Scikit-learn · Pandas · Matplotlib · Seaborn

---

## How to Run

Open `2432214_YuyutsuLamsal.ipynb` in Google Colab and run all cells sequentially.  
PySpark and all dependencies are installed in the first cell.

---

## Module

6CS030 — Big Data Analytics  
Herald College Kathmandu | University of Wolverhampton  
Author: Yuyutsu Lamsal (Student ID: 2432214)
