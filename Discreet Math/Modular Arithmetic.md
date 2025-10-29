
## Congruency

When two numbers *a* and *b* have the same result with $mod m$ 

$a \equiv b = (a \pmod m = b \pmod m)$

1. Two congruent numbers have their difference as a multiple of $m$.
	- $(12 \equiv 27) \pmod 5$, therefore $(27 - 12 )| 5$
2. Let $m$ be a positive integer, $a$ and $b$ are only congruent if there is an integer $k$ such that $a = b + km$.

## Changing Bases

Given any integer $n$, you can represent it as a sum of $x = a_{k}b^k + a_{k-1}b^k-1 + ... + a_{1}b + a_{0}$.
In this case, we call it ***base $b$ expansion of $n$***. We don't call it anything special for base 10, as that's the default for most math.

This just means that you can represent any integer in any base. AKA, you can represent any integer in base-2 (binary), base-10, or hex (base-16). 

> Example with 23
> Base-10: $23 = 2*10^1 + 3*10^0$
> Base-2 (Binary): $23 = 1*2^4 + 0*2^3 + 1*2^2 +1*2^1 + 1*2^0$ (10111)
> Base-3: $23 = 2*3^2 + 3^1 + 2$

### Converting from Base10
1. Divide your number ($n$) by your base ($b$) and find the remainder
2. Divide your quotient ($q$) by $b$ and repeat until $q=0$
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

### Converting to Base10
Using Horner's method, we can convert to base10 with as few multiplication as possible.

```python
def toBase10(s, alphabet): # this works for base16, using strings
b = len(alphabet)
x = 0
for c in s:
	index = s.find(c)
	x = x * b + index
return x
```

Starting left to right, we begin with the first number. For demonstration, I'll convert $1202_{3} \rightarrow 1202_{10}$.

1. Start with the first number (1)
2. Multiply by the base and add the next digit
	- $1 * 3 + 2 = 5$
3. Use that old number and repeat until you reach the end
	- ($5 * 3 + 0 = 15$)

### Long Division/Multiplication

#### Multiplication

The same as regular long multiplication, but when you have to carry over a number, convert that number to it's extension in base $b$. Then long add all the other bits together.


## Basic Math Algorithms

### Multiplication

A general long multiplication algorithm takes $O(N^2)$, while there's another one that takes $O(N^{1.585})$. However that one has a shit ton of overhead that only makes it viable with extremely long digit counts.

> For multiplication algorithms, keep in mind that $N$ can mean either the length of digits, or the actual integer size of the product/divisor


### Division

Stick to grade school long division. Algorithm recommended by book is hot dogshit.

### Exponential
$512^{644}\mod645$

Instead of finding $512^{644}$, we do little steps at a time and mod by 645 as we do each step.
This only works if we're doing exponential then immediately after modulus.

`pow(512, 644, 645)` - Use the built-in python function, and add your mod as a third parameter

## Prime Numbers

### Theorems

1. Every number can be written as a product of it's primes.
	$12 = 2 * 2 * 3$

### Algorithms

#### Finding Prime Factors
1. Divide by the smallest prime number first (usually 2)
2. Divide by that number as much as possible, then move to the next smallest prime

> [!example]
> $72 = 2 * 36$ 
> $72 = 2 * 2 * 18$
> $72 = 2 * 2 * 2 * 9$
> $72 = 2 * 2 * 2 * 3 * 3$
> $72 = 2 * 2 * 2 * 3 * 3 * 1$