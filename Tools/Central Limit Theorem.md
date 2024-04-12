Date Created: 2024-04-09
References: #ref/NONE
Tags: #theorem #probability/tail-estimates #probability/concentration-inequalities

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Central Limit Theorem

Let $X_1, X_2, \ldots$ be a sequence of iid random variables with $E[X_i] = \mu$ and $\text{Var}[X_i] = \sigma^2 < \infty$. Then the random variables
$$
\frac{X_1 + \cdots + X_n - n\mu}{\sqrt n}
$$
converge to the normal random variable $\mathcal N (0, \sigma^2)$ in distribution.

```

<i>Proof.</i> <% tp.file.cursor(2) %>