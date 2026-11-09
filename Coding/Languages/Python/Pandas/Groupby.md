The function used to [[Math/Statistics/Data Reshaping/Groupby|group categories in data]]. 

We can use `df.groupby` to generate a `groupby` object that is a dictionary of each group and their associated row index.

```python
grouped_df = immunizations_df.groupby('School Type')
# Group each school by it's type (middle, high, elementary)
```

- The `groupby` function by itself returns a `groupby` object, which is a dictionary where each group is a key, and each key has a list of all the row indices that fit into the group.

## Agg Function
Serves to both *apply* and *combine* the results on a `GroupBy` object.

```python
# .agg({'Column' : 'agg_function})
grouped_means = grouped_df.agg({'Total Enrollment':'mean'})
# We can also pass a *list* of functions to apply
grouped_stats = grouped_df.agg({'Total Enrollment': ['mean', len, 'mode', 'sum', 'min', 'max', 'count']})
```

**Aggregation functions:**
- *mean*
- *len*
		- Don't put in quotation marks when used
- *mode*
- *median*
- *sum*
- *min*/*max*
- *count*