A regression used when your response variable is continuous and your predictor variables are not correlated with each other.

> If your data has a *binary* response variable, then use a [[Logarithmic Regression]]
## Simple
Two different variables, $x$ and $y$. One independent, one dependent. Using correlations we try to see if there's any [[Continuous Probability Distributions|patterns]] between the variables. 

 **EX**: *Relationship between seismic activity at an outpost and distance to a nearby volcano.*

### Assumptions
1. $X_{i}$ are assumed to be fixed, non-random quantities
2. $Y_{i}$ is related to $X_{i}$ by the following [[Pearson's Correlation Coefficient|linear relationship]]
	- $Y_{i} = \theta_{0} + \theta_{1}X_{i} + e_{i}$
### Determining the Best Line
When finding the line of best fit, we can just find which line has the least deviation from the points. What we can do is just get the [[Residuals|residuals]] from the line and square/absolute that to find the total difference.

We want our difference to get as close to 0 as possible.

$\hat{\beta_{0}} = \overline{Y} - p\overline{X}$
$\hat{\beta_{1}} = p_{x,y}\frac{\hat{theta}_y}{}$

### Finding the y-intercept
To find the y-intercept you need to make a hypothesis to see if you need a y-intercept or not.
For, $y=mx + b + \epsilon$:

$H_{0}: b=0$
$H_{1}: b \neq 0$

### Verifying Models

#### Homoscedasticity
The condition that the [[White Noise|white noise]] ($\epsilon$) amount doesn't change as $X_{i}$ changes. A violation of this assumption is pretty bad so we gotta check for it.

We can do this by just drawing a scatter plot with our line of fit. If the point deviation increases as $X_{i}$ changes, we can assume that we do not have Homoscedasticity.


#### Linearity

Linearity assumes that the error is linear and doesn't curve when plotted. You can check this with the same [[Residuals|residual]] scatter plot as homoscedasticity.

![[Pasted image 20251108152738.png]]`

#### Normality
Use a [[Q-Q Plot|Q-Q plot]] of the errors to make sure that the errors are [[Continuous Probability Distributions#Normal Distribution|normally distributed]]. If it isn't normally distributed we transform $Y_{i}$ based on what type of deviation it is.
If it's a right-skew use $log()$, $\sqrt{()}$, $\frac{1}{r}$ transformations.
If it's a left-skew use $r^2$ or $exp()$



### Testing the Model
In this case $y_{p}$ is our predicted data and $y_{o}$ is the original data.

Mean Absolute Error: $\frac{\sum{}|y_{p} - y_{o}|}{n}$

## Multiple

As you add multiple values to your linear regression, your $R^2$ increases as you gain more information. Even if your added predictor variable has no correlation to the response variable, then your $R^2$ increases anyways.

### Optimization

There's a tradeoff. Increase your accuracy ($R^2$) and your model complexity increases (by a fuck ton). 
The computational power also increases, as adding a variable adds a new dimension to the matrix math behind the scenes.

Because of this tradeoff, we want to keep our model as simple as possible

### Differences from Simple
There are two ways of adding all of your extra predictor variables
1. Forward-adding
	- Append your new variables to your current linear regression
2. Backwards-subtraction
	- Do all of your variables at once and subtract the ones you don't need at the end
	- We can use the P-values to see if the predictor is significantly needed for the regression
	- Even as we take out variables, our accuracy still remains *increased*


### Estimation and Interpretation
We start with the same basic concept as simple linear regression, where we try to find the line of best fit by minimizing our deviation from our predictors. 

### Categorical Variables
When using categorical variables (i.e fire type, water, ground, etc) we must change them in order to work with our formulas.
There are two main methods:
1. [[Dummy Variable|Dummy Variables]]
	- Turning categories into Boolean columns
	- Don't make them real 

### Missing Data
For categorical data, make sure to use the `drop_first=True` argument to ensure that missing data doesn't taint the good data.

### Example Code

```python
import pandas as pd
import numpy as np
import scipy.stats as stat
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as smf
from statsmodels.formula.api import ols

df = pd.read_csv("datasets/advertising.csv")

# find correlation
print(df.corr())

# Since TV and sales have high correlation, we set the vars
x = df[["TV", "Newspaper", "Radio"]]  # independent variables
y = df.TV  # dependent

# We can't graph this because we're working with 4D graphs (impossible to view lol)
# plt.scatter(x, y)
# plt.show()

# add a constant column cause we need it for some fucking reason
# add a ton of 1's so that we can predict b
# y = mx + nb, where n is what we're finding
# the model just needs something there to predict
x = smf.add_constant(x)  # This just adds a column of 1's

model = smf.OLS(x, y).fit()

print(model.summary())
# Take the coeff column and use that as your coefficients for your linear regression
# There will be errors
# Sales = 4.67 + 0.0544*TV + 0.0003*Newspaper + 0.1070*Radio
# R-squared is your accuracy rating (.903 or 90.3% accuracy)

# Now we have to find if all the variables need to be weighted
# We use the P values (P>|t|)
# For each value H{n}: val == 0 / H{a}: val != 0
# If they're small, then we can assume that it matters
# If they're over our alpha then we disregard it (it doesn't significantly matter)

predictions = model.predict(x)  # predict based off our model using an X

dataF = {"pred": predictions, "y": y}
dataF = pd.DataFrame(dataF)

# We shouldn't see any patterns in this plot (homoscedasticity)
# The positive and negative errors should cancel out close to 0
dataF["errors"] = dataF.y - dataF.pred  # calculate errors from model

plt.scatter(x.TV, dataF.errors)  # linearity
plt.show()

# qqplot
smf.qqplot(
    dataF.errors
)  # since this is pretty linear, we can assume a normal distribution of errors
plt.show()

print(
    model.predict([1, 10])
)  # start at 1, says that if you make $10k in sales, how many tv's can you sell
# Sold 7.53 TV's
# You can get very insane numbers if you use super large numbers

# since we also don't see any outliers, we don't worry about those

# Sales = 6.67 + 0.0555 * TV
```