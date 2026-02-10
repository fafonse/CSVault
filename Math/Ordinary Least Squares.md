A model that fits a dependent to an independent variable, and produces the amount of standard error from a [[Linear Regression|linear fit]] by finding the least squares in the sum of differences.

## Input
- $x\rightarrow$ Independent variable
- $y\rightarrow$ Dependent variable

## Output
- $r\rightarrow$ correlation coefficient
- $R^2\rightarrow$ coefficient of determination
	- $R^{2} = \frac{\text{Explained Variation}}{\text{Total Variation}} = 1 - \frac{\text{Unexplained Variation}}{\text{Total Variation}}$
	- Our $R^2$ is your fraction of explainable noise compared to [[White Noise|white noise]].
	- A good model is usually >$\%70$, and an amazing model would be >$\%90$
- $P(constant)\rightarrow$ the [[Hypothesis Testing|p value]] used to determine if you need a [[Linear Regression#Finding the y-intercept|y-intercept]] for your model
- $P(\text{y})\rightarrow$ the p value used to determine if you need a slope for your model