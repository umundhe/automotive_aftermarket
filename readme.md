# Auto Parts Compatibility & Analysis Project

##  Project Overview
This project focuses on analyzing the complex relationships between aftermarket auto parts and vehicle compatibility. By leveraging a relational dataset of sellers, products, and vehicle specifications, the goal is to establish a data-driven approach to part-to-vehicle fitment, price optimization, and market gap analysis.

##  Database Architecture
The dataset is structured as a relational database. To perform analysis, these tables must be joined using their respective keys.

[Image of relational database schema for auto parts dataset]

### Core Tables:
| File | Description | Key Joins |
| :--- | :--- | :--- |
| `applications.csv` | Main product listings (Price, Condition, Title) | `app_id`, `seller_id`, `category_id` |
| `compatibility.csv` | The bridge table linking parts to vehicles | `app_id`, `vehicles_id` |
| `vehicles.csv` | Vehicle metadata (Manufacturer, Model, Years) | `vehicles_id` |
| `product_category.csv`| Taxonomy of part types | `category_id` |
| `application_status.csv`| Status of the listing (VIP, Standard, etc.) | `status_id` |

---

##  Compatibility Baselines
Before moving to predictive modeling, the project establishes a baseline of the current ecosystem:

* **Network Density:** Measures how "connected" the parts are to the available vehicles.
* **Part Versatility:** Quantifies the "Multi-fit" capability of parts (Average number of vehicles per part).
* **Temporal Window:** The age range (Year Span) that a part typically covers.
* **Manufacturer Coverage:** Identification of which car brands have the highest density of aftermarket support.

---

##  Project Roadmap

### 1. Data Integration & Cleaning
* Merging relational tables using `pandas`.
* Standardizing `price_usd` and handling currency/outlier issues.
* Fixing temporal anomalies (e.g., cases where `bottom_year` > `top_year`).

### 2. Exploratory Data Analysis (EDA)
* Price distribution analysis by item condition.
* Correlation between part "Versatility" and market price.
* Identification of "Universal Parts" vs. "Niche Parts."

### 3. Feature Engineering 
* **Age Match:** Calculating the delta between part manufacturing and vehicle age.
* **Brand Affinity:**

### 4. Predictive Analysis 
This phase utilized machine learning to improve catalog accuracy and identify market opportunities:

* **Compatibility Link Prediction**: 
    * **Objective**: Predict the probability that a specific part fits a vehicle even if not explicitly listed.
    * **Results**: A **Random Forest Classifier** achieved **96.9% accuracy**.
    * **Outcome**: Identified **293 high-probability missing links** (potential fitments with >70% probability not currently in the dataset).

* **Price Elasticity Modeling**: 
    * **Objective**: Analyzed how "Versatility" (number of compatible vehicles) influences the market price.
    * **Result**: Found a near-zero correlation (**-0.0153**), suggesting pricing is driven by factors other than general compatibility.

* **Market Gap Identification**:
    * **Objective**: Forecasted "under-supplied" segments where vehicle population is high but part availability is low.
    * **Findings**: **Oldsmobile**, **Arcfox**, and **Fisker** showed the lowest coverage (1 part each), representing significant supply-chain opportunities.