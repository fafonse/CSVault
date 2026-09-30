A model that fits a dependent to an independent variable, and produces the amount of standard error from a [[Linear Regression|linear fit]] by finding the least squares in the sum of differences.

> [!warning] Unrealistic Results
> Because OLS fits using a linear model, sometimes it can create unrealistic results.
> This happens because it just subtracts/adds to a variable based off another, with no context. So if your `age` has an inverse relationship with `wealth` and `height`, then a super short and poor kid can come out with a negative age value.
## I/O
**Input:**
- $x\rightarrow$ Independent variable
- $y\rightarrow$ Dependent variable

**Output:**
- $r\rightarrow$ correlation coefficient
- $R^2\rightarrow$ coefficient of determination
	- $R^{2} = \frac{\text{Explained Variation}}{\text{Total Variation}} = 1 - \frac{\text{Unexplained Variation}}{\text{Total Variation}}$
	- Our $R^2$ is your fraction of explainable noise compared to [[White Noise|white noise]].
	- A good model is usually >$\%70$, and an amazing model would be >$\%90$
- $P(constant)\rightarrow$ the [[Hypothesis Testing|p value]] used to determine if you need a [[Linear Regression#Finding the y-intercept|y-intercept]] for your model
- $P(\text{y})\rightarrow$ the p value used to determine if you need a slope for your model

## Python Usage
```python
import statsmodels.formula.api as smf

# Age *depends* on *categorical variable* pclass *categorical variable* sex
# And fare and parch
m = smf.ols(formula="age ~ C(pclass) + C(sex) + fare + parch", data=imputed_age_df)
```

- [[Categorical]] variables must be identified and labeled as such
	- The model automatically generates [[Dummy Variable|dummy variables]] to use as continuous-ish data.

### Interpreting Results
```
                            OLS Regression Results                            
==============================================================================
Dep. Variable:                    age   R-squared:                       0.242
Model:                            OLS   Adj. R-squared:                  0.236
Method:                 Least Squares   F-statistic:                     41.33
Date:                Wed, 30 Sep 2026   Prob (F-statistic):           1.69e-57
Time:                        19:43:39   Log-Likelihood:                -4114.2
No. Observations:                1043   AIC:                             8246.
Df Residuals:                    1034   BIC:                             8291.
Df Model:                           8                                         
Covariance Type:            nonrobust                                         
====================================================================================
                       coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------------
Intercept           38.6591      1.403     27.549      0.000      35.905      41.413
C(pclass)[T.2]     -11.2177      1.290     -8.694      0.000     -13.749      -8.686
C(pclass)[T.3]     -15.8803      1.227    -12.947      0.000     -18.287     -13.473
C(sex)[T.male]       2.7301      0.843      3.240      0.001       1.077       4.384
C(embarked)[T.Q]     4.9222      2.060      2.390      0.017       0.881       8.964
C(embarked)[T.S]     2.2963      1.062      2.162      0.031       0.212       4.380
fare                -0.0055      0.009     -0.585      0.559      -0.024       0.013
sibsp               -3.1802      0.464     -6.857      0.000      -4.090      -2.270
parch               -0.7039      0.522     -1.347      0.178      -1.729       0.321
==============================================================================
Omnibus:                       26.070   Durbin-Watson:                   1.962
Prob(Omnibus):                  0.000   Jarque-Bera (JB):               27.630
Skew:                           0.370   Prob(JB):                     1.00e-06
Kurtosis:                       3.296   Cond. No.                         377.
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
```

- Dependent variable shows what is we're comparing to
- The `coef` column shows the correlation number between results
	- Like a [[Pearson's Correlation Coefficient]]
	- Not limited $-1 \rightarrow 1$, but instead is closer to a slope number
		- For `C(pclass)[T.3]`, passengers tend to be 15 years younger than tier 1 passengers
		- For `C(sex)[T.male]`, passengers tend to be 3 years older than women
- Remember to look at the [[P-Value]] to check if the `coef` is actually statistically significant