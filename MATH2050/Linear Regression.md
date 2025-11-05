
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

### Linearity
We look at a regression plot

### Normality
Use a [[Q-Q Plot|Q-Q plot]] of the errors to make sure that the errors are [[Continuous Probability Distributions#Normal Distribution|normally distributed]]. If it isn't normally distributed we transform $Y_{i}$ based on what type of deviation it is.
If it's a right-skew use $log()$, $\sqrt{()}$, $\frac{1}{r}$ transformations.
If it's a left-skew use $r^2$ or $exp()$


## Multiple

As you add multiple values to your linear regression, your $R^2$ increases as you gain more information. Even if your added predictor variable has no correlation to the response variable, then your $R^2$ increases anyways.

### Optimization

There's a tradeoff. Increase your accuracy ($R^2$) and your model complexity increases (by a fuck ton). 
The computational power also increases, as adding a variable adds a new dimension to the matrix math behind the scenes.

Because of this tradeoff, we want to keep our model as simple as possible

### Differences from Simple
There are two ways of adding all of your extra predictor variables
1. Forward-adding
	- Append your new variables to your current linear regression
2. Backwards-subtraction
	- Do all of your variables at once and subtract the ones you don't need at the end
	- We can use the P-values to see if the predictor is significantly needed for the regression
	- Even as we take out variables, our accuracy still remains *increased*


### Estimation and Interpretation
We start with the same basic concept as simple linear regression, where we try to find the line of best fit by minimizing our deviation from our predictors. 

### Categorical Variables
When using categorical variables (i.e fire type, water, ground, etc) we must change them in order to work with our formulas.
There are two main methods:
1. [[Dummy Variable|Dummy Variables]]
	- Turning categories into Boolean columns

### Missing Data
i fucking hate this lecturer he's so unbelievably fucking shit at his job