Your missing data by default might use the `NA` tag, which can cause headaches down the line. So instead, you might have other plans.

- Replace with python `None`
- Replace with a value that fits the rest of the data formats
	- If gender is `1` or `0`, you can give the missing columns `-1` 
- Replace with the column [[Measures of Center|mean]]

This can greatly skew a distribution however.