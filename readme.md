Exploratory Data Analysis: Aftermarket Auto Parts Retail
Project Objective
The goal of this analysis is to perform Exploratory Data Analysis (EDA) on the Georgian Aftermarket Auto Parts dataset to identify key drivers of part compatibility and retail demand. This module focuses on data cleaning, feature engineering, and establishing a baseline machine learning model for future optimization.

The Dataset
The analysis utilizes a relational structure consisting of:

Parts Table: Specifications and branding for individual components.

Vehicles Table: Detailed car data (Make, Model, Year, Engine).

Applications Table: The mapping link between parts and compatible vehicles.

Results & Key Findings
1. Data Cleaning & "Heavy Lifting"
To make the data usable for modeling, the following steps were taken:

Relational Merging: Joined the Parts, Vehicles, and Applications tables to create a master dataframe.

Handling Missingness: Identified null values in Engine_Size and imputed them using the median value per specific Vehicle_Model.

Outlier Detection: Used box plots to identify and remove extreme outliers in Price (if applicable) and Vehicle_Year that represented data entry errors.

2. Feature Engineering
Created new features to improve model predictive power:

Compatibility Score: A count of how many unique vehicle models a single part fits.

Vehicle Age: Derived from the current year and the vehicle’s manufacturing year.

Brand Premium: A categorical flag for "Luxury" vs. "Standard" brands based on the vehicle manufacturer.

3. Exploratory Visualizations
Compatibility Distribution: Discovered a "Long Tail" distribution where [X]% of parts are niche (fit < 3 vehicles), while [Y]% are universal.

Market Availability: A bar chart revealed that [Brand Name] has the highest volume of aftermarket parts, suggesting a high-demand secondary market for that manufacturer.

Correlation Heatmap: Observed a strong positive correlation between [Feature A] and [Feature B], guiding final feature selection for the baseline model.

Baseline Model Performance
A baseline Random Forest Classifier was developed to predict [Target Variable, e.g., Part Category or Condition].

Model Type: Random Forest

Key Features: Compatibility Score, Vehicle Age, Engine Size

Baseline Accuracy: [e.g., 74.2%]

Primary Metric (F1-Score): [e.g., 0.72]

Note: This model serves as a benchmark. In Module 24, I will explore Hyperparameter Tuning and Gradient Boosting to improve these metrics.
