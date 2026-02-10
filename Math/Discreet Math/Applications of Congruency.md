## Hashing

## Linear Congruential Method
A method to generate pseudo-random numbers that stays consistently with a seed.

**Values**
- $X_0$: Our seed value
	- $0 \leq X_0 < m$
- $a$: Our multiplier
	- $2 \leq a < m$
- $c$: our increment
- $m$: The modulus


1. Start at $x_0$ (seed value)
2. Given any $x_n$,, $x_{n + 1} = (ax_n + c) \mod m$

## Hashing
Modulus can be used for hashing functions to fill out an array randomly without any conflicts.