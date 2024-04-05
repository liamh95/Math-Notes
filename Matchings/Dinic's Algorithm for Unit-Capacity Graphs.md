Date Created: 2024-04-03
References: #ref/NONE
Tags: #theorem #graph-theory/flows #graph-theory/algorithms 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

There are some classes of networks where it's easier to find a [[Dinic's Algorithm#Blocking Flow|blocking flow]] than the $O(mn)$ time suggested by our analysis of [[Dinic's Algorithm#Dinic's Algorithm|Dinic's algorithm]]. That analysis was based on the idea that there are at most $m$ augmenting paths, each of length at most $n-1$, giving $O(mn)$ plus the $O(m)$ cost of marking dead ends. We can do better when all (positive) capacities are one.

### Blocking flows in unit-capacity graphs

```ad-proposition
title: Blocking Flows in Unit-Capacity Graphs

If every positive capacity in $(G, c, s, t)$ is one, then a blocking flow can be found in $O(m)$ time.
```

*Proof.* Since we saturate edges at each step and our capacities are 1, all residual graphs will also be of unit capacity.  Unit capacity tells us that no edge can be used in multiple augmenting paths (it can belong to more than one, but we can only augment along one of these paths). When we build our blocking flow, the *total* length of the augmenting paths we use is at most $m$ then. When we add the cost of marking dead ends, we find our augmenting paths and build our blocking flow in $O(m)$ time.

### Number of blocking flows in unit-capacity graphs

So we can find a blocking flow in $O(m)$ time now. Since augmenting along such a flow increases the distance from $s$ to $t$, it looks like we can find the max flow in $O(mn)$ time: an improvement. It turns out we can still do better.

```ad-proposition
title: Number of Blocking Flows in Unit-Capacity Graphs

If every positive capacity in $(G, c, s, t)$ is one, then we need at most $2\sqrt m$ blocking flows to find the max flow.
```

*Proof.* Each time we build a blocking flow, we increase the $s\to t$ distance in the residual graph by at least one, so after $k$ blocking flows, the $s\to t$ distance is at least $k$. Let's consider the max flow in this residual graph. Each augmenting path has length at least $k$, and there are at most $m$ edges in the graph. Since our edges have unit capacity, the augmenting paths we take to build a blocking flow need to be edge-disjoint, so we can take at most $m/k$ augmenting paths. Each augmenting path has capacity 1, so the max flow here is $m/k$.

Each blocking flow adds at least one unit of flow, so we need to find at most $m/k$ more blocking flows. We've done $k$ already, so the total number of blocking flows we need is at most $k + \frac mk$. This is minimized when $k = \sqrt m$, so we need at most $2\sqrt m$ blocking flows.

### Dinic's algorithm for unit-capacity graphs

```ad-theorem
title: Dinic's Algorithm for Unit-Capacity Graphs

Dinic's algorithm can find the max flow on the unit-capacity network $(G, c, s, t)$ in time $O(m^{3/2})$.

```

<i>Proof.</i> Each blocking flow can be found in time $O(m)$ and we only need $O(\sqrt m)$ many blocking flows.