A single column of continuous data.

- Series come built in with an *index*
	- By default it's just like a regular 0-based array
	- It's a C data type, `int64`, which means it *can overflow!*
	- Does not have to be unique
- Access/Lookup methods are faster than a [[Dictionaries|dictionary]] or regular list
	- Use `.get()` or `[]`


```python
bands = pd.Series(["Radiohead", "Beatles", "DFA 1979", "Beach Boys"])

bands[0] # Radiohead
```

You can make a series have the index of another series. The index does not have to be numerical.

```python
founded = pd.Series([1985, 1960, 2001, 1961])
bands_founded = pd.Series(founded, bands) # values, index

bands_founded["Beatles"] # 1960
bands_founded.get("DFA 1979") # 2001
```

## Updating
You can update a value by just using it's index.
If you have two cells with the same index, this will update both at the same time.
```python
bands_founded["Radiohead"] = 2026
# 1985, 1960, 1961, 2026
```

If you want to avoid that, you can use `iloc` to update purely on the *positional index*/*position*.
```python
bands_founded.iloc[0] = 1985
# Radiohead, Beatles, DFA1979, Beach Boys
```

## Slicing
You can slice by index using `loc` and by position using `iloc`.
```python
bands_founded.iloc[1:3]
# Beatles, DFA1979, Beach boys
bands_founded.loc["Thom": "Sebastien"]
# Radiohead, Beatles, DFA1979
```

You can get a subset of specified cells by using `loc`/`iloc`/`get`
```python
bands_founded.get(["John", "Brian"]) # Subset of series with Beatles + Beach Boys
bands_founded.loc[["John", "Brian"]]
bands_founded.iloc[[1, 3]]
```

## Masks and Filtering
We can also create mask arrays that only contain boolean values.
```python
mask = bands_founded > 1961
# Radiohead, DFA1979
```

This creates a new array, a copy, that we can use to get a subset from the main array.
```python
bands_founded[mask]
# One liner
bands_founded[bands_founded > 1961]
```

## Data Exploration
You can use `.count()` to show how many non-null values are in the series.
> To drop *null* values, use `.dropna()`

```python
numbers = pd.Series([1, 2, None, 4, 6, 5])
numbers.count() # 5
```

We can also get the [[5 Number Summary]] from using `.describe()`

## Sorting
We can sort series super easily using `.sort_values`.
```python
numbers.sort_values()
# 1, 2, 4, 5, 6
numbers.sort_values(ascending=False)
# 6, 5, 4, 2, 1
```

The index will stay the same in a separate column however. We can reset it using `.reset_index`.

```python
# We need to drop or else old index is perserved in a seperate column
numbers.reset_index(drop=True)
```

## Data Manipulation
You can do basic math operations like you would with a mask.
```python
print(numbers * 10)
# 10, 20, 40, 50, 60
```

You can also apply a function or dictionary to the set using `.map()`
```python
numbers.map({1:3, 4:"Grr", 12:"wolf!"}) # Using a dicitonary
# 3, NaN, "Grr", NaN, NaN
```