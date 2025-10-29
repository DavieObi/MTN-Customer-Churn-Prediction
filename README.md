# MTN Customer Churn Prediction

-----

## 📝 Introduction

This project aims to analyze customer data for a telecommunications company (MTN) to identify and predict which customers are likely to **churn** (cancel their subscription or cease using the service). By applying machine learning classification models, we can gain insights into the key factors driving customer attrition and provide a tool for proactive retention strategies.

-----

## 📊 Dataset Overview

The dataset, `mtn_customer_churn.csv`, contains 974 customer records with 17 features, including demographics, service usage, purchasing behavior, and satisfaction metrics.

| Feature Name | Description | Data Type |
| :--- | :--- | :--- |
| **Customer Churn Status** | The target variable (Yes/No). | Object (Target) |
| **Customer ID** | Unique identifier. | Object |
| **Age** | Customer's age. | Integer |
| **State** | Geographic location of the customer. | Object |
| **MTN Device** | Type of device used (e.g., 4G Router, Mobile SIM Card). | Object |
| **Gender** | Customer's gender. | Object |
| **Satisfaction Rate** | Numerical rating (1 to 5). | Integer |
| **Customer Review** | Categorical review (e.g., Fair, Poor). | Object |
| **Customer Tenure in months** | How long the customer has been subscribed. | Integer |
| **Subscription Plan** | The customer's active plan. | Object |
| **Total Revenue** | Total revenue generated from the customer. | Integer |
| **Data Usage** | Average data consumption. | Float |
| **Reasons for Churn** | The stated reason for leaving (contains missing values). | Object |

### Key Data Observations

  * The target variable is **imbalanced**, with **690 customers not churning** ('No') and **284 customers churning** ('Yes').
  * The `Reasons for Churn` column contains a significant number of missing values, which were treated during preprocessing.

-----

## 🛠️ Methodology and Preprocessing

The analysis followed a standard machine learning workflow, including data cleaning, feature engineering, and modeling.

### Data Cleaning and Feature Engineering

1.  **Handling Missing Data:** Missing values in the `Reasons for Churn` column were imputed with the value **'Not Applicable'**.
2.  **Feature Dropping:** The `Full Name` and `Date of Purchase` columns were dropped as they were not useful for the predictive modeling task.
3.  **Categorical Encoding:**
      * The categorical features (`State`, `MTN Device`, `Gender`, `Customer Review`, `Subscription Plan`, `Reasons for Churn`) were converted into a numerical format using **One-Hot Encoding**.
      * The target variable, `Customer Churn Status`, was encoded using **Label Encoding** (Yes $\rightarrow$ 1, No $\rightarrow$ 0).
4.  **Feature Scaling:** All numerical features were standardized using **StandardScaler** to ensure equal contribution to the models.
5.  **Data Splitting:** The dataset was split into training and testing sets using an **80/20 ratio**.

-----

## 🧠 Modeling and Results

Three different classification algorithms were trained and evaluated on the processed data:

### Model Evaluation

| Model | Accuracy Score | Key Metric (F1-Score / Macro Average) |
| :--- | :--- | :--- |
| **Logistic Regression** | **0.78** | **0.78** (Weighted Avg) |
| **K-Nearest Neighbors (KNN)** | 0.75 | 0.75 (Weighted Avg) |
| **Decision Tree** | 0.63 | 0.64 (Weighted Avg) |

### Conclusion

The **Logistic Regression** model performed the best in predicting customer churn, achieving the highest overall **Accuracy of 0.78**. This model is recommended for deployment due to its superior performance and interpretability.

-----

## 📦 Installation and Requirements

To run this notebook and reproduce the results, the following Python libraries are required. You can install them using `pip`:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Key Libraries Used

  * `pandas`
  * `numpy`
  * `matplotlib`
  * `seaborn`
  * `scikit-learn`
