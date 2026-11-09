When you have data that can be categorized, and you want to do some sort of function on those groups.

> Given a dataset of 1-mile records, what's the average for men and average for women?
## Split-Apply-Combine
The typical steps to compute statistics for groups.

1. Split a dataframe into it's groups
2. Apply a function to each group independently (sum, mean, etc.)
3. Combine the results into a new dataframe

> [!example]
> Given the previously mentioned 1-mile record dataset, how do we get the average times for men + women?
> 1. Split the data into male + female sets
> 2. Apply a *mean* function to each dataset
> 3. Combine the two into one new set showing the results

> Check [[Coding/Languages/Python/Pandas/Groupby|here]] for using this in [[Pandas|pandas]].
### Apply Types
The different categories of functions we apply to each group.

**Aggregation**
- When you want a single value from each group
- Sum, mean, mode, etc.
- Returned dataframe will be the same size as the number of groups
**Transformation**:
- Not summarizing, but editing the values in each group
- [[Normal Distribution|Normalization]], [[Z-Test|Z-score]], etc.
- The output dataframe will be the same size as the input
**Filtration**:
- Discard some groups, according to a boolean function
	- Discard data from insignificant groups
	- Filter data based on a sum or mean
- You get the values back for *some of the groups*
- Your output dataframe is generally shorter than the input (same ordering though)