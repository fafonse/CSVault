There are different kinds of missing data, which range in their "annoyingness" to fix.

Solutions to missing data:
%% Begin Waypoint %%
- [[Dropping Values]]
- [[Imputation]]
- [[Replacing Missing Values]]

%% End Waypoint %%

## Kinds of Missing Data
Here they are listed from least trouble, to the most:
- **Missing Completely at Random (MCAR)**
	- The probability for the data point to be missing is unrelated to it's value or the value of other variables. Usually very rare
	- *EX: Data is lost in corrupted file*
- **Missing at Random (MAR)**
	- Th e probability for the data point to be missing is not related to its own value, but is related to other observed data. Relatively common.
	- *EX: Respondents stop answering survey questions cause they're bored*
- **Missing not at Random (MNAR)**
	- The probability of the data point missing depends on its value or the value of other variables. Probably the most common
	- *EX: Women are less likely to report their age than men*