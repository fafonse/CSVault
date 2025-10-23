
$H_{n} =$ The complement of your hypothesis. When your $H_{u}$ is wrong, your $H_{n}$ must be right.
$H_{a}$ = What you're trying to prove. Like your actual hypothesis

1. Have a null and alternate hypothesis.
2. Select an alpha ($\alpha$) value, this is your max error
3. Choose a test statistic
	- [[T Distribution|T-test]]: Working with samples, and population [[Standard Deviation|STD]] isn't known
	- Z-test: For proportions or when population STD is known
4. Calculate the test statistic 
5. If $p < \alpha$, then you can reject your null hypothesis, otherwise your null is true.

## Two Sample Testing

*P-values:*
- **Left-tailed:** testing if $\mu_{1} < \mu_{2}$
	- `p = stats.t.cdf(t, df)`
- **Right-tailed:** $\mu_{1} < \mu_{2}$
	- `p = 1 - stats.t.cdf(t, df)`
	- $df = n - 1$
- **Two-tailed:** $\mu_{1} \neq \mu_{2}$
	- `p = 2 * (1 - stats.t.cdf(t, df))`
	- $df = n - 1$