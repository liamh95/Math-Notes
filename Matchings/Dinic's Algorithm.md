Date Created: 2024-04-01
References: #ref/NONE
Tags: #theorem #graph-theory/flows #graph-theory/algorithms

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Even when we use shortest paths each time, there still appears to be some waste in the [[Edmonds-Karp Algorithm]]. When we use [[Breadth-First Search]] to find an augmenting $s\to t$ path in the residual graph, it really gives us more than just this one path. The BFS really returns an $s$-rooted tree, encoding all of the shortest paths from $s$. So maybe we can run BFS once and use it to exhaust several shortest augmenting paths.

### Blocking Flow

```ad-definition
title: Blocking Flow

A flow $f$ on the network $(G, c, s, t)$ is a **blocking flow** if every shortest $s\to t$ path in $G$ has some arc saturated.
```

Suppose the distance from $s$ to $t$ in the residual graph is $d$. To construct a blocking flow, we need a collection of augmenting paths such that, after augmenting all of them, there are no more augmenting paths of length $d$. In other words, a blocking flow increases $d$. Consequently, there can be at most $n$ blocking flows, so if we can quickly find these, we get a better algorithm.

Running BFS gives us these pretty much instantly. After running it, lay out all the vertices at distance 1 from $s$ in one layer. In the next layer, lay out all vertices of distance 2 from $s$ and include only the edges from the first layer into the second. In this fashion, layer all of the vertices in $G$ and only include edges from one layer to the one immediately following it. The original graph $G$ might have edges that go backwards with respect to these layers, but they can't be part of a shortest $s\to t$ path, so we don't care about them.

### Layered Graph

```ad-definition
title: Layered Graph

The **layered graph** $L$ corresponding to a flow network $(G, c, s, t)$ has $V(L) = V(G)$ and has edge set defined by
$$
(u,v) \in E(L) \iff (u,v)\in E(G)\text{ and }d_G(s, v) = d_G(s,u)+1.
$$
```

We can construct the layered graph while running a BFS, which takes $O(m+n)$ time (at no additional space cost too -- just ignore edges that don't from one layer to the next). Now we can just work with the layered graph instead of the original graph $G$.

Cool, but how do we build a blocking flow? We can run a [[Depth-First Search]] on the layered graph from now on and only take unsaturated edges. An augmenting path has at most $n-1$ edges in it, but a naive DFS takes $O(n+m)$ time since it traverses some edges that won't even end up in the augmenting path (dead ends).

The key idea is that once we identify an edge as leading to a dead end after the first run of DFS, we can mark it as dead and never traverse it on future runs of DFS (if it isn't on a shortest path now, it never will be).

```ad-proposition
title: Blocking Flow Algorithm

We can find a blocking flow in $(G, c, s, t)$ in $O(mn)$ time.
```

*Proof.* First build the layer graph $L$ using a BFS in $O(m+n)$ time. Now we run modified breadth-first searches, as described above, to find augmenting paths (mark dead ends to never DFS them again). Since each augmenting path has length at most $n$, the time for each modified DFS is at most
$$
n + \text{number of new edges marked ``dead''}.
$$
Since there are at most $m$ augmenting paths, the total time is
$$
\begin{align*}
	&\sum_{i=0}^m(n + \text{number of new edges marked as ``dead'' in iteration }i)\\
	&= mn + \sum_{i=0}^m(\text{number of new edges marked ``dead'' in iteration }i)\\
	&= mn + \text{total number of dead edges}\\
	&= O(mn).
\end{align*}
$$
Putting it all together, we get Dinic's algorithm.

### Dinic's Algorithm

```ad-algorithm
title: Dinic's Algorithm

**Input: **A flow network $(G, c, s, t)$.
**Output: **An $s\to t$ flow $f$ of maximum value.

1. Set $f(e) = 0$ for every $e\in E(G)$.
2. `while` $d_L(s,t) <\infty$ where $L$ is the layered graph constructed from $G_f$
	1. Find a blocking flow $f'$ in $L$.
	2. Augment $f$ by $f'$.
3. `return` the flow $f$.
```


```ad-theorem
title: Dinic's Algorithm Runtime

Dinic's algorithm runs in time $O(n^2m)$. 

```

<i>Proof.</i> Augmenting along a blocking flow increases the distance from $s$ to $t$ in the residual graph. The distance from $s$ to $t$ is at most $n$, so the runtime is at most $n$ times the amount of time it takes to find a blocking flow. We showed earlier that we can find a blocking flow in $O(mn)$ time and the claim follows.