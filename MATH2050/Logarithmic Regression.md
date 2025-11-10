A [[Generalized Linear Model|GLM]] used to model a [[Discrete Probability Distributions#Binomial|binary]] categorical variable using numerical and categorical predictors. 

## Example

In this example, we'll look at the [donner party](https://en.wikipedia.org/wiki/Donner_Party), where out of 87 pioneers, 40 of them died.
Comparing the gender to the death status, 20 men died compared to 5 women. Both genders had 10 deaths for each.
Comparing age, we can see that the mean non-survivor age was around 35, while the mean survivor age was around 26.

Since age and sex seem to have some impact on the survivability, we can make a predictor model to see if a given person had a good chance of surviving. However, we can't use a [[Linear Regression|linear regression model]] since our response variable is categorical (Boolean). 

In this case we use a logarithmic regression since we have a [[Discrete Probability Distributions#Binomial|binary]] response variable. We can't map a [[Continuous Probability Distributions|continuous]] linear model into our response variable straight up, since the continuous variables have an output range of ($-\infty, \infty$). Therefore we need to use a link function to "convert" our results into our binary response.

Using our link function, we can find our $p$ of survival. Below 0.5 results in death, above is survival.

## Logit Function
The [[Generalized Linear Model|link function]] that connects $\eta$ to $p$.
There's a lot of options, but the most commonly used is the logit function.
$$\text{logit}(p) = \log{\frac{p}{1 - p}}, \text{ for } 0\leq p\leq 1$$
The logit function takes a value between 0 and 1 and maps it to a value between $(-\infty, \infty)$
The little bit that is $\frac{p}{1-p}$ is your *odds ratio*, which you can graph with a [[Odds Ratio Curve|OR curve]].

Here's the inverse of that:
$$g^{-1}(x) = \frac{exp(x)}{1 + exp(x)} = \frac{1}{1 + exp(-x)}$$
The inverse logit function takes a value between $(-\infty, \infty)$ and converts it to a binary result.