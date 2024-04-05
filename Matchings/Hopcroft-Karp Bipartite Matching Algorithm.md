Date Created: 2024-03-31
References: #ref/NONE
Tags: #theorem #graph-theory/matchings #graph-theory/algorithms #graph-theory/flows

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

The idea is to basically just use the idea for [[Flow-Based Bipartite Matching Algorithm]] implemented with [[Dinic's Algorithm for Unit-Capacity Graphs]].

```ad-algorithm
title: Hopcroft-Karp Bipartite Matching Algorithm

**Input: **A bipartite graph $G = (L\cup R,E)$.
**Output: **A maximum cardinality matching in $G$.

1. Orient all edges $L\to R$ in $G$. Add the vertex $s$ and an edge $(s,v)$ for all $v\in L$. Add the vertex $t$ and an edge $(v,t)$ for all $v\in R$. Set the capacity $c(e) = 1$ for all of these edges.
2. Use [[Dinic's Algorithm for Unit-Capacity Graphs]] to compute the maximum flow, $f$, on this network.
3. `return` the set of $L\to R$ edges for which $f(e) = 1$.
```

```ad-theorem
title: Hopcroft-Karp Bipartite Matching Algorithm Runtime

The Hopcroft-Karp algorithm finds a maximum cardinality matching in the bipartite graph $G$ in time $O(|E|\sqrt{|V|})$.

```

<i>Proof.</i> By [[Dinic's Algorithm for Unit-Capacity Graphs#Blocking flows in unit-capacity graphs|this discussion]] on Dinic's algorithm for unit-capacity graphs, it takes $O(|E|)$ time to construct any of the blocking flows. Now after $d$ iterations, any $s\to t$ path in the residual graph is at least $d$ edges long. Since we're working in a unit-capacity graph, we can only augment along an edge once, so the augmenting paths have to be edge disjoint. Furthermore, each vertex has either exactly one in-edge with capacity 1 (the vertices in $L$), or exactly one out-edge of capacity 1 (the vertices in $R$), so the paths we augment along have to be *vertex-disjoint* too. Consequently, there can be at most $|V|/d$ such paths. After $d$ iterations, the max flow is at most $d + |V|/d$, which maximized when $d = \sqrt{|V|}$, since the size of the max flow is at most $|V|$.

Thus, there are at most $O(\sqrt{|V|})$ iterations, each taking at most $O(|E|)$ time.