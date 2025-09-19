## Categories of counting problems:
- Permutations
	- There's `n` objects in a set, pick `r` of them
	- Order Matters
- Combinations
	- There's `n` objects in a set, pick `r` of them
	- Order doesn't matter
- Permutations with Repetition
	- Same as permutations, but you can have repetitions in your set
- Combinations with Repetition
	- Same as combinations, but add repetitions to your set
	- Because order doesn't matter, BBC == BCB
	- Way more "equal" sets


## Example:
> How many ways can we select a group of 3 students, out of 5 students, to stand in line for a picture.
1. Because its a picture, orders matters.
2. Because we can't have clones IRL, there is no repetition
This is a regular **permutation** problem.

Lets go through the choices one by one.
1. After selecting one guy, our set is reduced by one. Our first "bucket" had a chance of 1/5
2. We select another, reducing our set again. Second bucket 1/4
3. Another, our set reduced. Third bucket 1/3
Our set has a combined mix of 5\*4\*3, which is **60 possibilities**.

We can use this solution for all problems like `P(n, r)`. If we can pick everything in a set, the answer for `P(n, n) = n!`. If `r < n`, we use the factorial, but only multiply up to `(n-r)`, instead of `(n-n)`