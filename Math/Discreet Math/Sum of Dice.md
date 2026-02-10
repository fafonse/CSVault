## 2 Dice
For numbers $2\rightarrow7$, your chance to sum up to it is $\frac{n-1}{36}$, maxing out at $\frac{6}{36}$.
For numbers $8\rightarrow12$, it starts decreasing by one as $n$ increases, with 8 having a $\frac{5}{36}$ chance and 12 having a $\frac{1}{36}$ chance. 


## 3 Dice

> How many ways can 3 dice add up to 15?

$x1 + x2 + x3 = 15$

This is a variation of the [[Donut Problem]], but instead with some obvious restrictions. Lets say that they are not constrained between 1-6, and we just say they need to add to 15.
1. Every roll must be a minimum of 1, and a max of 6


### Solving
1. Dice start at 1, not zero. We can translate that to *at least one of each*, dropping our choices from 15 down to 12. 
2. Second constraint is $x<=6$ , so no more than 6. However, since we already have a minimum of 1, we can only pick *5 more*, so our constraint is limited to 5, not 6.
3. What about the patterns subtracted twice? We have to add them back in post, such as numbers like $771$ or $717$.