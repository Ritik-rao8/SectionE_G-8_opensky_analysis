# ✈️ OpenSky Global Flight Analysis

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Data Dictionary](https://img.shields.io/badge/docs-data%20dictionary-green.svg)](docs/data_dictionary.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive data engineering and analytics pipeline for processing global aircraft state vectors from the **OpenSky Network**. This project transforms raw API flight data into high-quality, dashboard-ready datasets through a structured 5-stage pipeline.

---

## 🚀 Project Overview

This repository contains the end-to-end analysis of real-time flight data. We tackle challenges like sensor noise, missing geospatial data, and high-frequency updates to deliver actionable insights into global air traffic patterns.

### Key KPIs Tracked
*   **Airborne Volume**: Percentage of aircraft currently in flight vs. on-ground.
*   **Geospatial Density**: Identification of high-traffic corridors and country-level distributions.
*   **Flight Profile Analysis**: Vertical rates, altitude distributions, and velocity trends.
*   **Feature Engineering**: ML-ready transformations including trigonometric heading encoding.

---

## 🛠 The Pipeline

The analysis is broken down into five sequential notebooks:

1.  **[01 Extraction](notebooks/01_extraction.ipynb)**: Data ingestion from the OpenSky REST API.
2.  **[02 Cleaning](notebooks/02_cleaning.ipynb)**: Imputation of missing altitudes/velocities and coordinate pruning.
3.  **[03 EDA](notebooks/03_eda.ipynb)**: Exploratory analysis of temporal and geospatial flight patterns.
4.  **[04 Statistical Analysis](notebooks/04_statistical_analysis.ipynb)**: Feature engineering and distribution testing.
5.  **[05 Final Load Prep](notebooks/05_final_load_prep.ipynb)**: Preparation of the `tableau_ready_dataset.csv`.

---

## 📁 Project Structure

```bash
├── data/
│   ├── raw/                # Original API extracts (opensky.csv)
│   └── processed/          # Cleaned & dashboard-ready data
│       ├── cleaned_dataset.csv
│       └── tableau_ready_dataset.csv
├── docs/
│   └── data_dictionary.md  # Detailed field definitions & cleaning logic
├── notebooks/              # Modular analysis notebooks (01-05)
└── README.md               # You are here
```

---

## 📖 Documentation

For detailed information on every column, data types, and specific cleaning decisions made during the preprocessing phase, please refer to our **[Data Dictionary](docs/data_dictionary.md)**.

### Data Quality Highlights
*   **Mandatory Coordinates**: Rows without latitude/longitude are removed to ensure geospatial accuracy.
*   **Median Imputation**: Missing barometric and geometric altitudes are imputed using group-wise medians.
*   **Logical Validation**: Vertical rates are forced to zero for all grounded aircraft.

---

## 🔧 Setup & Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yatinsingh2007/SectionE_G-8_opensky_analysis.git
   cd SectionE_G-8_opensky_analysis
   ```

2. **Install Dependencies**:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy
   ```

3. **Run the Pipeline**:
   Start with `notebooks/01_extraction.ipynb` and follow the sequence through `05_final_load_prep.ipynb`.

---

## 📊 Visualizations
The final outputs are optimized for **Tableau**. Connect the `tableau_ready_dataset.csv` to your dashboard to visualize live flight profiles and global traffic heatmaps.

---
*Developed as part of the Section E Group 8 Capstone Project.*
