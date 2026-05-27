A [[Linear Regression|linear regression]] model that combines two techniques, LASSO and Ridge, to deal with data with pockets of [[Independent Events|collinearity]] and [[Sparsity|sparsity]].
By blending the two techniques together, you get a regression that's robust to collinearity and sparsity.
## Parameters

Elastic net has something called *hyperparameters*, so aside from optimizing the predictor variables, we must also optimize the hyperparameters for our dataset.

**Alpha ($\alpha$)**:
- Controls the amount of regularization
- Using `scikit.learn`, we instead use $C$, which is the inverse of $\alpha$
**L1 Ratio**:
- Controls the mixing between LASSO and Ridge models
- A L1 of zero means a completely LASSO model, while a L1 of one is a completely Ridge model

## Optimization

Because elastic net is a *penalized* approach, we cannot rely on the p-values the same way we do with linear regressions. However, we can instead use a LASSO pre-pass to screen out any insignificant coefficients (that's what its built for). 
We can take those p-values from there and plug it into our elastic net for optimized inputs.

When it comes to optimizing our *hyperparameters*, we need to do [[Cross Validation|cross validation]] to find our model accuracy.

### Code Example
```python
from sklearn.linear_model import LogisticRegressionCV

model = LogisticRegressionCV(
    solver="saga",
    penalty="elasticnet",
    l1_ratios=[0.1, 0.5, 0.9], # try multiple l1 + C (alpha) ratios
    Cs=[0.01, 0.1, 1, 10, 100],
    cv=5 # 5 fold cross-validation
)
model.fit(X, y)
```