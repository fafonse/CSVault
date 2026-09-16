
> Measure possibility of *n* occurrences of an event happening in a certain timeframe
- Coming from [[Binomial Distribution|Binomial distribution]]
	- Fix the expectation $\lambda=np$
	- Let the number of trials $n\rightarrow \infty$

>[!info] Python Usage
>```python
>import scipy.stats as stats
>Y = stats.poisson(λ)
>Y.pmf(X) # find probability of n == X
>Y.cdf(X) # find the probability of n <= X occuring
>p = 1-Y.cdf(15) # find p(n >= X) occuring
>```

>[!warning] Regression Usage
>Poisson distribution uses **counts** for measurement. You can't use it with regular regression functions, you gotta use a [[Poisson Regression]] specifically.

## Example
- **Data**: NYC 311 calls per day
- **Example**: Suppose the average of nose complaints per day is 12
	- The number of complaints on a given day follows $Poisson(\lambda=12)$
- **Question**: What's the probability of tomorrow having less than 15 complaints?
	- What's the probability of tomorrow having more than 15 complaints?