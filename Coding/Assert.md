Throws an exception if your code doesn't do what it expects. This exists in some way or form in about every language.

If it doesn't exist you can think of it like this:
```python
if condition == False:
	raise AssertionError()
```

This is a great way to [[Data Validation|validate data]] or any sort of debugging.