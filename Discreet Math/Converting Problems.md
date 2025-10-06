Sometimes you can't find the probability of $E$ directly, so instead find the probability of the complement of $E$. 

Here are some problem types to look out for:
- Anything involving `OR` for probabilities
	- If there's only two events[[CS2100 Midterm Review]] being tracked, we can just use the [[Probability#Basic Probability Properties|addition rule]]
		- For 2+ events, we need to remove the intersections between ALL events (remove intersections in pairs, add back in intersections between all 3). Super huge pain in the ass.
	- The complement of an `OR` problem is always an `AND`
		- Use for anything with >2 events