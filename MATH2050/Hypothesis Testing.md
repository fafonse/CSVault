
$H_{n} =$ The complement of your hypothesis. When your $H_{u}$ is wrong, your $H_{n}$ must be right.
$H_{u}$ = What you're trying to prove. Like your actual hypothesis

1. Have a null and ultimate hypothesis.
2. You need the [[T Distribution|t-statistic]] if you're working with samples.
3. Find your P value 
	- $P(t_{0} > t)$
4. If $p < \alpha$, then you can reject your null hypothesis.

## Z-Test
$$Z=\frac{\hat{p} - p_{0}}{\sqrt{\frac{\hat{p}(1-\hat{p})}{n}}}$$
**Parameters:**
- *count* - Count of the tracked variable
- *nobs* - Count of the number of observations
- *alternative* = Can be *larger*, *smaller*; The alternate hypothesis
- *value* = hypothesized value you believe the successes is in the larger population
>[!info] Python Usage
>```python
>import statsmodels.stats.proportion.proportions_ztest
>proportions_ztest(count, nobs, value=x, alternative)
>```
