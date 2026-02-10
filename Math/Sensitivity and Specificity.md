A measure of your predictor model's accuracy.

> For a visual representation use a [[ROC Curve]]
## Sensitivity
A test's ability to identify positive results
$P(\text{Test} + | \text{Condition} +) = P(+|\text{lupus}) = 0.98$

When your test has low sensitivity, it has a high chance for *false positives*, also known as a *type I error*.

Your sensitivity is the amount of true positives out of the total positive results.

## Specificity
A test's ability to identify negative results
$P(\text{Test} - | \text{Condition} -) = P(-|\text{no-disease}) = 0.74$

When your test has low specificity, it has a high chance for *false negatives*, also known as a *type II error*.

Your specificity is the amount of true positives out of the total positive results.

## Causes/Fixes
If your model has a significantly different specificity and sensitivity, you can adjust the model to try and minimize...