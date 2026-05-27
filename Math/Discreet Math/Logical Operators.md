Different operations we can do with binary variables/[[Proposition|statements]].
The basis of all computer science.

## Main 4
The most common logical operators used in everyday programming. The least common of these is the *XOR*, but its still more popular than the rest.

### NOT
Given $p$, return the opposite of $p$. 
The math symbol is an exclamation point in front of the variable: $!p$

### AND
Given $p$ and $q$, both must be true for the condition to return true.
The math symbol is a up-pointing arrow, $p \cap q$. 

### OR
Given $p$ and $q$, *at least* one variable is true.
The math symbol is a cup shape, $p \cup q$

### XOR
Exclusive OR
Given $p$ and $q$, one may be true, but both at once returns false. 
Written out as $p \oplus q$
## Implication

Can be thought of as `not(p) or q`.
Written out as $p\rightarrow q$.

Anytime $p$ is false, assume the whole thing is true.
Anytime $q$ is true, assume the whole thing is true.

Only returns false when $p$ is true and $q$ is false.

### Variations

**Converse**: $q \rightarrow p$
**Inverse**: !$p \rightarrow$ !$q$
**Contrapositive**: !$q \rightarrow$ !$p$

> Apparently a lot of people jump from implication to the converse, creating a common logical fallacy