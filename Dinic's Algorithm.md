Date Created: 2024-04-01
References: #ref/NONE
Tags: #theorem #graph-theory/flows #graph-theory/algorithms  #in-progress

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


```ad-theorem
title: Dinic's Algorithm



```

<i>Proof.</i> <% tp.file.cursor(2) %>