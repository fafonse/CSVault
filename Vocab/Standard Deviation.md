$$
\sigma = \sqrt{\frac{1}{N}\sum_{i=1}^{N} \big(x_i - \mu\big)^2}
$$
The average distance that the data *deviates* from the mean of the dataset.

We ain't doing all of this, so instead we can get `numpy` to do it for us with `STD = np.std(dataset)`.