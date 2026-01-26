## Expectations

Ensure that all of your steps that you do in code are in your final PDF. For example, when building the model, show how your $R^2$ changes before and after optimization, and show which variables you discard from the model.

Basically describe your code steps in your final paper.

## Draft Plan

For our dataset we'll need to *balance* the data first. We have like 5% of our dataset as bankrupt companies and the rest are normal. Since we have such a large disparity (and we're predicting for the minority), we have to balance the dataset before we apply any predictor models.

~~For balancing we should use the SMOTE method, which generates new pseudo-samples from the minority to balance the data.~~ Actually SMOTE is kinda shit for our situation, since we have a 30:1 majority-minority class ratio. This is so horrendous that SMOTE would probably fuck our model with it's synthetic data points. According to *el ChatGPT*, we can instead do something called **class weighting**, which instead of generating synthetic data just weights our minority class more compared to the majority.

For our models, I'm thinking we can do a logistic regression (binary response) and a elastic net model. The elastic net is a bit more complicated since we have to optimize our hyperparameters ($\alpha$, $l$)
### Class Weighting
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(
    penalty="elasticnet", # 
    solver="saga",
    l1_ratio=0.5,
    class_weight="balanced" # important part here
)
model.fit(X_train, y_train)
```
### SMOTE
We still should have an example of this.

```python
import pandas as pd
import matplotlib.pyplot as plt
from imblearn.over_sampling import SMOTE

data = pd.read_csv('datasets/bankruptcy.csv')
df = pd.DataFrame(data)

x = data.drop('Bankrupt?', axis=1)
y = data['Bankrupt?']
# Before resampling we have like a horrible ratio

smote = SMOTE(sampling_strategy='minority') # resample using smote
x_bal, y_bal = smote.fit_resample(x, y) # new x and y balanced values
print("After SMOTE:\n", y_bal.value_counts())
```
### Elastic Net
Work on using a more complicated method to describe your model when it has multiple collinear variables. (Elastic Net - regularized logistic)

Explain the new model, any **terms that you do not know must be fully dumbed down/explained**.
- [[Sparsity]]
- High-dimensional data
- LASSO (L1) penalty
- Ridge (L2) penalty
- loss
- $\alpha$ is the mixing factor. 1 is full LASSO, 0 is full Ridge.