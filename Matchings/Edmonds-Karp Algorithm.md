Date Created: 2024-03-31
References: #ref/NONE
Tags: #theorem #graph-theory/algorithms #graph-theory/flows

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


The [[Ford-Fulkerson Algorithm]] for bipartite matchings works by constructing a flow network, finding a source-sink path, and then sending flow down it. It leaves the method of actually finding the source-sink path as a black box, however. In the following example, if the path-finding subroutine finds the $s\to a\to b\to t$ path and then the $s\to b \to a \to t$ path and so on, this algorithm will only add one unit of flow at a time, taking $2^{101}$ iterations in total. However, if it found the $s\to a\to t$ and then $s\to b \to t$ paths, then it'll just take 2 iterations.

![[Pasted image 20240331174604.png]]

In this example, it looks like taking a *shortest* $s\to t$ path would have made our lives better. This is what the Edmonds-Karp algorithm does.

```ad-algorithm
title: Edmonds-Karp Algorithm

Edmonds-Karp implements Ford-Fulkerson by selecting a *shortest* $s\to t$ path in the residual graph during each iteration.
```

This can be done by running [[Breadth-First Search]] for example.

```ad-theorem
title: Edmonds-Karp Algorithm Runtime

The Edmonds-Karp algorithm makes at most $|V||E|$ iterations. (This comes out to a running time of $O(|V||E|^2)$ if we include the time for BFS to find a shortest path in each iteration.)

```

<i>Proof.</i> Let $d$ be the distance from $s$ to $t$ in the current residual graph. Suppose we decide to send flow along some shortest $s\to t$ path, $P$. Since this is a shortest path, the $P$-distance of any vertex in $P$ to $s$ is equal to its actual distance to $s$ in the residual graph. When we send flow down $P$, we saturate at least one of its edges, say $(u,v)$. This removes $(u,v)$ from the residual graph, but creates a back-edge $(v,u)$ if it didn't already exist. This can't lower the distance from $s$ to $t$, so $d$ does not decrease.

Each iteration saturates at least one edge, say $(u,v)$, removing it from the residual graph. It will not reappear until we send flow down the resulting back-edge, $(v,u)$, which happens if and only if this back-edge is on some shortest $s\to t$ path in the residual graph. If $d(v,s) = d(u,s)+1$ in the residual graph, then $(v,u)$ is not on a shortest $s\to t$ path. So in order for the back-edge $(v,u)$ to appear on a shortest $s\to t$ path, the distance from $s$ to $t$ has to increase. Since there are $|E|$ edges, the distance from $s$ to $t$ must increase by at least one every $m$ iterations.

Since the distance from $s$ to $t$ can be at most $n$, there must be at most $|E||V|$ iterations.