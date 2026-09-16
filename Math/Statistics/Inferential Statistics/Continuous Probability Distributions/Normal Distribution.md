---
aliases:
  - Gaussian Distribution
---
Your standard bell curve. Also known as a *Gaussian distribution*.

- Most values are average, with few outliers
	- Think human height/weight, most are average
- You can't find the probability by finding the y-value, but instead must find the area under the curve
	- You can't find $p(x)$, but you can find $p(n < x < r)$
- The $f(x) = \frac{1}{\sigma * \sqrt{2*\pi}} * e^{}$
	- Two main parameters: the *mean* ($μ$) and the [[Standard Deviation|standard deviation]] ($\sigma$).

> You can generate fake normal data using `scipy.stats.rvs(x, n, size=x)`, where size determines the size of the dataset.


## Standard Normal Distribution
 A normal deviation where the *mean* is 0 and the *standard deviation* is 1. To compare to a normal distribution, you must [[Standardization|standardize]] the CPD's.

## Identifying a Normal Distribution
- Draw a histogram or qplot
	- If the histogram has the normal bell curve, its a normal distribution
	- If the [[Q-Q Plot]] is similar to $f(x) = x$, then its a normal distribution

## Normalizing Data
Some equations and formulas have assumptions that the data is normal, but sometimes a large skew/tail can mess these up. Normalizing is like squishing and moving the data so that it fits in "frame" for those calculations.

How to do it:
- Take the log of the data to get it closer to a normal distribution if its skewed