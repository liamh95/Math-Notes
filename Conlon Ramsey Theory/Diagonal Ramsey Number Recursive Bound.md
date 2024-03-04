Date Created: 2024-03-04
References: #ref/NONE
Tags: #corollary #ramsey-theory/ramsey-numbers 

Proved by: <i>Not Applicable</i>
References: Conlon Ramsey theory notes: Lecture 1
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-corollary
title: Diagonal Ramsey Number Recursive Bound

$$
r(t) \leq 4r(t, t-2) + 2.
$$
```

<i>Proof.</i> Suppose we have 2-colored the edges of $K_n$ in such a way that we have no monochromatic $K_t$. If $ab$ is a red edge, then the common neighborhood of $a$ and $b$ has at most $r(t-2, t)-1$ vertices $v$ connected to both $a$ and $b$ by red edges. Otherwise, we'd have a blue $K_t$ or a red $K_{t-2}$, which, when taken together with $ab$, gives a red $K_t$. Similarly, each blue edge has at most $r(t, t-2)-1$ vertices connected by blue edges to both ends. Therefore, the number of monochromatic triangles is at most $\frac{1}{3}\binom{n}{2}(r(t-2, t)-1)$. Comparing this to [[Monochromatic Triangles in Two Coloring of K_n]], we obtain $n\leq 4r(t,t-2)+1$.