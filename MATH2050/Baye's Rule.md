- Given two events A and B and suppose that $Pr(A) \gt 0$. Then
$$
Pr(B|A) = \frac{Pr(AB)}{{Pr(A)}} = \frac{Pr(A|B)Pr(B)}{Pr(A)}
$$
- $Posterior = Prior * \frac{likelihood}{marginal}$
	- *Posterior* is the data after evidence is considered
	- *Prior* probability is the probability before evidence is considered
	- *Likelihood* probability of even given the evidence is true
	- *Marginal* probability is the chance of the event happening regardless
 - Given some data, how will that effect your probability? ($A$ is the data)
	- $P(A|B)$ is the likelihood of having that data in hand
	- $P(B)$ is the probability before evidence is considered
	- $P(A)$ is the probability under any circumstance

> Bayes' Rule is one of the most important equations for this class, as it's a mathematical way to show if we can update our expectations based on new evidence (learning!)


## Variants

### Naive Bayes' Rule:
1. Multiple variables, but all variables are equally important
2. All variables are independent
	- They can be correlated, but they can't be dependent on each other
$$
Pr(B|X,Y,Z) = \frac{[Pr(X|B)Pr(Y|B)Pr(Z|B)]*Pr(B)}{Pr(X)Pr(Y)Pr(B)}
$$
> When $Pr(X/Y/Z)$ is the same above and below, you can multiply it out, so it's just like a constant you multiply with the $Pr(B)$