## Uniform Distribution
- Equal probability across [a, b]
- **PDF**: $f(x)=1/(b-a)$
- Mean: $(a+B)/2$
- Variance: $(b-a)^2/12$
- Example: a dice roll

## Exponential Distribution
- Models time between [[Discrete Probability Distributions#Poisson|Poisson]] events
- Find chances of success within a period of time
- **PDF**: $f

>[!example]
>**Data**: Call center logs
>**Example**: If calls arrive on average every 2 minutes, the *time between calls* follows $Exponential(\lambda = 0.5$ $per$ $minute)$
>**Question**: What's the probability of waiting more than 5 minutes for a call?

### Python Usage
Using `scipy`, you have to input the *rate*, not the *average*
 - In the example, the average is 2 minutes, while the rate is 0.5 per minute
 - False, just do `scipy.stats.expon.cdf(x, scale)`, where scale is the time it takes and $x$ is where you want to sample from the graph.
 - To find the *median*, do `stats.expon.ppf(0.5, scale)`, since the median is just the middle value

## Normal Distribution
- Most values are average, with few outliers
	- Think human height/weight, most are average
- You can't find the probability by finding the y-value, but instead must find the area under the curve
	- You can't find $p(x)$, but you can find $p(n < x < r)$
- $f(x) = \frac{1}{\sigma * \sqrt{2*\pi}} * e^{}$
	- Two main parameters: the *mean* and the [[Standard Deviation|standard deviation]].

> You can generate fake normal data using `scipy.stats.rvs(x, n, size=x)`, where size determines the size of the dataset.

### Standard Normal Distribution
 A normal deviation where the *mean* is 0 and the *standard deviation* is 1. To compare to a normal distribution, you must [[Standardization|standardize]] the CPD's.

### Identifying a Normal Distribution
- Draw a histogram or qplot
	- If the histogram has the normal bell curve, its a normal distribution
	- If the qplot is similar to $f(x) = x$, then its a normal distribution

### Normalizing Data
Some equations and formulas have assumptions that the data is normal, but sometimes a large skew/tail can mess these up. Normalizing is like squishing and moving the data so that it fits in "frame" for those calculations.

How to do it:
- Take the log of the data to get it closer to a normal distribution if its skewed