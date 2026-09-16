An alternative to over/under sampling, where instead of directly changing the data, we just change how much the data *matters*.

Use class weighting when:
- Minority class is small
- Data is continuous
- Used with linear models
- Interpretability and stable coefficients matter

It's better to use SMOTE instead when:
- Model is non-linear
- Need to boost *recall*, and weighting doesn't do it for you

## Example Code

Usage with a regular logarithmic regression:
```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split

# Example: X and y are your features and labels
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=67, stratify=y
)

model = LogisticRegression(
    class_weight="balanced",
    solver="liblinear"  # good default for small/medium datasets
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

```

Usage with an [[CS Notes/MATH2050/Logarithmic Regression|logarithmic]] [[Elastic Net Regularization|elastic net regression]]:
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(
    penalty="elasticnet",  
    solver="saga",
    l1_ratio=0.5,
    class_weight="balanced" # important part here
)
model.fit(x_train, y_train)
```
