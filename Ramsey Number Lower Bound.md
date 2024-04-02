Date Created: 2024-04-01
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Ramsey Number Lower Bound

If $\binom nk 2^{1-\binom k2} < 1$, then $r(k,k) > n$. In particular,
$$
r(k,k) \geq \frac{k}{e\sqrt 2}2^{k/2}.
$$

```

<i>Proof.</i> Randomly red-blue color the edges of $K_n$, where red and blue are chosen with equal probability, each edge's color chosen independently. The probability that any particular $k$-clique is monochromatic is $2\cdot 2^{-\binom k2}$ since there are two colors to choose from and $\binom k2$ edges.