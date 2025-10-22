A test statistic used when working with proportions, or when the population standard deviation is known.
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




> If the population standard deviation is unknown and you're working with samples, use the [[T Distribution|T-test]] instead.