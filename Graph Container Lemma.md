Date Created: 2024-03-11
References: #ref/NONE
Tags: #theorem #graph-theory/containers #in-progress 

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

Let $A = V(G)$ be the set of available vertices.

1. If $\Delta(G[A]) < t-1$, output $S(I) = S$ and set $C(S)  = S\cup A$. Otherwise...
2. Let $v\in A$ be the vertex with maximum degree in $G[A]$ (break ties according to some arbitrary ordering on $V(G)$). If $v\notin I$, then set $A = A\setminus \{v\}$ and go back to step 1. If $v\in I$...
3. Set $S = S\cup \{v\}$ and $A = A\setminus \big(\{v\} \cup N_{G[A]}(v)\big)$. Go back to step 1.
```

By design, $I\subseteq S\cup A = C(S)$ and step 1 ensures that $\Delta(G[C(S)]) < t-1$.

Now define $\mathcal C = \{C(S(I)): I\in \mathcal I(G)\}$. It remains to show that this collection is not too large.