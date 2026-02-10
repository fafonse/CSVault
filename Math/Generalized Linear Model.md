All generalized linear models have 3 characteristics:
1. A probability distribution describing the outcome variable
2. A linear model: $\eta = \beta_0 + \beta_1X_1+...+\beta_nX_n$
3. A *link function* that relates the linear model to the parameter of the outcome distribution: $g(p) = \eta$ or $p = g^{-1}(\eta)$
	- Your link function just converts your output into what you need for your response variable.