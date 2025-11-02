Numbers which have no divisors except themselves and $1$. 
## Theorems

1. ***The ratio of the number of primes not exceeding $x$, with $x/\ln{x} \rightarrow 1$ as $x \rightarrow \infty$
	- Since both approach 1, we can assume they're roughly the same at large amounts
	- We can calculate the chances of finding a prime number at these large amounts
2. ***Every number can be written as a product of it's primes.***
	$12 = 2 * 2 * 3$
3. ***There's an infinite number of primes, and we never run out as we go to infinity***
	1. Assuming there's a finite number of primes, we can multiply all of them into integer $x$. 
	2. Given $x$, there must be a number that is $x+1$, which would be just outside the range of all known prime numbers
	3. $x+1$ would therefore be a prime number itself, adding one to the pile. We can repeat this *ad infinitum*, therefore there's an infinite number of primes
## Algorithms

### Finding Prime Factors
1. Divide by the smallest prime number first (usually 2)
2. Divide by that number as much as possible, then move to the next smallest prime

> [!example]
> $72 = 2 * 36$ 
> $72 = 2 * 2 * 18$
> $72 = 2 * 2 * 2 * 9$
> $72 = 2 * 2 * 2 * 3 * 3$
> $72 = 2 * 2 * 2 * 3 * 3 * 1$

### Generating Primes

#### Sieve of Eratosthenes
Ancient algorithm great for finding smaller primes (not insane numbers)

**Inputs:**
$n$ - Biggest number you'll test if it's prime

1. Start with an Boolean array, one for each number until limit $n$
	- Initialize all indexes to **true**
2. Starting with $2$, set it as your "mark"
3. Skipping by two's and starting at our mark, we set every number we land on to **false**
4. Go back to your mark and move it to the next number in order that's set to **true**
5. Repeat until your mark gets to $n$