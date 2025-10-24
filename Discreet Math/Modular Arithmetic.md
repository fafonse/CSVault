
## Congruency

When two numbers *a* and *b* have the same result with $mod m$ 

$a \equiv b = (a \pmod m = b \pmod m)$

1. Two congruent numbers have their difference as a multiple of $m$.
	- $(12 \equiv 27) \pmod 5$, therefore $(27 - 12 )| 5$
2. Let $m$ be a positive integer, $a$ and $b$ are only congruent if there is an integer $k$ such that $a = b + km$.

## Integer Representations

Given any integer $n$, you can represent it as a sum of $x = a_{k}b^k + a_{k-1}b^k-1 + ... + a_{1}b + a_{0}$.
In this case, we call it ***base $b$ expansion of $n$***. We don't call it anything special for base 10, as that's the default for most math.

This just means that you can represent any integer in any base. AKA, you can represent any integer in base-2 (binary), base-10, or hex (base-16). 

> Example with 23
> Base-10: $23 = 2*10^1 + 3*10^0$
> Base-2 (Binary): $23 = 1*2^4 + 0*2^3 + 1*2^2 +1*2^1 + 1*2^0$ (10111)
> Base-3: $23 = 2*3^2 + 3^1 + 2$

### Finding the extension
1. Divide your number by your base and find the remainder
2. Divide your quotient by your base and repeat until your quotient is 0
3. The answer is the column of remainders

$753_{10} \rightarrow 753_{2} = 1000111101$

$753 = 2 * 376 + 1$
$376 = 2*188 + 0$
$188 = 2*94 + 0$
$94 = 2 *47 + 0$
$47 = 2 * 23 + 1$
$23 = 2 *11 + 1$
$11 = 2 * 5 + 1$
$5 = 2 * 2 + 1$
$2 = 2 * 1 + 0$
$1 = 2 *0 + 1$