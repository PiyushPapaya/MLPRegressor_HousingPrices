# MLPRegressor_HousingPrices

Based on variables like location, number of rooms, and median income, this notebook forecasts housing prices using a **MLPRegressor** model.To enhance the model's predictive capabilities, additional ratio-based features were created from the original columns.

---

## About the Dataset

The dataset contains approximately **20,640 rows** and **10 columns**.

Here’s a sample of the original data:

| longitude | latitude | housing_median_age | total_rooms | total_bedrooms | population | households | median_income | median_house_value | ocean_proximity |
|------------|-----------|--------------------|--------------|----------------|-------------|-------------|----------------|--------------------|-----------------|
| -122.23 | 37.88 | 41.0 | 880.0 | 129.0 | 322.0 | 126.0 | 8.3252 | 452600.0 | NEAR BAY |
| -122.22 | 37.86 | 21.0 | 7099.0 | 1106.0 | 2401.0 | 1138.0 | 8.3014 | 358500.0 | NEAR BAY |
| -122.24 | 37.85 | 52.0 | 1467.0 | 190.0 | 496.0 | 177.0 | 7.2574 | 352100.0 | NEAR BAY |
| -122.25 | 37.85 | 52.0 | 1274.0 | 235.0 | 558.0 | 219.0 | 5.6431 | 341300.0 | NEAR BAY |
| -122.25 | 37.85 | 52.0 | 1627.0 | 280.0 | 565.0 | 259.0 | 3.8462 | 342200.0 | NEAR BAY |

### Dataset Statistics

| Statistic | longitude | latitude | housing_median_age | total_rooms | total_bedrooms | population | households | median_income | median_house_value |
|------------|------------|-----------|--------------------|--------------|----------------|-------------|-------------|----------------|--------------------|
| count | 20640 | 20640 | 20640 | 20640 | 20433 | 20640 | 20640 | 20640 | 20640 |
| mean | -119.57 | 35.63 | 28.64 | 2635.76 | 537.87 | 1425.48 | 499.54 | 3.87 | 206855.82 |
| std | 2.00 | 2.14 | 12.59 | 2181.62 | 421.39 | 1132.46 | 382.33 | 1.90 | 115395.62 |
| min | -124.35 | 32.54 | 1.00 | 2.00 | 1.00 | 3.00 | 1.00 | 0.50 | 14999.00 |
| 25% | -121.80 | 33.93 | 18.00 | 1447.75 | 296.00 | 787.00 | 280.00 | 2.56 | 119600.00 |
| 50% | -118.49 | 34.26 | 29.00 | 2127.00 | 435.00 | 1166.00 | 409.00 | 3.53 | 179700.00 |
| 75% | -118.01 | 37.71 | 37.00 | 3148.00 | 647.00 | 1725.00 | 605.00 | 4.74 | 264725.00 |
| max | -114.31 | 41.95 | 52.00 | 39320.00 | 6445.00 | 35682.00 | 6082.00 | 15.00 | 500001.00 |

### Final Transformed Dataset (for Model Training)

| longitude | income_per_household_room | median_income | log_median_income | income_geo_ratio | income_longitude_interaction | income_latitude_interaction | geo_ratio | latitude | rooms_income_ratio | income_times_age | income_density | INLAND |
|------------|---------------------------|----------------|------------------|------------------|------------------------------|-----------------------------|------------|-----------|--------------------|------------------|----------------|--------|
| -122.23 | 1.192016 | 8.3252 | 2.232720 | 0.051997 | 0.068111 | 0.219778 | 0.309908 | 37.88 | 0.814521 | 341.3332 | 21.275509 | 0 |
| -122.22 | 1.330748 | 8.3014 | 2.230165 | 0.051858 | 0.067922 | 0.219266 | 0.309769 | 37.86 | 1.068234 | 174.3294 | 17.514641 | 0 |
| -122.24 | 0.875636 | 7.2574 | 2.111110 | 0.045333 | 0.059370 | 0.191741 | 0.309637 | 37.85 | 1.004719 | 377.3848 | 20.337120 | 0 |
| -122.25 | 0.970045 | 5.6431 | 1.893579 | 0.035247 | 0.046160 | 0.149091 | 0.309611 | 37.85 | 1.267156 | 293.4412 | 14.378309 | 0 |
| -122.25 | 0.612271 | 3.8462 | 1.578195 | 0.024024 | 0.031462 | 0.101617 | 0.309611 | 37.85 | 1.922700 | 200.0024 | 8.390359 | 0 |

---

## About the Notebook

This notebook consists of the following sections:

- Import Libraries  
- Import the Dataset  
- Examine the Dataset Structure  
- Transform the Dataset  
  - Create New Columns from Ratios and Quotients of Existing Columns for Improved Prediction  
  - Plot All Features’ Mutual Information Scores  
  - Select Features Based on Mutual Information Score > 0.2  
- Train-Test Split and Data Standardization  
- RandomizedSearchCV for Optimal Parameter Combination  
- Define the Model and Fit It to the Dataset  
- Model Evaluation  
- Plot the Learning Curve  
- Plot True vs. Predicted Values  
- Plot the Loss Curve  

---

## Results

The model achieved the following performance:

- **R² Score:** 0.7036  
- **Median Absolute Error:** 26,098.75  

The loss curve stabilized after approximately **110 iterations**.  
Plotting actual versus predicted values reveals a fairly linear trend, albeit one that is somewhat unbalanced because of outliers and some underutilized engineered features.

---

Notebook created and trained on [Kaggle](https://www.kaggle.com) by **Piyush Nagpal**.  
Published on **09 November 2025**.
