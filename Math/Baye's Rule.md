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

> [!example] How to do ts
> 	Formula is a major bitch, so here's it without the greek
> 1. Calculate [[Probability#Conditional Probability|conditionals]] for posterior and complement
> 	- Calculate conditional probabilities for cases where target is met
> 	- Calculate conditional probabilities for cases where target is **not** met
> 2. Calculate the probabilities of the posterior and complement
> 	1. Multiply all posterior conditionals and posterior probability 
> 	2. Multiply all complement conditionals and complement probability
> 3. Find the probability of your target case happening
> 	- `overall_prob = yes_prob / (yes_prob + no_prob)`
> 
 
 
 - When given continuous variabilities, segment them out into categories. Like chopping up continuous percentages into [[Percentile and Quarters|percentiles]]. Then you can just track those categories as separate outcomes.