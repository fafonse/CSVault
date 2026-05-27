A method to test a model, similar to a test-train split. However, instead of using a single test-train split we rotate our training data around the dataset.

Every "rotation" is called a *fold*, and we just compare different folds to get a fuller accuracy measurement.

Useful for the following situations:
- Dataset is small
- Results vary due to [[White Noise|randomness]]
- You're tuning [[Elastic Net Regularization#Parameters|hyperparameters]]