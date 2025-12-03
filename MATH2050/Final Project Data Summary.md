

# **Methodology and Data Summary**

  

## **1. Introduction**

  

The dataset used in this study contains financial indicators for companies labeled as either **bankrupt** or **non-bankrupt**. A critical challenge of this dataset is the **extreme class imbalance**: only about **5%** of observations correspond to bankrupt companies, creating a roughly **30:1 majority-to-minority ratio**. This imbalance makes predicting the minority class particularly difficult, as standard machine learning algorithms tend to favor the majority class.

  

To address this, the methodology involves preprocessing, balancing techniques, and advanced modeling approaches such as logistic regression and elastic net regression. All steps performed in code are documented to ensure reproducibility and clarity.

  

---

  

## **2. Data Balancing**

  

### **2.1 Class Weighting**

  

Class weighting adjusts the importance of each class during model training rather than modifying the dataset itself. By assigning greater weight to bankrupt companies, the model can better recognize minority cases without introducing synthetic data, which can destabilize models in extreme imbalances.

  

For logistic regression, the following parameters are applied:

  

* **Elastic net penalty**

* **SAGA solver**

* **l1_ratio = 0.5**

* **class_weight = "balanced"**

  

This configuration handles both collinear predictors and class imbalance effectively.

  

```python

from sklearn.linear_model import LogisticRegression

  

model = LogisticRegression(

    penalty="elasticnet",

    solver="saga",

    l1_ratio=0.5,

    class_weight="balanced"

)

model.fit(X_train, y_train)

```




---

  

## **3. Modeling Approaches**

  

### **3.1 Logistic Regression with Class Weighting**

  

Logistic regression is applied as a **binary classification model**. Using class weighting, the model accounts for the imbalance in bankrupt vs. non-bankrupt companies. Key steps include evaluating the model's **R²** and accuracy before and after weighting to demonstrate improvement.

  

### **3.2 Elastic Net Regression**

  

Elastic net regression extends logistic regression with regularization, particularly useful in datasets with **high-dimensional and collinear features**.

  

Important concepts:

  

* **High-dimensional data:** many predictors relative to observations.

* **Sparsity:** model can shrink unimportant coefficients to zero.

* **LASSO (L1) penalty:** encourages sparsity by forcing some coefficients to zero.

* **Ridge (L2) penalty:** shrinks correlated coefficients together.

* **Elastic Net:** combines L1 and L2 penalties with a mixing factor (\alpha):

  

  * (\alpha = 1) → full LASSO

  * (\alpha = 0) → full Ridge

  

Hyperparameter optimization for (\alpha) and regularization strength (\lambda) ensures the model generalizes well. The final model is evaluated using metrics such as **accuracy, sensitivity, specificity, and confusion matrices**, showing the effect of regularization and class weighting.

  

---

  

## **4. Summary of Steps**

  

1. **Data Preprocessing:** Load and inspect dataset.

2. **Logistic Regression:** Fit with elastic net penalty and balanced class weights.

3. **Elastic Net Regression:** Tune $(\alpha)$ and $(\lambda)$; interpret coefficients.

4. **Model Evaluation:** Compare metrics (R², accuracy, sensitivity, specificity) before and after optimization.

  

This methodology ensures reproducibility, addresses extreme class imbalance, and applies advanced regularization techniques suitable for high-dimensional financial datasets.