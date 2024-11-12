Date Created: 2024-09-20
References: #ref/NONE
Tags: #theorem #probability/concentration-inequalities  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Tail bound with variance

```ad-theorem
title: Tail bound with variance

Let $X_1, \ldots, X_n$ be independent random variables with finite mean and variance. Let $X = \sum_{i=1}^n X_i$ and $\sigma^2 = \text{Var}(X) = \sum_{i=1}^n \text{Var}(X_i)$. Suppose that $|X_i - E[X_i]| \leq M$ with probability 1 for all $i$. Then for any $t\geq 0$,
$$
\Pr[X \geq E[X] + t\sigma] \leq \exp\left( -\frac{\frac{1}{2}t^2}{1 + \frac{1}{3}\frac{M}{\sigma}t} \right).
$$

```

<i>Proof.</i> <% tp.file.cursor(2) %>