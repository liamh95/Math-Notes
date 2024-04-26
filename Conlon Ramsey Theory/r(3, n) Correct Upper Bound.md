Date Created: 2024-04-22
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 3]]
Tags: #theorem #ramsey-theory/ramsey-numbers #graph-theory/triangle-free 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: r(3, n) Correct Upper Bound

The [[Ramsey Number|off-diagonal Ramsey number]] $r(3, n)$ satisfies
$$
r(3, n) \leq \frac{n^2}{\log n}.
$$

```

<i>Proof.</i> Suppose there is a two-coloring of $K_N$ without a red triangle or a blue $K_n$. Let $G$ be the graph containing just the red edges. Since it is triangle-free, the neighborhoods of $G$ form independent sets. Since we don't have a blue $K_n$, this means $G$ has independence number at most $n$ and average degree $d$ at most $n$ as well. By [[Triangle-Free Independence Number Lower Bound]], we then have
$$
n\geq \alpha(G) \geq \frac{n\log n - n+1}{(n-1)^2}N \geq \frac{\log n}{n}N,
$$
and the claim follows.