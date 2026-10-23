 A model of [[Human Factors|human movement]].
 
- Predicts the time required for rapid, aimed movement to a target
	- EX: moving a mouse pointer
- Depends on distance + width of target
- Tradeoff speed or accuracy

> Assumes *low error rate* and *user expertise*. Not for people who don't know what a computer is.

## The Law

Parameters:
- Time to move to target
- Distance to target
- Width of the target
	- Law was originally for *one-dimensional* problems

$$\text{Index of Difficulty} = log_2(\frac{Distance}{Width} + 1)$$

## Extensions / MT
The law was later extended to include *MT*, or *movement time*.

$$ \text{Movement Time} = a + b*DI$$
Your $a$ and $b$ variables depend on what task you're doing as well as the input method. 