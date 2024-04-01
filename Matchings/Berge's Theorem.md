Date Created: 2024-03-30
References: #ref/NONE
Tags: #theorem #graph-theory/matchings

Proved by: <i>Not Applicable</i>
References: Bondy and Murty
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Berge's Theorem

A matching $M$ in a graph $G$ is a maximum matching if and only if $G$ contains no $M$-augmenting path.
```

<i>Proof.</i> 
Suppose $M$ is a matching in $G$ and say $P$ is an $M$-augmenting path in $G$. Then $M' = M \triangle E(P)$ is also a matching (if $v$ is initial or terminal in $P$, then it will have degree 1 in $M\triangle E(P)$ since $P$ is $M$-augmenting; if it is internal, then exactly one of the two edges from $M\cup P$ incident to it will survive) with $|M| + 1$ edges (the first and last edges of $P$ survive and alternate). Hence, $M$ was not maximum.

On the other hand, suppose $M$ is a non-maximum matching and that $M^*$ is a maximum matching. Consider the induced graph $H:= G[M\triangle M^*]$. Since $M$ and $M^*$ are matchings, each vertex is incident to at most one edge from each, so the maximum degree in $H$ is two. Consequently, each component in $H$ is an isolate, a cycle or a path. The edges in these components alternate membership with $M$ and $M^*$, so the cycles must be even. Since $M^*$ is a larger matching, $H$ must contain more edges from $M^*$, some path component must have more $M^*$ edges. This path component is $M$-augmenting.