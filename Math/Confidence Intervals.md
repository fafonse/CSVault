1. Compute the sample [[Measures of Center|mean]] and [[Standard Deviation|standard deviation]].
2. Use a distribution to find the margin of error
	- $MOE=t*(\sigma / \sqrt{n})$
	- Use [[T Distribution|t-distribution]] if sample size is 30-50 big
		- For $t$, use the [[Percent-Point Function|PPF]] at $x= (1- \frac{\alpha}{2})$, which gives the $t$ critical value, and include `df=len(sample)-1`
	- Use [[Discrete Probability Distributions#Binomial|binomial]] distribution if the outputs are binary (1 or 0)
		- You need the [[Point Estimate|point estimate]] of the variable and the *mean*.
		- Find the critical z-value
			- Normal distribution PPF at $x=1 - \frac{alpha}{2}$
		- Use z-value to find the $MOE$
			- $MOE = z*\sqrt{\hat{p} * (1 - \hat{p}) / n}$
			- $n$ in this case being amount of data points (column size)
3. Construct the interval by doing $\pm$ to the margin of error

## Business interpretation
We can use the confidence interval to find the relationship between the true mean and the mean.
- `ci_upper > sample_mean` - True mean could be *greater than* the sample mean
- `ci_lower < sample_mean` - True mean could be *lower than* the sample mean