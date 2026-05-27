> Given a weighted coin with a $2/3$ chance of getting heads, what are the chances that you get 4 heads out of 7 coin flips?

CR(7, 4) - At least 4

We have a bit string here, either tails or heads

## 7.1 way
- We can find the number in [[Pascal's Triangle]], using the $C(7, 4)$ as coordinates, with 7 as $x$ and 4 as $y$. ($35$)
- Find the probability of each part of the triangle by dividing by $2^r$, which is the probability of getting $x$ amount of heads, with $x$ being the distance from the left.

> This does not account for differing probabilities, however in 7.2 we do...

## 7.2 way
- Instead we do $\frac{1}{2}^4 * \frac{1}{2}^3$, where we split up that $2^r$, and the left side is the probability of heads, and the right is the probability of tails
- For a weighted coin, we just replace the heads side with $2/3$, and the tails with $1/3$, changing our odds