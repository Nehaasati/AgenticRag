Overview

This project builds a regression model (Random Forest) to predict a numerical target (e.g., sales, visits, price). Key steps:

Data cleaning & preparation

Train/test split

Baseline Random Forest model training

Model evaluation (MAE, MSE, RMSE, R²)

Hyperparameter tuning with RandomizedSearchCV and cross-validation

Interpretation of results and next steps

Data cleaning & preparation :

(Summarize the actual operations you ran — adapt to your dataset)

Missing values

Inspected columns with df.isna().sum() and handled missing data:

Dropped columns with > X% missing (if any).

Imputed numeric columns using median (robust to outliers) or mean where appropriate.

Imputed categorical columns with a special token ('missing') or the mode.

Type conversion & parsing

Ensured date/time columns are datetime (with pd.to_datetime) and extracted features (year, month, day, weekday, hour).

Converted categorical columns to category dtype.

Feature engineering

Created new features that help the model (e.g., lag features, rolling means, interaction terms).

Encoded categorical features:

Low-cardinality: one-hot encoding (pd.get_dummies() or OneHotEncoder).

High-cardinality: target encoding or ordinal encoding.

Outlier handling

Inspected distributions and clipped or transformed extreme values (log transform for right-skewed features).

Scaling

For tree-based models scaling is not required; for other models I used StandardScaler or MinMaxScaler as needed.

Train/test split

Split data into training and test sets (e.g., train_test_split(..., test_size=0.2, random_state=42)).

If time-series: used a time-based split (train on earlier dates, test on later dates).
