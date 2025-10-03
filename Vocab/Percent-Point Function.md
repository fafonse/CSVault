The inverse of the [[Continuous Probability Distributions]], where instead of telling you the probability given the time, the function tells you the time it takes to get that probability.

> Ex: If a bus comes around every 14 minutes, how long until 80% of passengers would have seen a bus go by?

> [!info] Python Usage
> ```python
> from scipy import stats
> prob = stats.expon.ppf(0.8, scale = 14)
> ```
> You can use any CDF/PDF type you want, just remember to do `.ppf` for the results
 