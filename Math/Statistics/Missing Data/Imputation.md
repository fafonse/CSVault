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

> [!example] Missing data for dog barks
> Lets say you have a dataset about dogs.
> - You have dog breed, bark loudness, and weight.
> - You have to impute for the bark loudness.
> Starting with a cell that has a weight of 100lb and a doberman, you find the average of the other 100lb dobermans (lets say 60db).
> Impute every cell within that weight+breed group with 60db (only for missing bark data).