Date Created: 2024-04-02
References: #ref/NONE
Tags: #theorem #probabilistic-method #graph-theory

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Property B Pluhar Probabilistic Lower Bound

There is some constant $c>0$ so that every $n$-uniform hypergraph with fewer than $cn^{1/4}2^n$ edges has [[Property B]]. In particular, $m(n) = \Omega(n^{1/4}2^n)$.

```

<i>Proof.</i> Consider the following randomized greedy algorithm. Let $\sigma$ be a randomly chosen ordering of the vertices of $H$. Color the vertices of $H$ one by one in the following way. At step $i$, color the vertex $\sigma(i)$ red, unless it would make an edge monochromatic, in which case, color it blue instead. 

By design, there are clearly no monochromatic red edges once this procedure terminates. Suppose the edge $f = \{\sigma(i_1), \ldots, \sigma(i_n)\}$ is monochromatic blue, with $i_1 < \cdots < i_n$. Each of these vertices was colored blue so as to prevent some other edge from being monochromatic red. In particular, there are edges $e_1, \ldots, e_n$ where $|e_i\cap f| = 1$ and each vertex in $e_i$ precedes the vertices in $f$ according to $\sigma$ (except, of course, on the intersection). Call two edges that intersect in this way a *simple pair*. The probability that two edges of $H$ form a simple pair w.r.t. $\sigma$ is 
$$
\frac{(n-1)!\cdot (n-1)!}{(2n-1)!}.
$$
Consequently, if $m = |E(H)|$, then a union bound shows that the probability that there is a simple pair is at most
$$
\binom m2 \frac{[(n-1)!]^2}{(2n-1)!} = \frac 2n\binom m2\binom{2n}{n}^{-1}.
$$
By [[Stirling's Approximation]], $\binom {2n}{n} \approx \frac{4^n}{\sqrt{\pi n}}$, so this is less than 1 when $m \approx (\frac{n}{\pi})^{1/4}2^n$.