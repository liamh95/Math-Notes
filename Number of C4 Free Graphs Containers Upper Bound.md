Date Created: 2024-04-15
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Number of $C_4$-Free Graphs Containers Upper Bound

The number of $C_4$-free (not necessarily induced) graphs on $n$ vertices is at most
$$
2^{1.75n^{3/2}}.
$$

```

<i>Proof.</i> Consider a min-degree ordering of the vertices of $G$, $V(G) = \{v_1, \ldots, v_n\}$, that is, $v_i$ is a vertex of minimum degree in $G_i:= G[v_1, \ldots, v_i]$. If we can show that for each $i$, there are $2^{O(\sqrt n)}$ ways to select the neighborhood $N_{G_i}(v_i)$, while keeping $G_i$ $C_4$-free, then we'll be good since there are then $2^{O(\sqrt n)\cdot n} = 2^{O(n^{3/2})}$ many $C_4$-free graphs on $n$ vertices. This is because a graph is uniquely determined by a min-degree ordering and the neighborhoods $N_{G_i}(v_i)$.