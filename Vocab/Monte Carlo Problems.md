Random sampling being used to sidestep complicated math. Confidence goes up as you increase the number of samples.


## QA Example
> Lets say you're high at work at a chip facility. You're slow, and only fill up 2 bins with bad chips. Your boss is coming in soon, and you have a whole bin you need to filter. Bad batches have 1/10 of their total as bad chips. You can only check a couple, what do you do?

1. We gotta start by checking the bin. We pull randomly from it, and check lets say 3 chips.
2. If we ever get a single bad chip, we throw out the whole barrel, but that's a 1/10 chance, and there's like a thousand in there.
3. Instead, we can increase our confidence if we pull more good chips. If we pull 3 good chips, thats a $\frac{9}{10} * \frac{9}{10}* \frac{9}{10}$, which is a 30% chance to have a bad barrel.
4. If we had the time, it would take **135** pulls to get a one in a million chance of being wrong.