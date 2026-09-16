- A and B independent when adding more information/variables doesn't change the outcome
- $P(A\cap B)$
- Mutually exclusive independent

- Two events A and B are independent when
	- $Pr(A\cap B) = Pr(A)Pr(B)$
- A set of events $\{A_{i}\}$ is independent in case
	- $Pr(\cap_{i}A_{i}) = \prod_{i} Pr(A_{i})$

> Ex: If you roll two dice, the chance of you landing two sixes is the same as if you rolled each dice separately and got six on both. The dice's outcome is independent from one another.

## Testing for Categorical Counts (Chi-Square Test)
When you're testing if *counts* (not probabilities) are independent, you need to change it up a bit.

- You need your expected amount for your counts. It'll be given as a percent, and you multiply that by $n$ to get your expected count.
	- $E = \frac{\text{(row total)(column total)}}{\text{total sample size}}$
- Your expected count is the amount you expect if the variables are **independent**
	- Therefore, the closer the expected is to the *observed* measurements, the more independent the variables are

### Example
Given the table:
![300](https://i.imgur.com/63coG7w.png)

For the category *Democrat: Favor*, we could find the $E$ with $E=\frac{(285)(202)}{500}$, which gives us the expected proportion


### Python Usage

```python
import pandas as pd
import scipy.stats as stats

	contingency = pd.crosstab(df['x1'], df['x2'])
	
		# Run chi-square test
	chi2, p, dof, expected = stats.chi2_contingency(contingency)
	
		# Frequency table for expected values
	print(pd.DataFrame(expected, index=contingency.index, columns=contingency.columns))
```