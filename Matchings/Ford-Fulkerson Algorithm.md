Date Created: 2024-03-30
References: #ref/NONE
Tags: #theorem #graph-theory/algorithms #graph-theory/flows

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Say we start with zero flow on a network. Can we improve it to a flow of larger value? Well, if there's a directed path $P$ from the source $s$ to the sink $t$, we can add $\min_{e\in P}c(e)$ to the flow along every edge in $P$ and still get a feasible flow (see [[Flow Constraints]]). Pushing this further, we can improve any flow that has available capacity along some directed path from $s$ to $t$.

Okay, we can certify that a flow is *not* optimal by looking at directed $s\to t$ paths (how we find those is another story), but how can we verify that a flow *is* optimal? Maybe in following the ideas of the above paragraph, we sent some flow down a suboptimal path. Suppose there are some edges that always end up saturated when we attempt to increase the flow (maybe they lie on every $s\to t$ path). Then the sum of these capacities gives an upper bound on the maximum flow value.

```ad-definition
title: Cut

An $s$-$t$ **cut** is a set of edges whose deletion separates $s$ from $t$. Equivalently, a cut is a partition of the vertex set $V = S\cup T$ with $s\in S$ and $t\in T$ (so the cut edges are the crossings).

The **capacity** of a cut $(S,T)$ is the sum of the capacities along the cut edges, i.e.
$$
c(S,T):= \sum_{u\in S}\sum_{v\in T}c(u,v).
$$

Note that this does not include edges from $T$ to $S$.
```

In this terminology, we have
$$
\text{value of \textit{any} flow} \leq \text{value of max flow} \leq \text{capacity of min cut} \leq \text{capacity of \textit{any} cut}.
$$

^6d518d

So if we can find a flow whose value equals the capacity of *any* cut, then it must be a maximum flow.

Cool, so now we know how to tell whether or not a flow is optimal, but how do we build one? If we just greedily enumerate $s\to t$ paths and go path by path in some arbitrary order, adding flow in accordance to the minimum capacity of an edge, it's easy to construct examples where this doesn't lead to a maximum flow. It looks like we need the ability to "undo" the action of sending flow. This is the idea behind the Ford-Fulkerson algorithm.

```ad-definition
title: Residual graph

Given a flow $f$ on a flow network $(G, c, s, t)$, the **residual graph**, $G_f$, has the same vertex set as $G$ and has edge set for which the **residual capacity**, defined by
$$
c_f(u,v) = \begin{cases}
c(u,v) - f(u,v) &\text{if }(u,v)\in E\\
f(v,u) &\text{if }(v,u)\in E
\end{cases},
$$
is positive.
```

The first case is intuitive: it just sets the residual capacity to whatever room is left over after we've sent flow. The second case allows us to send flow back up $(v,u)$, which might not have even been an edge in the original graph.

```ad-algorithm
title: Ford-Fulkerson Algorithm

1. `while` there is an $s\to t$ path of positive residual capacity
	1. choose such a path $P$ arbitrarily and send the maximum possible flow along $P$.
```

Note that this algorithm black boxes the method used to find $s\to t$ paths. This can be done with something like BFS or DFS.

```ad-theorem
title: Ford-Fulkerson Algorithm Runtime

Let $(G, c, s, t)$ be a flow network where the capacity function $c$ is integer-valued. Then there is an algorithm that produces a flow $f$ of maximum value on this network in $O(|E|F)$, where $F$ is the value of a maximum flow (which is equal to the capacity of a minimum cut).

```

<i>Proof.</i> If the maximum flow value is $F$, then we need at most $F$ iterations since each iteration pushes at least one unit of flow. If we use DFS on each step to find an $s\to t$ path, this can be done in $O(|E|+n) = O(|E|)$ iterations. In total, this is $O(|E|F)$ iterations.

Let's prove optimality of the final flow, $f$. In the final residual graph, there must be no $s\to t$ path. Let $S$ be the set of vertices reachable from $s$ in this residual graph and let $T$ be the rest. The partition $S\cup T$ is an $s$-$t$ cut since $t\in T$. Let $c = c(S,T)$ be the capacity of this cut *in the original graph* $G$. Based on the preceding discussion, we know that $|f| \leq c$. From [[Ford-Fulkerson Algorithm#^6d518d]], if we can show that $|f| = c$, then we will have proved the optimality of $f$.

Look at the edges in $G$ that cross $S\to T$. If one of these edges wasn't saturated, then the residual graph $G_f$ would have an edge with positive capacity from $S$ to $T$. But then there would be an $s\to t$ path in $G_f$. Thus, all edges $S\to T$ are saturated.

Now look at the edges that cross $T\to S$. Suppose some such edge has a positive amount of flow along it. Then by the definition of residual capacity, the residual graph would have an edge with positive capacity going in the opposite direction from $S$ to $T$. This would again imply that there is an $s\to t$ path in the residual graph. Thus, all edges $T\to S$ have zero flow along them.

We have then shown that $f(u,v) = c(u,v)$ for any $u\to v$ in $S\to T$. Similarly, we have $f(u,v) = 0$ for any $u\to v$ in $T\to S$. Thus, the net flow across the cut $S\cup T$ is $c(S,T)$ and the flow is optimal.