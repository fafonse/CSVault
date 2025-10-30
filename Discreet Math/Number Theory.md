---
aliases:
  - Chapter 4
---
Math surrounding integers. Foundation to [[Modular Arithmetic]].

### Theorems
1. **Theorem 1**
	1. if $a | b$ and $a | c$, then $a | (b+c)$[^1]
		- If two numbers share a factor, their sum shares it as well
	2. if $a | b$, then $a | bc$ for all integers $c$
		- If a number has a factor, no matter what you multiply with it, it still has it
	3. if $a | b$ and $b | c$, then $a | c$
		- Given a factor of a factor for $c$, that sub-factor still works for integer $c$
	
2. **The Division Algorithm**
	- Let $a$ be an integer and $d$ a positive integer (dividing $d$ into $a$). Then there are unique integers $q$ and $r$, with $0 \leq r < d$, such that $a = dq + r$.
	  $0 < r < d - 1$  
		- You can get to any $a$ by dividing with a remainder. That $r$ is the remainder.
		- In the book and python, they always have a positive remainder, so the $q$ for a negative $a$, would "overshoot" so there's a positive $r$. However, C++ does have negative $r$ values for mod operations.


[^1]:  The pipe symbol ( | ), is used to denote that in *a | b*, that *a* divides into *b* evenly (no remainder).
