A way of filtering strings in a simple, standard way.

## Example 1
Here's the regex for a valid dollar amount following the format `$100.00`.

`\$[0-9]+\.[0-9]{2}$`

- We escape the first dollar sign, as it usually marks the end of the regex
- `[0-9]` just means any amount of digit characters
- We escape the period
- Same `[0-9]` but now we have `{2}` to limit it to only 2 places. 
	- Dollars don't do a tenth of a cent.