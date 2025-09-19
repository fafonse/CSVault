> Given $x_{1} + x_{2} + x_{3} = 15$, how many combinations are there?


## Condition Types:

### At least:
$CR(n, b) \rightarrow CR(n, b/2)$
### Exact match:
$CR(n, b) \rightarrow CR(n-1, b)$
### At most
A bit more complicated than the rest. We have to use the process of elimination for this.

1. Find the *at least* and *exact match* conditions that are the "inverse" of the *at most* condition.
2. Count the number of combinations that both have, and add them up
3. Subtract that number from the number of unrestrained possibilities
4. Now you have your number of restrained possibilities!
This process is the same in approach as [[Removing Bad Choices]]. 