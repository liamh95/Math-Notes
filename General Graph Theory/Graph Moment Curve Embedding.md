Date Created: 2024-07-07
References: #ref/NONE
Tags: #theorem #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Graph Moment Curve Embedding

Every graph $G$ admits an embedding into $\mathbb{R}^3$ in such a way that all edges are represented by line segments that do not intersect, except possibly at vertices.

```

<i>Proof.</i> Say the vertices of $G$ are $\{v_1, v_2, \ldots\}$ (possibly countably infinitely many). Map vertex $v_j$ to the point $(j, j^2, j^3)$ in $\mathbb{R}^3$. If $\{v_j, v_k\}$ is an edge then represent it by the line segment connecting $(j, j^2, j^3)$ to $(k, k^2, k^3)$. Say we have edges $\{v_a, v_b\}$ and $\{v_c, v_d\}$. There's no issue if these edges have a vertex in common, so we'll assume they're disjoint. The line segments in questions cross if and only if the corresponding endpoints are coplanar. Let's show that they aren't.

The volume of the box spanned by these points has volume given by
$$
\begin{vmatrix}
1 & a & a^2 & a^3\\
1 & b & b^2 & b^3\\
1 & c & c^2 & c^3\\
1 & d & d^2 & d^3\\
\end{vmatrix}.
$$
This is a [[Vandermonde Matrix|Vandermonde matrix]] with distinct rows, so it has nonzero determinant. Since these four points determine a box with positive volume, they are not coplanar. Consequently, the edges in question do not intersect.