## Bernoulli
- 2 Possible outcomes (binary, 1 or 0)
- Imagine $P$ as the probability of success (1)
- $E(X) = p$
	- Expected Value = $p$
- $Var(X) = p(1-p)$

## Binomial
- $n$ draws of a Bernoulli distribution
	- $X_{i}$~$Bernoulli(p)$
	- $X=\sum{n}X_{i}$
	- Defined by $Bin(n, p)$
		- Needs $n$ draws and the $p$ of success
- Random variable $X$ stands for the number of times that there was success
- Track the distribution on a [[PMF]] to find its likeliness

>[!info] Python Usage
>```python
>import scipy.stats as stats
>X = stats.binom(n, p) # x = random binomial var
>X.pmf(X) # find probability of X successes in the binomial distribution
>```
>
#### Example:
- **Data**: A dataset of email campaigns with open rates (success/failure)
- **Example**: On average, per 100 emails 30 are opened
	- Follows $Bin(100, 0.3)$
- **Question**: What's the probability of 40 emails being opened?

## Poisson
> Measure possibility of *n* occurrences of an event happening in a certain timeframe
- Coming from *Binomial* distribution
	- Fix the expectation $\lambda=np$
	- Let the number of trials $n\rightarrow \infty$

>[!info] Python Usage
>```python
>import scipy.stats as stats
>Y = stats.poisson(λ)
>Y.cdf(X) # find the probability of n <= X occuring
>p = 1-Y.cdf(15) # find p(n >= X) occuring
>```

>[!warning] Regression Usage
>Poisson distribution uses **counts** for measurement. You can't use it with regular regression functions, you gotta use a [[Poisson Regression]] specifically.

#### Example
- **Data**: NYC 311 calls per day
- **Example**: Suppose the average of nose complaints per day is 12
	- The number of complaints on a given day follows $Poisson(\lambda=12)$
- **Question**: What's the probability of tomorrow having less than 15 complaints?
	- What's the probability of tomorrow having more than 15 complaints?
