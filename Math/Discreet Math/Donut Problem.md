> Given $x_{1} + x_{2} + x_{3} = 15$, how many combinations are there?


## Condition Types:

### At least:
*At least X of the choices must be chocolate donuts*
$CR(n, r) \rightarrow CR(n + r - X - 1, r - X)$
### Exact match:
*$X$ choices must be sprinkle donuts*
$CR(n, r) \rightarrow CR(n-x, r)$
### At most
*Up to 4 donuts can be glaze*
A bit more complicated than the rest. We have to use the process of elimination for this.

1. Find the *at least* and *exact match* conditions that are the "inverse" of the *at most* condition.
2. Count the number of combinations that both have, and add them up
3. Subtract that number from the number of unrestrained possibilities
4. Now you have your number of restrained possibilities!

This process is the same in approach as [[Removing Bad Choices]]. 