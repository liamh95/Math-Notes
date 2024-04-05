Date Created: 2024-04-05
References: #ref/NONE
Tags: #theorem #graph-theory/matchings #graph-theory/flows

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

### Vertex Cover
```ad-definition
title: Vertex Cover

Let $G = (V,E)$ be a graph. A **vertex cover** of $G$ is a set of vertices that includes at least one endpoint of every edge.
```

In any matching, each edge touches at least one of the vertices in a cover. Thus, the size of a minimum vertex cover is at least as large as a maximum matching in *any* graph $G$. So we have
$$
\text{size of \textit{any} matching} \leq \text{size of maximum matching} \leq \text{size of minimum vertex cover} \leq \text{size of \textit{any} vertex cover}.
$$

```ad-theorem
title: Kőnig's Theorem

Let $G$ be a bipartite graph. Then the size of a maximum matching in $G$ is equal to the size of a minimum vertex cover of $G$.

```

### Flow-based constructive proof
<i>Proof.</i> Label the halves of the bipartition $L$ and $R$. Consider this (modified?) version of [[Ford-Fulkerson Algorithm|Ford-Fulkerson]]. Set up the usual flow network (source $s$ with a unit-capacity edge into each vertex in $L$, sink $t$ with a unit-capacity edge from each vertex in $R$, orient all of $G$'s edges $L\to R$ ) and suppose we have some matching $M$ (maybe just a single edge). We would like to construct an $M$-augmenting path. Any $M$-augmenting path must be of odd length, since it will start and end on opposite halves of the bipartition. With this in mind, direct every edge in $M$ right to left and every other edge in $G$ left to right. Now find a path from an unmatched vertex on the left to an unmatched vertex on the right. This gives an $M$-augmenting path, so toggling it will boost our matching.

Suppose we repeat this until we have a maximum matching and consider the directed bipartite graph we're left with. Let $U$ be the set of unmatched vertices in $L$ and let $X$ be the set of vertices reachable from $L$ by directed paths. Let $C$ be the set of left vertices *not* in $X$ along with the right vertices that are in $X$:
$$
C:= (L\setminus X) \cup (R\cap X).
$$
We claim that this is a minimum vertex cover. To show that it is at least a cover, we need to show that there are no edges between $L\cap X$ and $R\setminus X$.
- If there was an unmatched edge from an unmatched vertex in $L\cap X$ to $R\setminus X$, then that vertex in $R\setminus X$ would be reachable from $U$, contradicting the definition of $X$.
- Similarly, if there was an unmatched edge from a matched vertex in $L\cap X$ to $R\setminus X$, that vertex in $R\setminus X$ would again be reachable from $U$.
- There can't be a matched edge from $R\setminus X$ to $L\cap X$ since everything in $L\cap X$ is reachable from $U$, it must be matched from something in $R\cap X$ already.

Now to show minimality. It suffices to show that the size of this cover is at most the size of a maximum matching, since the size of *any* vertex cover is at least as large as *any* matching. Our graph is bipartite, so all edges have at least one end in $C$.
- Every vertex in $R\setminus X$ must be matched. Otherwise, there would be an augmenting path(?).
- Every vertex in $L\cap X$ is matched, since being in $X$ means being reachable from $U\subseteq X$, so it must be reached by a vertex in $R$. Since there are no edges between $L\cap X$ and $R\setminus X$, this edge must originate from $R\cap X$. This edge is the only one this vertex in $R\cap X$ can correspond to.
So everything in $(R\setminus X) \cup (L\cap X)$ corresponds to a unique edge in the matching (and vertex of $C$).


### Constructive non-flow proof
*Proof.* Let $M$ be a maximum matching. It suffices to construct a vertex cover of size $|M|$. Let $U$ be the set of unmatched vertices in $L$ and let $Z$ be the set of vertices either in $U$ or reachable from $U$ by $M$-alternating paths. Set
$$
K:= (L\setminus Z) \cup (R\cap Z).
$$
If an edge $e$ belongs to an alternating path, it has a right endpoint in $K$. If $e$ is matched but not in an alternating path, then its left endpoint can't be part of an alternating path, and hence, belongs to $L\setminus Z$. Similarly, if $e$ is unmatched and not in an alternating path, then its left endpoint can't be part of an alternating path, otherwise we could extend such a path with $e$. Hence, $K$ is a vertex cover.

Now every vertex in $L\setminus Z$ is matched, since $Z\supseteq U$ and $U$ is the set of unmatched vertices in $L$. Similarly, every vertex in $R\cap Z$ is matched since these vertices are reachable from $U$ by alternating paths. If these were reached by non-matched edges, then these paths would be augmenting, contradicting the maximality of $M$. Thus, every vertex in $K$ touches the matching. But no edge has both ends in $K$. So $|K| = |M|$.