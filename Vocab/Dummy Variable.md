When you have a categorical variable and you create new columns for the categories.


## Example

Given a table with city types (small, medium, large), we have to make some dummy variables for it to play nice with linear regression.

| City_size | Small | Medium | Large |
| --------- | ----- | ------ | ----- |
| Small     | 1     | 0      | 0     |
| Medium    | 0     | 1      | 0     |
| Large     | 0     | 0      | 1     |
Sometimes you don't even need the last row as it's calculated from the missing ones.