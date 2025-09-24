## Uniform Distribution
- Equal probability across [a, b]
- **PDF**: $f(x)=1/(b-a)$
- Mean: $(a+B)/2$
- Variance: $(b-a)^2/12$
- Example: Dice roll

## Exponential Distribution
- Models time between [[Discrete Probability Distributions#Poisson|Poisson]] events
- Find chances of success within a period of time
- **PDF**: $f

>[!example]
>**Data**: Call center logs
>**Example**: If calls arrive on average every 2 minutes, the *time between calls* follows $Exponential(\lambda = 0.5$ $per$ $minute)$
>**Question**: What's the probability of waiting more than 5 minutes for a call?

>[!info] Python Usage
>Using `scipy`, you have to input the *rate*, not the *average*
- In python you have to put in the the *rate*, not the average
	- In the example, the average is 2 minutes, while the rate is 0.5 per minute