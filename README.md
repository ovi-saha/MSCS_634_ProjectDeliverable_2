# MSCS_634_ProjectDeliverable_2
This Repo is Residency Day 2: Project Deliverable 2: Project Deliverable 2: Regression Modeling and Performance Evaluation MSCS-634-M20

# Deliverable 2: Regression Modeling and Evaluation  
**Course:** Advanced Big Data and Data Mining (MSCS-634-M20)  
**Dataset:** Passenger Travel Facts and Figures (Bureau of Transportation Statistics)

---

## Project Overview

This deliverable focuses on developing and evaluating regression models using the Passenger Travel Facts and Figures dataset. The primary objective was to understand how various transportation-related variables influence the numerical target variable (`Value`). 

Building on the preprocessing performed in Deliverable 1, we applied feature engineering, handled high-dimensional categorical variables via one-hot encoding, and trained regression models to predict travel values. The analysis emphasizes proper data preparation, model evaluation, and interpretation.

we got this data from : https://data.bts.gov/Research-and-Statistics/Passenger_Travel_Facts_and_Figures_Latest/pqmc-mnds/about_data

---

## Dataset Description

The dataset contains transportation statistics categorized by commuting mode, statistical type, and year. The primary columns used in this analysis include:

- `Year`
- `Mode`
- `Statistic`
- `Value` (Target Variable)

Preprocessing steps included removing duplicate columns, handling missing values, and converting categorical and boolean variables to numeric values suitable for regression modeling.

---

## Data Preprocessing & Feature Engineering

Key steps in preparing the data for regression included:

1. **One-Hot Encoding:**  
   Categorical variables `Mode` and `Statistic` were transformed into dummy variables for numerical modeling:

   ```python
   df_reg = pd.get_dummies(df, columns=['Mode', 'Statistic'], drop_first=True)
   
2. **Boolean Conversion:**
Dummy variables with Boolean type were converted to integers:

df_reg = df_reg.astype(int, errors='ignore')


3. **Feature Selection:**
Only meaningful predictors such as Year and selected categories were retained to reduce dimensionality and avoid multicollinearity.

4. **Train-Test Split:**
The dataset was split into training and testing subsets for model evaluation.

5. **Model Fitting:**
Linear Regression and Ridge Regression models were trained on the processed data.

## Regression Models & Evaluation

The following models were evaluated:

- Linear Regression

 - Ridge Regression (L2 regularization)

Performance metrics on the test dataset:
| Model             | RMSE  | R²   |
| ----------------- | ----- | ---- |
| Linear Regression | 23.64 | 0.83 |
| Ridge Regression  | 23.42 | 0.84 |

## Interpretation

- Both models performed strongly, explaining more than 80% of the variance in passenger travel values.

- Ridge Regression slightly outperformed Linear Regression, indicating that regularization helped stabilize coefficient estimates in the presence of high-dimensional dummy variables.

- Low RMSE values indicate accurate predictions and strong practical applicability.

## Key Insights

- The Year variable shows measurable trends, highlighting changes in travel behavior over time.

- Commuting modes significantly influence travel values, indicating the impact of transportation type on overall passenger travel.

- Weekday versus weekend travel patterns show meaningful differences, reflecting behavioral variations.

- Reducing dimensionality and focusing on relevant features improved model interpretability and performance.

## Challenges Encountered

- High dimensionality: One-hot encoding created thousands of features, increasing multicollinearity and overfitting risk.

- Data type errors: Boolean and categorical variables initially caused ValueError in regression models. Conversion to numeric types was required.

- Duplicate and inconsistent columns: Columns like Year, Year, and Year 1 were removed to avoid redundancy.

- Regularization considerations: Feature scaling was necessary for Ridge Regression to perform effectively.

## Conclusion

Both regression models performed well, with Ridge Regression providing slightly better predictive performance due to its regularization properties. The analysis confirms that properly engineered features and careful preprocessing are critical to achieving strong regression results on real-world transportation datasets.
