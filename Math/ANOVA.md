*Analysis of Variance*

A method that determines if the means of 2+ populations are the same. Way easier than doing several [[Hypothesis Testing#Two Sample Testing|two sampled]] tests for every pair.


## Construction

### Assumptions
1. Each factor has a **[[Continuous Probability Distributions#Normal Distribution|normal population distribution]]**
2. Distributions have the **same [[Standard Deviation|variance]]**
	- If the highest/lowest STD ratio is between 0.5 and 2, then that assumption may not be violated
3. The factors are **[[Independent Events||independent]]**

### Hypothesis Building
**Hypotheses:**
$H_{a}$: at least one mean is different (AKA not all means are equal)[^1]
$H_{n}$: all means are equal

**Test Statistic:**
The test statistic is $F$ in this case. It's just the ratio of between group variance compared to the variance within the groups.
$F = \frac{\text{between group variance}}{\text{within group variance}}$

**ANOVA table:**
- For $n$ amount of groups, you create a sample $y$ by drawing a random observation from each group, creating $n$ samples $n$ long.
	- Each $y$ can be represented as $y_{ij}$, where $j$ is the individual observation from $i$ group
- Take the mean of each sample you create as $\overline{y}$

> [!info] Sum of Squares
> Sum of squares for Treatment or the Between Group Sum of Squares (SST)
> $$ SST = \sum_{i=1}^{t}n_{i}(\overline{y_{i}} - \overline{y}..)^2$$
> **Sum of squares for Error or the Within Group Sum of Squares**
> $$SSE=\sum_{i,j}^{}(y_{ij} - \overline{y}_{i})^2$$
> **Total Sum of Squares**
> $$TSS = \sum_{i,j}(y_{ij}-\overline{y}..)^2$$
>
> $TSS = SST + SSE$

## Python Usage
1. Get a response variable
	- You might need to create one if you need to find the difference/effects of some event before and after 
		- `add_column(col[a] - col[b])`
2. Select a model

### [[Ordinary Least Squares|Ordinary Least Squares (OLS)]]
```python
import statsmodels.api as sm
from statsmodels.formula.api import ols

rv = "response variable column"
grouping = "variable that assigns groups (column in data)"
model = ols("differences ~ C(Diet)", data=dataFrame).fit()  # C = category
anova_table = sm.stats.anova_lm(model, typ=2)
```


### Tukey Method

Used for multiple comparison of means, showing which allows you to get more specific and find how different the individual means are from each other. 

Lets you find if $\mu_{1} \neq \mu_{3}$ instead of finding if $\mu_{1} \neq \mu_{2} \neq \mu_{3}$
```python
res = stat()
res.tukey_hsd(df=df_melt,res_var='value',xfac_var='treatements',anova_model='diff ~ C(Diet)')
res.tukey_summary()
```

[^1]: ANOVA is considered [[Hypothesis Testing#Two Sample Testing|two-tailed]]
