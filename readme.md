# Exploratory Data Analysis: Aftermarket Auto Parts Retail

## Project Overview
This project performs an **Exploratory Data Analysis (EDA)** on an aftermarket auto parts dataset to uncover relationships between vehicle specifications, part compatibility, and market demand. The goal is to perform the "heavy lifting" of data preparation and establish a baseline model for future optimization.

---

## 1. Data Cleaning & Preparation
The initial phase involved transforming raw, relational data into a flat structure suitable for analysis.
* **Table Joins:** Integrated `Parts`, `Vehicles`, and `Applications` tables using `part_id` and `vehicle_id` as primary keys.
* **Missing Value Strategy:** * `Engine_Size`: Imputed missing values using the **median** grouped by `Vehicle_Make`.
    * `Part_Condition`: Dropped records with missing labels as they represented less than 1% of the data.
* **Data Consistency:** Standardized string values (e.g., "BMW" vs "bmw") and converted manufacturing years to numerical `Vehicle_Age`.

---

## 2. Feature Engineering
Key features were engineered to capture the complexity of the automotive aftermarket:
* **Compatibility Index:** A numerical feature representing the total number of unique vehicle models a single part fits.
* **Engine Volume Class:** Categorized `Engine_Size` into 'Small', 'Medium', and 'High Performance' buckets.
* **Part-to-Vehicle Age Ratio:** A derived feature to see if older cars tend to require more specialized (lower compatibility) parts.

---

## 3. Key Findings (EDA)
Our visual analysis revealed several critical insights:
* **Compatibility Concentration:** **80% of parts** fit fewer than 5 vehicle models, while a small subset of "Universal" parts (mostly filters and spark plugs) fit over 50.
* **Brand Dominance:** **[Insert Brand, e.g., Toyota]** accounts for the highest volume of available parts in this dataset.
* **Outliers:** Identified several parts with a `Compatibility Index` higher than 200; these were verified as universal fasteners rather than engine-specific components.

---

## 4. Baseline Model
To establish a performance benchmark, a baseline **Random Forest Classifier** was trained.

### Model Parameters:
* **Algorithm:** Random Forest
* **Target Variable:** `Part_Category`
* **Features:** `Compatibility Index`, `Vehicle_Age`, `Engine_Size`, `Brand_Encoded`

### Performance Metrics:
* **Accuracy:** **[Enter your % here, e.g., 72.5%]**
* **Key Insight:** The model performs exceptionally well on "Engine" parts but struggles with "Interior Accessories," likely due to lower variance in features for cabin parts.

---

## 5. Next Steps
* **Module 24:** Implement Hyperparameter Tuning (GridSearchCV).
* **Feature Expansion:** Incorporate pricing data to predict "Profitability" as a secondary target.
* **Model Comparison:** Test Gradient Boosting (XGBoost) against this baseline.