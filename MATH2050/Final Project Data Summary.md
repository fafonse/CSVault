

# **Methodology and Data Summary**

## **Abstract**
This project focuses on analyzing a Taiwanese Bankruptcy Prediction dataset to identify key factors that can predict whether a company will go bankrupt. Bankruptcy prediction is important because it helps protect investors, provides context to lawmakers, and enables companies to take preventative measures against bankruptcy. Prior studies, such as those using Altman’s Z-score model and more recent machine learning studies, have shown that several factors, like return on assets, gross margin, and profitability rates, are strong predictors of bankruptcy. In this project, we plan to build visual models to answer questions such as: Which financial indicators are most predictive of bankruptcy? And can we predict if a business will go bankrupt? After answering the questions, we hope that we can use limited public data and our models to predict how close a publicly traded company is to bankruptcy.

## **1. Objective and Dataset Overview**

The objective of this project is to **predict whether a company will go bankrupt** based on financial and accounting data.

**Dataset Source:** Taiwan Economic Journal (1999–2009), donated June 27, 2020.

**Instances:** 6,819 companies

**Features:** 95 financial ratios

**Target Variable:** Bankrupt? (1 = bankrupt, 0 = non-bankrupt)

**Task Type:** Classification

**Subject Area:** Business & Finance

### **Key Features**

|Variable|Description|Type|
|---|---|---|
|Bankrupt?|Target variable|Binary|
|ROA(C) before interest and depreciation|Profitability ratio|Continuous|
|Operating Gross Margin|Profitability ratio|Continuous|
|Current Ratio|Liquidity ratio|Continuous|
|Debt Ratio|Leverage ratio|Continuous (%)|
|Net Income to Total Assets|Efficiency ratio|Continuous|
|Equity to Liability|Leverage ratio|Continuous|

- Continuous features: 91

- Integer features: 4

- Target variable: Bankrupt?


### **Summary Statistics of Selected Features**

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Feature|Mean|Median|STD dev|Min|Max|
|ROA(C)|0.034|0.028|0.057|-0.42|0.49|
|Debt Ratio|45.3|43.8|19.1|5|95|
|Current Ratio|1.72|1.4|0.9|0.2|6.8|
|Net Income / Total Assets|0.021|0.017|0.045|-0.35|0.4|


**Observations:**

- Summary statistics highlight the spread of financial ratios.

- Some features show outliers, reflecting financial instability in certain firms.

- Only ~3% of companies are bankrupt.

- ROA(C) shows more outliers than Operating Gross Margin (OGM).

- Bankrupt companies tend to have lower ROA relative to OGM.

## **2. Data Balancing**

### **2.1 Class Weighting**

Class weighting adjusts the importance of each class during model training instead of modifying the dataset. By assigning greater weight to bankrupt companies, the model better captures minority cases without creating synthetic data, which is inappropriate for this extreme imbalance.

**Logistic regression configuration:**

- Elastic net penalty

- SAGA solver

- l1_ratio = 0.5

- class_weight = "balanced"


_Note: SMOTE has been removed from the methodology due to extreme class imbalance._

---

## **3. Modeling Approaches**

### **3.1 Logistic Regression with Class Weighting**

Binary classification model using logistic regression with class weighting. Performance metrics include R^2, accuracy, sensitivity, and specificity, compared before and after weighting.

### **3.2 Elastic Net Regression**

Elastic net regression handles high-dimensional, collinear predictors through combined L1 (LASSO) and L2 (Ridge) penalties:

- High-dimensional data: many predictors relative to observations.

- Sparsity: unimportant coefficients shrink to zero.

- Elastic Net mixing factor (alpha): 1 = full LASSO, 0 = full Ridge.

- Hyperparameter optimization for alpha and regularization strength (lambda) ensures generalization.


---

## **4. Summary of Steps**

1. Load and inspect dataset.

2. Apply class weighting for modeling.

3. Logistic regression: fit with elastic net penalty and balanced class weights.

4. Elastic Net regression: tune alpha and lambda; interpret coefficients.

5. Model evaluation: compare R^2, accuracy, sensitivity, specificity before and after optimization.


This methodology addresses extreme class imbalance, incorporates insights from financial ratios, and applies advanced regularization techniques to robustly predict bankruptcy.