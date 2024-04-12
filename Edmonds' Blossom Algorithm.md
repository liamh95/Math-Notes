Date Created: 2024-04-04
References: #ref/NONE
Tags: #theorem #graph-theory/matchings #graph-theory/algorithms  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

By [[Berge's Theorem]], a matching $M$ in a graph $G$ is maximum if and only if $G$ contains no $M$-augmenting path. At a high level, we can build a maximum matching by starting with some (maybe empty) matching and successively augmenting it (if $P$ is an $M$-augmenting path, then $M\triangle P$ is a larger matching). Ostensibly, it comes down to how we find these augmenting paths.

If $G$ contains a [[Blossom]] and the edges inside the cycle incident to the root are also unmatched, then we can toggle the stem and make the root unmatched.

### Lifting blossoms

```ad-proposition

Given a graph $G$ and a matching $M$, let $B$ be a blossom in $G$. Then there is an $M$-augmenting path in $G$ if and only if there is an $M/B$-augmenting path in $G/B$.
```

*Proof.* We can always toggle the stem, so we assume it has length zero, and that the only vertex in the cycle that links two unmatched edges is free. Since all other vertices in the blossom are matched, any other edges out of $B$ are non-matching.

Suppose $P$ is an $M$-augmenting path in $G$. If $P$ does not go through $B$, then it's still an augmenting path of the contraction $G/B$. If $P$ does go through $B$, since the root, $r$, is the only unmatched vertex in $B$, there must be at least one unmatched vertex $v$ in $G$ which is an end of $P$, but is not in $B$. Since $r$ is unmatched in $G/B$, the path from $v$ to $r$ that goes along $P$ is an $M/B$-augmenting path in $G/B$.

Conversely, suppose there is an $M/B$-augmenting path $P'$ in $G/B$ and that we contract $B$ in $G$ to $u$ in $G/B$. If $P'$ does not go through $u$, then $P'$ is unchanged when we un-contract $B$. If $P'$ does go through $u$, then since $u$ is unmatched, it must be an end of $P'$. Say the other end is $s$ and that $e$ is the edge connected to $u$ in $P'$. If we un-contract $B$ and $e$ is connected to the root of $B$ (so the two edges incident to $u$ in $B$ are both unmatched), then the path from the root to $s$ is an $M$-augmenting path in $G$. On the other hand, if $e$ connects to $B$ through a matched vertex, just start the $M$-augmenting path at the root.

### Finding augmenting paths

Similar to [[Dinic's Algorithm]], we construct a sort of layered graph. 

```ad-algorithm
title: Finding Augmenting Paths

1. Put all unmatched vertices in $L_0$ and mark them.
2. Given the even layer $L_{2i}$, construct the next odd layer $L_{2i+1}$ as follows. For each vertex $u\in L_{2i}$ and edge $(u,v)\in E\setminus M$, do the following.
	a. If $v$ is unmarked, then place it in layer $L_{2i+1}$ and mark it.
	b. If $v$ is marked
		i. If $v$ is in $L_{2i}$, then 
```

```ad-theorem
title: Edmonds' Blossom Algorithm



```

<i>Proof.</i> <% tp.file.cursor(2) %>