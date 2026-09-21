Determines if two categorical variables are independent or not.
You get a [[P-Value|p-value]] and an *expected results* table. That table shows the *expected counts* if the variables are independent.

> Does NOT require [[Normal Distribution|normality]].

## Assumptions
Data must be two [[Categorical|categorical]] variables.
- Each sample should be independent
- Sample size should be large enough
	- 5 counts per each cell

## Python Example

```python
# problem setup
table = [[7, 9, 24],[129,  46,  215]]
# Star Trek Blue/Gold/Red shirt fatalities (are red shirts disposable?)
# 7 blue, 9 gold, 24 red dead
# 129 blue, 46 gold, 215 red alive
# results

stat, p, dof, expected = chi2_contingency(table)

print('Statistic: {}'.format(stat))

print('P Value: {}'.format(p))

print('Expected Frequencies')

print(expected)
```

The statistic value and p-value aren't really useful for reading this. Since $p=0.04$ we can assume there is some statistically significant relationship here. However, the more important information is in the *expected frequencies*. In this example, blue and gold shirts die a lot less than expected if shirt color had no statistical significance.