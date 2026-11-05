# Fitness Tracker Data Cleaning and Preprocessing

A Python (pandas / scikit-learn) project that cleans, explores, and prepares a large fitness-tracker dataset for analysis and machine learning.

> Group project for the Data Cleaning and Preprocessing course, Data Science Department, Umm Al-Qura University.

## Objective
Assess the quality of the fitness data and prepare it for exploratory analysis, looking at how activity (steps, active minutes) relates to health indicators (sleep, heart rate) and mood.

## Dataset
- About 1,000,000 rows and 12 columns (daily records per user).
- **Numeric:** steps, calories_burned, distance_km, active_minutes, sleep_hours, heart_rate_avg
- **Categorical:** workout_type, weather_conditions, location, mood
- **Other:** user_id, date
- Source: [Fitness Tracker Dataset on Kaggle](https://www.kaggle.com/datasets/smayanj/fitness-tracker-dataset). The CSV is not included in this repo; download it from Kaggle.

## What Was Done
| Step | Details |
|------|---------|
| Quality assessment | Missing values, duplicates, invalid values (negative steps, impossible sleep hours), inconsistent labels |
| Missing values | Median for numeric columns; mode for categorical columns; "Unknown" for `workout_type` |
| Cleaning | Removed duplicates, fixed data types (dates, categories), normalized text labels |
| Outliers | Detected with the IQR method and boxplots; kept because values were realistic; log transformation applied on a copy |
| EDA | Summary statistics, group-by, pivot tables, histograms, bar plots, boxplots, scatter plots, correlation heatmap |
| Feature engineering | `Activity_Level` (Low / Medium / High) from step counts; PCA |
| Transformation | Standard scaling (RobustScaler also tested), log transformation, one-hot encoding of categorical columns |

## Key Findings
- Numeric features had realistic ranges (for example heart rate 60 to about 180 bpm).
- Correlations between numeric features were very weak (all within about ±0.08 in the sample).
- Categories (workout type, mood, weather) were fairly evenly distributed, with only small differences in calories and sleep.
- In the sample, yoga shows a somewhat higher average calories burned than the other workout types; weather conditions show only small differences.
 
## Visualizations
The plots below were generated from a sample of the data.

![Correlation Heatmap](images/Screenshot_2026-11-05_150653.png)

![Calories Burned by Weather Conditions](images/Screenshot_2026-11-05_150636.png)

![Average Calories Burned by Workout Type](images/Screenshot_2026-11-05_150744.png)

## Limitations
- No demographic data (age, gender, weight).
- Weak correlations limit predictive modeling.
- PCA was run on unscaled features, so the first component dominates (about 99% of variance); results should be re-checked on scaled data.

## Files
- `fitness_tracker_preprocessing.ipynb`: the full notebook (written for Google Colab)

## How to Run
1. Open the notebook in Google Colab.
2. Download the dataset from the Kaggle link above and upload `fitness_tracker_dataset.csv` to the Colab session (the notebook reads it from `/content/`).
3. Run all cells.

## Tools Used
Python, pandas, NumPy, scikit-learn, seaborn, Matplotlib, Google Colab

## Team
- Fay Salman Alzahrany
- Aylan Saad Alharbi
- Manal Marzouq Alrowqi
