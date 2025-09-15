- $C(n, r) = \frac{n!}{(n-r)! * r!}$
	- $CR(n, r) = C((n - 1 + r), r)$
- $P(n, r) = \frac{n!}{(n-r)!}$
	- $PR(n, r) = n^r$

### How to solve any combination repetition problem

> Given 30 people, how many different combinations with repetition can you make with 12 people?

1. We split everything into 30 "containers", which only has 29 "barriers", we then add 12 to that. We can convert any *CR* problem into a *C* problem by just doing allat.
2. We have 12 "markers" that we can put in any bucket.  Since we can have repetition, its possible for one bucket to have all the markers.


$$
CR(6, 12) = C(17, 12)

$$