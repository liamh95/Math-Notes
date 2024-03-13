Date Created: 2024-03-12
References: #ref/NONE
Tags: #theorem #graph-theory/containers #graph-theory/coloring #graph-theory/regular-graphs  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

How many ways can we properly $q$-color $K_{d,d}$? We can just sum over the number of ways to choose colors for the parts to get the estimate
$$
\sum_{i=1}^{q-1}\binom qi i^d(q-i)^d.
$$
If we take $n/{2d}$ copies of $K_{d,d}$, then we get about $(q/2)^{n}$ colorings when $q$ is even and $(\frac{q+1}{2})^{n/2}(\frac{q-1}{2})^{n/2}$ when $q$ is odd. We can use containers to show that, asymptotically, this is the best we can do for any $d$-regular graph.

```ad-theorem
title: q-Colorings of d-Regular Graphs

Assume that $n$ is a multiple of $2d$. Among $n$-vertex, $d$-regular graphs, the vertex-disjoint collection of $K_{d,d}$'s maximizes the number of proper $q$-colorings (asymptotically).

```

<i>Proof.</i> The color classes $C_1, \ldots, C_q$ are independent sets. When we apply the [[Graph Container Lemma]], we get that each color class is contained in some $S\cup G_S$. Using the same supersaturation argument from [[d-Regular Graph Independent Sets]], we can take $t = \sqrt{d\log d}$ and guarantee that each $|C_j\cup G_j| \leq n(\frac{1}{2} + o(1))$.

The number of ways to choose $q$ fingerprints is at most
$$
\binom{n}{\leq n/\sqrt{d\log d}}^q \leq 2^{3nq\sqrt{\log d/d}}
$$