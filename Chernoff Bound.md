Date Created: 2024-03-04
References: #ref/NONE
Tags: #theorem #probability/concentration-inequalities #probability/tail-estimates

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Chernoff Bound

Let $X_1, \ldots, X_n$ be independent Bernoulli random variables. Let $X$ denote their sum and let $\mu = E[X]$. Then for any $\delta > 0$,
$$
\Pr[X > (1+\delta)\mu] \leq \left(\frac{e^\delta}{(1+\delta)^{1+\delta}}\right)^{\mu}.
$$
It is also true that for any $0<\delta < 1$,
$$
\Pr[X < (1-\delta)\mu] \leq \left(\frac{e^{-\delta}}{(1-\delta)^{1-\delta}}\right)^{\mu}.
$$

By applying the inequality $\frac{2\delta}{2+\delta}\leq \log(1+\delta)$, we obtain
$$
\begin{align}
	\Pr[X > (1+\delta)\mu] \leq e^{-\delta^2\mu/(2+\delta)} ,&\quad 0\leq \delta,\\
	\Pr[X < (1-\delta)\mu] \leq e^{-\delta^2\mu/2} ,&\quad 0<\delta<1,\\
	\Pr[|X-\mu| > \delta \mu] \leq 2e^{-\delta^2\mu/3} ,&\quad 0< \delta < 1.
\end{align}
$$
```

<i>Proof.</i> <% tp.file.cursor(2) %>