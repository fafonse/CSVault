Your inverse modulus is $d$ where $1 \equiv ad \mod m$. Generally requires that $a$ and $m$ are [[Relative Primes|relative primes]].


## Euclidian's Theorem

An extension of the [[Greatest Common Divisors|Euclidean GCD method]]. Basically continue the method until you reach one and do repeated substitutions for your answer.

Being very computationally simple, this method is best for doing it by hand.
It can broken down into three distinct steps.

> For this example we're using $1 \equiv 12d \mod{29}$
### Step 1
Do the [[Greatest Common Divisors|Euclidean GCD method]] and continue it until you have 1 as your remainder.
If you cannot reduce into one, then your numbers don't have a GCD of 1, or a shared inverse likely.

```c
29 = 12 * 2 + 5
12 = 5 * 2 + 2
5 = 2 * 2 + 1
```

### Step 2
Now is the hard part. Start substituting the different numbers into the equation using the previous step as reference. Don't multiply anything together, as the factors will stack very nicely into one another.

You'll know you're done when you have your original $a$ and $m$ in your equation.
```c
1 = 5 - 2(2)
1 = 5 - 2(12 - 2(5)) = 5 - 2(12) + 4(5) = 5(5) - 2(12)
1 = 5(29 - 2(12)) - 2(12) = 5(29) - 10(12) - 2(12) = 5(29) - 12(12)
1 = 5(29) - 12(12)
```

### Step 3
Easy finish here. Just modulus your equation by the one stated in the question. Your factor then tells you the answer.

```c
1 = 5(29) % 29 - 12(12) % 29 /* left side goes to zero */
1 = -12(12) % 29
d = -12 + 29 /* because d is negative, we add on m */
d = 17
```

Viola! Look back at the question, and $d$ is right in front of your eyes! Careful to add on $m$ if $d$ is negative. 
## Fermat's Little Theorem
#todo
This method is best for programming, as it can be done easily with computers.