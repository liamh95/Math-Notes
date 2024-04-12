Date Created: 2024-04-09
References: #ref/NONE
Tags: #theorem #probabilistic-method/alterations #graph-theory/independence-number 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Independence Number Average Degree Lower Bound

Let $G$ be a graph with average degree $d$. Then
$$
\alpha(G) \geq \frac{n}{2d}.
$$

```

<i>Proof.</i> Include each $v\in V(G)$ in $S$ with probability $p$, each choice made independently. Let $X = |S|$ and let $Y$ be the number of edges in the induced subgraph $G[S]$. Each edge appears in $G[S]$ with probability $p^2$, so by the linearity of expectation,
$$
E[Y] = \frac{nd}{2}p^2.
$$
Now $E[X-Y] = np - \frac{nd}{2}p^2$. Choosing $p = 1/d$ maximizes this expression, giving
$$
E[X-Y] = \frac{n}{2d}.
$$
[[First Moment Method|Thus]], there is a set $S$ such that the number of vertices in $S$ minus the number of edges in $S$ is at least $n/2d$. Now just take one vertex from each edge in $S$ and delete it. This leaves us with an independent set with at least $n/2d$ vertices in it.