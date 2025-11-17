## Euclidian's Theorem
Finding inverse of 8 mod 59.
Basically find $8 * x \mod 59 = 1$, where $x$ is our inverse. Basically you must find what factors can give you 1.

Euclidian's theorem requires that the numbers are [[Relatively Prime|relatively prime]], otherwise they might not have a unique inverse, or an inverse at all.

First find the [[Greatest Common Divisors|GCD]] using Euclidian's other algorithm. However, we use the quotient and the remainder (8 and 3 in the first step), which allows us to get the numbers super small.

> [!example]
> $8 * x \mod 59 = 1$
> $59 = 8 * 7 + 3$
> $8 = 3 * 2 + 2$
> $3 = 2 * 1 + 1$
> $2 = 8 - 2 * 3$
> $1 = 3 - 1 * 2$
> $1 = 3 - (8 - 2 * 3) = -1 * 8 + 3 * 3$
> $1 = -1 * 8 + 3 * 3 * (59 - 7 * 8) = 3 * 59 - 22*8$
> Our answer gives us -22, but because it's negative we add 59 to make it positive.
> $-22 + 59 = 37$
## Fermat's Little Theorem
#todo 