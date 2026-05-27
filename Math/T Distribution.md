The standard distribution formula used when testing *samples*, not population. Has a fatter "tail" than a normal distribution, and more uncertainty.
$$
t=\frac{\overline{x} - \mu}{s/\sqrt{n}}
$$

Parameters:
- $\overline{x} =$ sample mean
- $\mu=$ hypothesized population mean
- $s=$  sample standard deviation
- $n=$ sample size

## Two Sample Variation
$$
t=\frac{\overline{x}_{1} - \overline{x}_{2}}{SE}
$$
What the Standard Error $SE$ is depends on your sampling.

### Different Groups
Use Welch's T-test

### Same Groups (Paired-Sample)
Same individuals, just measured twice.
Compute the differences, then do a one-sample t test using that difference.

$$
t=\frac{\overline{d}}{s_{d}/\sqrt{n}}
$$
$S_{d}$ stands for the standard deviation of the differences