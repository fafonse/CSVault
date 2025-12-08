1. 21 buckets, 4 possible answers. No answer can be done twice in a row.
It's not $3^{21}$,we can't do the same answer in the row, so it would be $4*3^{20}$. Because you answer the first one (4 choices), and for the rest you always have one option missing, so it would be $3^{20}$.

2. How many bit strings len(10) begin and end with two 1's. 
$2^6$, as we remove 4 options from the bitstring.

3. Count the strings of english letters of length 4 or less
$26^4$, since repeats are allowed, and every item afterwards we decrease the exponent to represent the smaller lengths. so $26^4 + 26^3 + 26^2 + 26$

4. How many bit strings beign with two 1's or end with 2 one's
	$2^8 + 2^8 - 2^6$, addition rule used here. $2^6$ is the union of both (4 one's on either end)

5. How many variables can you make of length 7 in c++. Must start with a letter or underbar. Can be followed by digits, letters, or underbars. Repeats allowed.
	$27*37^6$. 27 choices for the first characters, 37 for the rest.

6. If you have 3 treats and 12 horses, how many ways can you give the treats to the horses? You can give a horse more than 1 treat.
	$CR(12, 3)$, since we have 12 places we can put the 3 treats. Or we can call it 12 choices, 3 picks.

7. A group of 10 men and 10 women line up. How many ways to arrange it, if all the women must stand next to each other?
$10! * 11 * 10!$. We can arrange the men however, so it would be $10!$, however the women can be in any of the 11 spaces around them. And those women can be arranged $10!$ ways. 

8. What is the chance that a bit string of length 8 has exactly 3 ones?
$C(8, 3) / 2^8$, since its the probability of it happening once.

9. A shop sells 10 kinds of doughnuts, mom sends you to buy 20. 

10. HOw many permutations of the letters in "alabama" are there?
If there were no repeats, it would $7!$. However since 4 are the same, we can arrange them $4!$ ways, and we must remove those from the total. So our answer is $7! / 4!$

11. What is the next permutation in lexicographical order after "546321"
$561234$. We find the pivot ($x+1$ > $x$) which is $4$ in this example. Then we swap the pivot with the first greatest on the right, in this case $6$. We then take the pivots current position and reverse everything after it to be "inorder", from least to greatest.

12. What are the next two combinations in "1368" given that we are choosing 4 from the set of 1 through 8?
$1378$ and $1456$. With combinations, we add to the one's, then the 10's, etc. When we find a digit we can add to, we "pack" everything afterwards to be ($x, x+1, x+2$, etc)

13. Given a 21 question test, a student answers 1 out of 4 choices. What are the chances they get at least one question right?
It's all OR's, so we must convert it to an AND. So instead of at least one question right, we do every question wrong. Which would be $\frac{3}{4}$ per question, or $\frac{3}{4}^{21}$. We need the complement of that. Or $1 - \frac{3}{4}^{21}$

14. You can choose eight coins from a piggy banks having 100 pennies and 80 nickels.
This is a like a bit string, as every answer can be either *P* or *N*. Order doesn't matter, and repetitions are allowed since you can pick multiple of a coin. So it's $CR(2, 8)$. 

15. A publish has 3000 copies of a book. How many ways are there to to store these books in 3 different warehouses?
$CR(3, 3000)$. We have 3 "buckets" and 3000 "picks". All the books are indistinguishable, so it has to be repetition. Order doesn't matter, since we're just tossing them in there.

16. How many ways are there to distribute 20 different books to 4 different people, so that each gets an equal number of books?
$20! / (5!)^4$, since we have $20!$ picks, but we need to order them into groups of 5, and must be split 4 ways. 

17. How many ways to choose 6 pieces for a chess game, where 3 are white and 3 are black and order doesn't matter. There must be exactly 1 white and black king on each side. They other pieces may repeat. 6 Kinds of pieces per color. 
$CR(5, 2) * CR(5, 2)$ . We have one choice taken from each half, and we add them together. 

18. What's the chance that rolling 2 dice results in a sum of 5?
$4/36$. 

19. Given a lottery of 4 digits, a small prize is awarded if exactly 3 digits are matched. 
$(4*9)/10^4$. We can pick one of the 4 digits to get wrong, and it can be one of 9 choices, since 9/10 numbers are wrong and 1/10 are right. We divide by the total choices to get a probability.

20. Whats the probability that we have a hand in poker with all red or black cards?
We have 52 cards, half of which are red, half are black. So it's C(52, 5)

21. How many wasy can you distribute 2 identical apples ot 4 distinct children? Repeats allowed.
CR(4, 2), which is C(5, 2), which turns into $\frac{5!}{3!2!} = 10$.