Date Created: 2024-04-02
References: #ref/NONE
Tags: #theorem #simple-estimates

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Binomial Coefficient Simple Estimates

For any $0 \leq k \leq n$,

$$
\left(\frac nk\right)^k \leq \binom nk \leq \frac{n^k}{k!}\leq \left(\frac{ne}{k}\right)^k.
$$

```

<i>Proof.</i> For the upper bounds, we have
$$
\binom nk = \frac{n(n-1)\cdots (n - (k-1))}{k!} \leq \frac{n^k}{k!}.
$$
Now if we look at the expansion $e^k = \sum_{j=0}^\infty \frac{j^k}{j!}$, we see that $e^k  >k^k/k!$. Substituting this in gives $\binom nk \leq (\frac{ne}{k})^k$. As for the lower bound, we have $\frac nk \leq \frac{n-1}{k-1}$, so inductively, $\frac nk \leq \frac{n-t}{k-t}$ for all $0\leq t \leq k-1$, hence
$$
\left(\frac nk\right)^k = \frac nk \cdots \frac nk \leq \frac nk\cdot  \frac{n-1}{k-1}\cdots \frac{n-(k-1)}{1} = \binom nk.
$$