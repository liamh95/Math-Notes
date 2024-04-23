Date Created: 2024-04-01
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method #ramsey-theory/ramsey-numbers 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Ramsey Number Lower Bound

If $\binom nk 2^{1-\binom k2} < 1$, then $r(k,k) > n$. In particular,
$$
r(k,k) \geq 2^{k/2}.
$$

```

<i>Proof.</i> Randomly red-blue color the edges of $K_n$, where red and blue are chosen with equal probability, each edge's color chosen independently. The probability that any particular $k$-clique is monochromatic is $2\cdot 2^{-\binom k2}$ since there are two colors to choose from and $\binom k2$ edges. Union bounding over all $\binom nk$ cliques of size $k$, the probability that there is some monochromatic $k$-clique is at most
$$
\binom nk 2^{1-\binom k2}.
$$
As long as this is strictly less than 1, then there must be some 2-coloring with no monochromatic $k$-clique ([[Probabilistic Method Basic Idea]]). Since $\binom nk \leq \frac{n^k}{k!}$ ([[Binomial Coefficient Simple Estimates]]), if we set $n = \lfloor 2^{k/2}\rfloor$, this quantity is indeed less than 1. Using $\binom nk \leq (\frac{ne}{k})^k$, we can actually set $n = \frac{k}{e\sqrt 2}2^{k/2}$. 

