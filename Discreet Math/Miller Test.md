An algorithm that determines if a number is prime or not over [[Monte Carlo Problems|multiple calls]].

When it says yes, its 75% certain. In order to make sure that the number is prime, we can just run the test a lot to reduce the chance of error.

## Method


```python
from random import randint

def Miller(n):
    t = n - 1
    s = 0
    while t % 2 == 0: # while t is odd
        t = t // 2
        s += 1
    b = randint(2, n-1)
    # Tests now
    if pow(b, t, n) == 1:
        return True
    for j in range(s):
        if pow(b, (pow(2, j) * t), n) == n-1:
            return True
    return False
```

Repeating the algorithm 20x leads to a failure chance of $\frac{1}{4}^{20}$, or less than 1 in a trillion chance of failure.

>[!info] Python specifics
> Remember to use `remainder = pow(b, e, n)` instead of `remainder = b ** e % n`. The `pow()` function is more optimized for the mod operation compared to the regular way.

1. $n$ is our number we want to test
2. Let $n-1=2^{s}t$, where $s$ is a positive integer and $t$ is an odd positive integer.
	- We divide $t$ by 2, starting with $n-1$. Every time we get an even integer, we divide by 2 again, adding 1 to $s$.
	- For $n=113$, we could set $s=4$ and $t=7$
	- $113 = 2^{4} * 7$
3. We set $b$ to a random integer between $(2, n-1)$ inclusive
	- This is what makes the algorithm different every time we run it
4. To pass Miller's test we have several conditions that can be fulfilled
	1.  $b^{t}\mod n == 1$ , return `true`
	2. For each $j$, from (0, $s-1$) inclusive, if $b^{2^{j}*t} \mod n== n-1$ we can return `true`
5. If none of the past tests do not pass, we can for sure claim that the number is a composite