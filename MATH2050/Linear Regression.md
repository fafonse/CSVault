
## Simple
Two different variables, $x$ and $y$. One independent, one dependent. Using correlations we try to see if there's any [[Continuous Probability Distributions|patterns]] between the variables. 

 **EX**: *Relationship between seismic activity at an outpost and distance to a nearby volcano.*

### Assumptions
1. $X_{i}$ are assumed to be fixed, non-random quantities
2. $Y_{i}$ is related to $X_{i}$ by the following [[Pearson's Correlation Coefficient|linear relationship]]
	- $Y_{i} = \theta_{0} + \theta_{1}X_{i} + e_{i}$
### Determining the Best Line
When finding the line of best fit, we can just find which line has the least deviation from the points. What we can do is just get the sum of differences (*residuals*) from the line and square/absolute that to find the total difference.

We want our difference to get as close to 0 as possible.

$\hat{\beta_{0}} = \overline{Y} - p\overline{X}$
$\hat{\beta_{1}} = p_{x,y}\frac{\hat{theta}_y}{}$

### Finding the y-intercept
To find the y-intercept you need to make a hypothesis to see if you need a y-intercept or not.
For, $y=mx + b + \epsilon$:

$H_{0}: b=0$
$H_{1}: b \neq 0$

### Homoscedasticity
The condition that the [[White Noise|white noise]] ($\epsilon$) amount doesn't change as $X_{i}$ changes. A violation of  this assumption is pretty bad so we gotta check for it.

We can do this by just drawing a scatter plot with our line of fit. If the point deviation increases as $X_{i}$ changes, we can assume that we do not have Homoscedasticity.

### Normality
Use a [[Q-Q Plot|Q-Q plot]] of the errors to make sure that the errors are [[Continuous Probability Distributions#Normal Distribution|normally distributed]]. If it isn't normally distributed we transform $Y_{i}$ based on what type of deviation it is.
If it's a right-skew use $log()$, $\sqrt{()}$, $\frac{1}{r}$ transformations.
If it's a left-skew use $r^2$ or $exp()$


## Multiple