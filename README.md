# Customer Churn Prediction — Interconnect 📡

## Project Overview

Customer retention is a critical challenge for telecommunications companies. Losing customers (churn) directly affects revenue and increases acquisition costs.

In this project, we analyze customer data from **Interconnect**, a telecommunications provider, to identify patterns that lead to customer cancellation and build a **machine learning model capable of predicting churn**.

The goal is to help the marketing team proactively identify customers likely to leave and offer targeted retention strategies such as discounts, promotions, or contract upgrades.

---

# Business Problem

Interconnect wants to **predict which customers are likely to cancel their services**. If high-risk customers can be identified early, the company can offer incentives to improve retention.

Key questions addressed:

* What factors influence customer churn?
* Which customer segments have the highest cancellation risk?
* Can machine learning models accurately predict churn?

---

# Dataset Description

The dataset consists of customer information collected from different sources.

### contract.csv

Information about customer contracts.

* `customerID` — unique customer identifier
* `BeginDate` — contract start date
* `EndDate` — contract end date ("No" if still active)
* `Type` — contract type (Month-to-month, One year, Two year)
* `PaperlessBilling` — electronic billing indicator
* `PaymentMethod` — payment method
* `MonthlyCharges` — monthly service cost
* `TotalCharges` — total amount charged

### personal.csv

Customer demographic information.

* `gender`
* `SeniorCitizen`
* `Partner`
* `Dependents`

### internet.csv

Internet services used by customers.

* `InternetService`
* `OnlineSecurity`
* `OnlineBackup`
* `DeviceProtection`
* `TechSupport`
* `StreamingTV`
* `StreamingMovies`

### phone.csv

Telephone service information.

* `MultipleLines`

All datasets were merged using the **customerID** column.

---

# Data Preparation

The following preprocessing steps were performed:

* Merged datasets into a single dataframe
* Converted date columns to datetime format
* Converted `TotalCharges` to numeric values
* Replaced missing values for non-internet users
* Removed duplicate rows
* Encoded categorical variables

Encoding methods included:

* Binary mapping for Yes/No variables
* Numeric mapping for gender
* One-hot encoding for multi-category variables

---

# Feature Engineering

Several features were created to improve model performance.

### Customer Tenure

Number of days a customer has stayed with the company.

### TotalServices

Total number of additional services used by the customer.

### EarlyStage

Indicator for customers with less than 6 months of tenure.

### RiskProfile

Combination of high monthly charges and short contract duration.

These features capture important behavioral patterns linked to churn.

---

# Exploratory Data Analysis

EDA revealed several important patterns:

### Tenure

Customers with shorter tenure are significantly more likely to churn.

### Monthly Charges

Higher monthly costs are associated with higher cancellation rates.

### Contract Type

Month-to-month contracts have much higher churn rates compared to long-term contracts.

### Additional Services

Customers with services such as **TechSupport** or **OnlineSecurity** are less likely to cancel.

### Customer Segments

Senior customers and those paying via **Electronic Check** show higher churn rates.

---

# Machine Learning Models

Three models were trained and evaluated:

### Logistic Regression

Baseline model using scaled features and balanced class weights.

### Random Forest

Tree-based ensemble model capturing nonlinear relationships.

### Gradient Boosting

Final model with the best predictive performance.

---

# Model Evaluation

Performance was evaluated using:

* Precision
* Recall
* F1-score
* Accuracy

The **Gradient Boosting model** achieved the best results with strong predictive performance and good balance between precision and recall.

---

# Key Insights

The most important factors influencing churn are:

1. **Customer Tenure**

   * New customers are significantly more likely to cancel.

2. **Contract Type**

   * Month-to-month contracts have the highest churn risk.

3. **Monthly Charges**

   * Higher charges correlate with increased cancellation.

4. **Additional Services**

   * Services such as technical support improve retention.

5. **Customer Segments**

   * Senior citizens and electronic check payments show higher churn rates.

---

# Business Recommendations

Based on the analysis and model results, the following strategies are recommended:

### Early Retention Programs

Focus retention efforts on customers within their first six months.

### Contract Incentives

Encourage customers to switch from monthly plans to longer contracts.

### Service Bundles

Offer discounted bundles that include additional services such as Tech Support.

### Targeted Customer Segments

Provide specialized support or offers to higher-risk groups such as senior customers.

---

# Project Structure

```
customer-churn-prediction/

data/
    contract.csv
    personal.csv
    internet.csv
    phone.csv

notebooks/
    churn_analysis.ipynb

README.md
requirements.txt
```

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

---

# Conclusion

Customer churn at Interconnect is strongly associated with short tenure, monthly contracts, and higher monthly charges. The predictive model developed in this project can help identify at-risk customers and enable targeted retention strategies.

Implementing these insights can reduce churn rates, improve customer satisfaction, and increase long-term revenue.



