Also known as *merging*, it's just creating one new table from a bunch of old ones.

**Parameters**:
- *left* table
- *right* table
- *key*
	- What you're basing your joins on
	- Generally a observation ID, row #, etc.

## Left / Right

When doing a *left join*, you prioritize keeping the records present in the left table. Usually this would be used if you're trying to extend the data present in one table with those in another.

- Left joining a `player_kills` table with `player_deaths` on the `player_id` would create a new table that's all of the `player_kills` with their death counts (but no new observations from the right table)

## Intersection / Inner
You only keep the observations that both tables have.

- Inner joining `player_kills` and `player_deaths` on `player_id` would only include `player_id`s that are in both tables. A player only in `player_kills` or `player_deaths` would not be added in.

## Union / Outer
Combine all records in both tables into a large single one. This will introduce a bunch of *NaN* if your tables don't share all of their observations. 