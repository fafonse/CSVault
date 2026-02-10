$LCD * GCD = n_{1} * n_{2}$
## Greatest Common Divisor
The biggest shared factor of *n* numbers.

EX: (24, 36)
The GCD would be 12 in this instance.

### Finding with Prime Factorization
Find the prime factorizations of both numbers, and basically `AND` the factors together.

EX: (24, 36)
$24 = 2*2*2*3$
$36 = 2*2*3*3$

24 and 36 share $2^2$ and a single $3$.
Therefore, their GCD is $2*2*3=12$

### Euclidean Algorithm
Using the basics of [[Number Theory#The Division Algorithm|number theory]], we can can represent any number as a $a=dq+r$, or as a quotient and remainder.

Setting the bigger number as $a$ and the smaller number as $q$, the GCD of $a$ and $q$ is the same as the GCD of $q$ and $r$. 

> [!Example]
> $GCD(287, 91) =$
> $287 = 91 * 3 + 14$
> $91 = 14 * 6 + 7$
> $14 = 7 * 2 + 0$
> 
> Therefore the GCD of 287 and 91 is *7*

## Least Common Multiple
