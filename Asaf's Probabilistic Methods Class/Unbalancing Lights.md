Date Created: 2024-04-09
References: #ref/NONE
Tags: #theorem #probabilistic-method/first-moment-method 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Unbalancing Lights

Let $A\in \{\pm 1\}^{n\times n}$. Then there are vectors $x,y\in \{\pm 1\}^n$ such that
$$
x^TAy \geq \left(\sqrt{\frac{2}{\pi}} + o(1)\right)n^{3/2}.
$$

```

<i>Proof.</i> Choose $y\in \{\pm 1\}^n$ uniformly at random and let
$$
R_i := \sum_{j=1}^n a_{ij}y_j
$$
be the $i$-th component of $Ay$. Since $A$ is fixed, $a_{ij}y_j$ is a Rademacher random variable, so $R_i$ has the distribution of a sum of independent Rademachers. Intuitively, we expect each $R_i$ to be around $\sqrt n$ in absolute value, so if we just choose $x$ to have the appropriate signs, we can make $x^TAy$ around $n^{3/2}$. This can be made more precise using the [[Central Limit Theorem]]. Or, we can just do it manually.

If $n$ is even, then $|R_i|$ can only take even values, so
$$
E[|R_i|] = 2^{-n}\sum_{d=-n}^n|d|\Pr[R_i = d] = 2^{2-n}\sum_{j=1}^{n/2}j\binom{n}{\frac{n+2j}{2}} = 2^{1-n}\sum_{j=1}^{n/2}(n-2j)\binom{n}{j}.
$$
Using the identity $k\binom nk = n\binom{n-1}{k-1}$, the above simplifies down to
$$
n2^{1-n}\sum_{j=1}^{n/2}\binom nj - n2^{2-n}\sum_{j=1}^{n/2}\binom{n-1}{j-1}.
$$
Using the fact that $\sum_{j=0}^{n/2}\binom nj = 2^{n-1} + \frac{1}{2}\binom{n}{n/2}$ when $n$ is even, we see that this is equal to
$$
n2^{1-n}\binom{n-1}{\lfloor(n-1)/2\rfloor}.
$$
When $n$ is odd, use the fact that $\sum_{j=0}^{\lfloor n/2\rfloor}\binom nj = 2^{n-1}$ to obtain a similar result. In any case, the result follows from [[Stirling's Approximation]] and the [[First Moment Method]].