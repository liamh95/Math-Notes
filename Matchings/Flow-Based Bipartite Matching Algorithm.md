Date Created: 2024-03-31
References: #ref/NONE
Tags: #theorem #graph-theory/matchings #graph-theory/algorithms

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Flow-Based Bipartite Matching Algorithm

Suppose $G = (L\cup R, E)$ is a bipartite graph. Then there is an algorithm that finds a maximum cardinality matching in $G$ in $O(|V||E|)$ steps.

```

<i>Proof.</i> Construct the following flow network $(G, c, s, t)$ from $G$. Create a source node $s$ and send an out-edge from $s$ to every vertex in $L$. Create a sink node $t$ and send an out-edge from every vertex in $R$ to $t$. Orient all edges from $L$ to $R$ and give all edges capacity 1. Use the [[Ford-Fulkerson Algorithm]] to find a maximum flow in this network. Since the initial capacities were all 1, the resulting flow will be either 0 or 1 along all edges. We claim that the edges with flow 1 along them form a maximum cardinality matching.

First consider any matching in $G$. Send one unit of flow along each matched edge in $(G, c, s, t)$ and one unit of flow from $s$ into every matched edge and out such edges into $t$. This flow clearly satisfies the capacity constraints, and it satisfies the conservation constraint because each (non $s$ or $t$) vertex is matched to at most one edge.

Conversely, consider any feasible (integral?) flow on $(G, c, s, t)$ and take all of the edges with unit flow along them. Since the flow is integral, each hit vertex in $L$ has unit flow coming out, so it has at most one edge into it with flow along it. Thus, we have a matching.

In both cases, the value of the flow equals the cardinality of the matching, so a maximum flow corresponds to a maximum matching. Since Ford-Fulkerson always finds a maximum flow, it therefore finds a maximum matching.

Let's look at the runtime. If the maximum flow value is $F$, then Ford-Fulkerson runs in time $O(|E|F)$. Since a maximum matching has at most $\min\{|L|, |R|\}$ edges in it, and the size of a maximum matching equals the value of a maximum flow, the runtime is $O(|E|\cdot \min\{|L|, |R|\})$.