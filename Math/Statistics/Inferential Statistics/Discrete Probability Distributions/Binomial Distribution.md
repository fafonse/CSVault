"Summarizes" the outcome of $n$ [[Bernoulli Distribution|Bernoulli]] random variables. 

> If applied to coin flips, we would flip a 100 coins and count how many times heads came up. We don't care about the individual flips.


- $n$ draws of a *Bernoulli distribution*
	- $X_{i}$~$Bernoulli(p)$
	- $X=\sum{n}X_{i}$
	- Defined by $Bin(n, p)$
		- Needs $n$ draws and the $p$ of success
- The *mean* is $np$
- Variance is $np(1-p)$
- Random variable $X$ stands for the number of times that there was success
- Track the distribution on a [[Probability Mass Function|PMF]] to find its likeliness


>[!info] Python Usage
>```python
>from scipy import stats
>X = stats.binom(n, p) # x = random binomial var
>X.pmf(X) # find probability of X successes in the binomial distribution
>```
>

## Example:
- **Data**: A dataset of email campaigns with open rates (success/failure)
- **Example**: On average, per 100 emails 30 are opened
	- Follows $Bin(100, 0.3)$
- **Question**: What's the probability of 40 emails being opened?