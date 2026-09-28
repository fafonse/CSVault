Replacing missing values with something useful.

## Pivoted data
Lets say the `age` value is missing in a dataset. Start off by finding the *imputed* ages by finding the average age per *type of group*. Like if your dataset is about employment, find the age of employees who are male and in tech, the average age of women in construction, etc. for every group. Then you use that to replace the missing data in the dataset.
```python
pd.pivot_table(data=imputed_age_df.dropna(subset=['age']), # < result

               index=['pclass','embarked','sex'], # group by these

               values='abs_age_error', # idk this part

               aggfunc='mean') # find the mean of the age
```
This can often be done with a [[Pivot Table]].