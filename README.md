# 🏠 Zillow Home Value Prediction

This project focuses on predicting home values using a real-world dataset from Zillow. It includes full data preprocessing, exploratory data analysis (EDA), feature selection, and model evaluation using various regression techniques.

The target variable in this dataset is defined as the difference between the logarithm of the predicted and actual home price, allowing the model to learn in a more normalized and robust way.

## 📊 Dataset Overview

The dataset contains **77,613 rows** and **59 columns**, where each row represents a property, and columns include a wide range of property-related attributes such as:

- Parcel ID
- Number of bedrooms and bathrooms
- Square footage
- Tax information
- Categorical attributes like architectural style, air conditioning type, etc.
- The `target` column, which represents `log(predicted price) - log(actual price)`

Some columns contain missing values or are highly imbalanced. Therefore, a data cleaning phase was essential before modeling.

## 🧼 Data Cleaning

To prepare the dataset for modeling, the following cleaning steps were applied:

- Removed columns that had:
  - Only one unique value
  - More than 60% missing values
- Imputed remaining missing values:
  - Used **mean** for numerical columns
  - Used **mode** for categorical columns
- Removed obvious outliers from the `target` column:
  - Kept only rows where `target` is between **-1 and 1**

These steps helped reduce noise and maintain the integrity of the dataset for training.

## 📈 Exploratory Data Analysis (EDA)

The dataset was analyzed to better understand its structure and relationships:

- Data types were categorized into: `int`, `float`, and `object` (categorical)
- A **distribution plot** of the `target` variable showed skewness and presence of outliers
- A **boxplot** was used to further confirm outliers in the `target`
- **Label Encoding** was applied to convert categorical variables into numerical format
- A **heatmap of correlations** revealed multicollinearity among several features

To reduce complexity and avoid information redundancy, some highly correlated features were removed from the dataset.

## 🤖 Model Training & Evaluation

After preprocessing, the features and target variable were split into training and test sets. The features were scaled using `StandardScaler`.

Four regression models were trained and evaluated using **Mean Absolute Error (MAE)**:

- Linear Regression
- XGBoost Regressor
- Lasso Regression
- Ridge Regression

All models achieved relatively low MAE on both train and test sets, with XGBoost performing slightly better on the training set, though it showed minor signs of overfitting.

```python
LinearRegression:
  Train MAE: 0.0620
  Test MAE : 0.0629

XGBRegressor:
  Train MAE: 0.0559
  Test MAE : 0.0651

Lasso:
  Train MAE: 0.0619
  Test MAE : 0.0629

Ridge:
  Train MAE: 0.0620
  Test MAE : 0.0630
```

## 🎯 Conclusion & Future Work

This project demonstrated an end-to-end pipeline for predicting home values based on the Zillow dataset.

Future improvements could include:

- Exploring additional advanced models and hyperparameter tuning
- Incorporating external data sources such as neighborhood demographics or economic indicators
- Implementing feature engineering to extract more predictive attributes
- Deploying the model for real-time predictions or integrating it into an application

Feedback and contributions are welcome!
