## Expectations

Ensure that all of your steps that you do in code are in your final PDF. For example, when building the model, show how your $R^2$ changes before and after optimization, and show which variables you discard from the model.

Basically describe your code steps in your final paper.

## Draft Plan

For our dataset we'll need to *balance* the data first. We have like 5% of our dataset as bankrupt companies and the rest are normal. Since we have such a large disparity (and we're predicting for the minority), we have to balance the dataset before we apply any predictor models.

For balancing we should use the SMOTE method, which generates new pseudo-samples from the minority to balance the data.

For our models, I'm thinking we can do a logistic regression (binary response) and a elastic net model. The elastic net is a bit more complicated since we have to optimize our hyperparameters ($\alpha$, $l$)
### Elastic Net
Work on using a more complicated method to describe your model when it has multiple collinear variables. (Elastic Net - regularized logistic)

Explain the new model, any **terms that you do not know must be fully dumbed down/explained**.
- [[Sparsity]]
- High-dimensional data
- LASSO (L1) penalty
- Ridge (L2) penalty
- loss
- $\alpha$ is the mixing factor. 1 is full LASSO, 0 is full Ridge.