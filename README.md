# NYC Taxi Fare Prediction

**Role:** Individual Project | **Course:** UCR STAT 206

**Objective:** Leverage real-world New York City taxi data to extract actionable insights and construct a high‑accuracy fare prediction model using advanced feature engineering and machine learning techniques.

---

## Project Overview

I conducted an end‑to‑end analysis of NYC taxi trips—covering data ingestion, cleansing, exploratory analysis, feature engineering, and predictive modeling—to understand fare drivers and deliver a production‑ready regression model with robust performance.

## Methodology

1. **Data Preparation & Quality Assurance**

   * Imported 100,000 ride records (`train.csv`, `test.csv`) and enforced data integrity by dropping rows with missing coordinates or invalid values (fares ≤ \$0 or ≥ \$300; passenger counts outside 1–10).
   * Standardized datetime formats and validated geographic bounds within NYC (latitudes 40–42, longitudes –75 to –72).

2. **Feature Engineering**

   * **Taxi‑Cab Distance:** Calculated Manhattan (L1) distance from pickup/drop‑off coordinates.
   * **Temporal Signals:** Extracted hour, day‑of‑week, month, and weekend indicator from timestamps.
   * **Airport Flag:** Identified trips to/from JFK, LGA, EWR via proximity threshold.
   * **Advanced Features:** Added log‑distance and interaction term (distance × passenger\_count) to capture non‑linear and combined effects.

3. **Exploratory Data Analysis (EDA)**

   * **Distributions:** Revealed right‑skew for fare and distance; most trips carry one passenger.
   * **Correlation:** Established strong positive correlation (0.80) between distance and fare; negligible effect of passenger count.
   * **Geospatial Mapping:** Plotted 2,000 ride points on a dark‑themed NYC map—highlighting dense activity in Midtown and airport corridors.

4. **Model Development & Tuning**

   * **Baseline:** Linear Regression yielded RMSE ≈ 6.12 (average error \$6.12).
   * **Advanced:** Random Forest (100 trees) improved to RMSE ≈ 5.47.
   * **Optimization:** GridSearchCV over 54 parameter combinations (n\_estimators, max\_depth, min\_samples\_split) with 3‑fold CV; best model (200 trees, max\_depth = 10, min\_samples\_split = 10) achieved RMSE ≈ 5.25.

5. **Final Evaluation**

   * Retrained tuned model on full training set; generated fare predictions on hold‑out test data—delivering reliable estimates within \$5.25 average error.

---

## Impact & Next Steps

* **Business Insight:** Identified peak demand windows and critical fare drivers, enabling dynamic pricing and resource allocation for fleet operators.
* **Scalability:** Production‑ready pipeline supports real‑time fare estimation; architecture can integrate weather or traffic feeds.
* **Enhancements:** Incorporate external data (weather, events), test gradient boosting or deep‑learning regressors, and deploy via REST API for operational use.

---

**Technologies:** Python, pandas, NumPy, scikit‑learn, Matplotlib, seaborn, Plotly, GeoPandas, Folium

**Key Metrics:** Final RMSE = \$5.25 | Distance–Fare Correlation = 0.80 | Data Sample = 100K records
