Date Created: 2024-03-11
References: #ref/NONE
Tags: #theorem #graph-theory/containers

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Graph Container Lemma

Let $G$ be a graph on $n$ vertices and let $t$ be a positive real number. Then there is a collection $\mathcal C$ of subsets of $V(G)$ (containers) such that:
1. for every independent set $I$, there is some $C\in \mathcal C$ such that $I\subseteq C$;
2. $\Delta(G[C]) < t$ for all $C\in \mathcal C$;
3. $|\mathcal C| \leq \binom{n}{\leq n/(t+1)}$.

```

<i>Proof.</i> Our proof is algorithmic. The idea is to somehow "encode" the independent sets. Given an independent set $I$, our goal is to output some set $S = S(I)$ (think of as the "fingerprint" of $I$). We'll try to do this in a way so that $S$ corresponds to some container $C$ satisfying the conclusions of the theorem.

Here's one idea. We could try letting $S$ be just a single vertex from $I$. In a way, the vertex that "stands out" the most is the vertex in $I$ of maximum degree. So let's let $S := \{v\}$, where $d(v) = \max_{u\in I}d(u)$. Then we can let $C := V(G)\setminus N(v)$. Then $I\subseteq C$ and if $d(v)$ is large, then $C$ is small. Since $v$ is the vertex in $I$ of maximum degree, we can throw away even more vertices and let
$$
C:= V(G)\setminus \big(N(v) \cup \{u\in V(G): d(u) > d(v)\}\big).
$$
This way, even if $d(v)$ isn't that big, we can throw away a lot of vertices to make $C$ smaller. Let's try to iterate this.

```ad-algorithm
Input: $I$ an independent set of the graph $G$ and a positive real number $t$.

1. Fix some ordering of the vertex set $V(G) = \{v_1, \ldots, v_n\}$ and set $G_0 ;= G$. Initialize the set $S = S(I) := \emptyset$ (the "signature" of $I$).
2. While $\Delta(G_i) \geq t$:
	1. Let $u$ be a vertex of maximum degree in $G_i$. If there are ties, take the one that comes first in the fixed ordering of $V(G)$.
	2. If $u \in I$, then set $S := S\cup \{u\}$ and $G_{i+1} := G_i\setminus N_{G_i}[u]$.
	3. If $u\notin I$, then let $G_{i+1} := G_i\setminus \{u\}$.
3. Output $S(I)$ and set $C(S) = S\cup G_{i+1}$.
```

By design, $I\subseteq S\cup V(G_{i+1})$ and $\Delta(G[C(S)]) < t$.

Now define $\mathcal C = \{C(S(I)): I\in \mathcal I(G)\}$. It remains to show that this collection is not too large. If the algorithm hasn't terminated yet, then $\Delta(G_{i+1}) \geq t$. Every time we add a vertex to $S$, we remove a vertex and its at least $t$ neighbors from $G_i$. So we remove at least $t+1$ vertices at a time from $G$, and there are at most $n/(t+1)$ steps. Thus, $|S| \leq n/(t+1)$. In total, we have at most $\binom{n}{\leq n/(t+1)}$ choices for $S$.