Find the next permutation in lexicographical ordering
1. Find target
2. Replace with digit to its right
3. fill numbers to the right of the target smallest to biggest, starting at the target
	   - `[0, 2, 3]` would be `[1,2,3]`, not `[1, 0, 2]`
4. After running out of numbers that are $n + 1$, then use the place in the combination to the left
 
This is just binary counting, but replacing 1's with arbitrary amounts.

> [!info] The algorithm in the book is 1 based, while the Mr. Stander's implementation is 0-based. So in the book `L[1] == first element` while the teacher uses `L[0] = first element`
*High key you could just do the book algorithms correctly and just subtract one from everything in the list to make it zero-based*
## Algorithm
**Given C(6, 4), list all the permutations, IN ORDER from least to greatest**

1. $C(6, 4) = \frac{6!}{2!4!} = 15$ :  amount of permutations
2. Since we have 6 options, we lay them out as `[0, 1, 2, 3, 4, 5]`
	- Smallest amount of 4 picks is `[0, 1, 2, 3]`
	- However, the next combination isn't `[0, 1, 3, 2]`
		- Because this is combination, *without* repetition
3. To prevent repeated combinations, we sort them so that all numbers are always in the same position
4. To create a new addition, do `[0,1,2,4]`, since we want to keep the far right low, so the next 2 additions have the end replaced and nothing else
5. Now we change the second-last, and the smallest option is `3`, so we get `[0,1,3,4]`, since we can't do 2 since its sorted