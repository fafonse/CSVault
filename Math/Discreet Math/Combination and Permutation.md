## Combinations
- $C(n, r) = \frac{n!}{r!(n-r)!}$ - Find total possibilities
	- $CR(n, r) = C((n - 1 + r), r)$
### How to solve any combination repetition problem

> Given 30 people, how many different combinations with repetition can you make with 12 people?

1. We split everything into 30 "containers", which only has 29 "barriers", we then add 12 to that. We can convert any *CR* problem into a *C* problem by just doing allat.
2. We have 12 "markers" that we can put in any bucket.  Since we can have repetition, its possible for one bucket to have all the markers.
3. $CR(6, 24) = C(29, 24)$
## Permutations
- $P(n, r) = \frac{n!}{(n-r)!}$ - find total possibilities
	- $PR(n, r) = n^r$

