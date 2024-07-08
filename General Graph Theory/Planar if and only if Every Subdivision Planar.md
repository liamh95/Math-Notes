Date Created: 2024-07-07
References: #ref/NONE
Tags: #proposition #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-proposition
title: Planar if and only if Every Subdivision Planar

Let $G$ be a graph. Then $G$ is planar if and only if every [[Subdivision|subdivision]] of $G$ is planar.

```

<i>Proof.</i> Fix a planar embedding of $G$. Leaving this embedding alone and subdividing edges gives a planar embedding of the subdivision.

Conversely, suppose every subdivision of $G$ is planar and take some subdivision $H$ of $G$. Take a planar embedding of $H$. In this embedding of $H$, none of its edges cross. If we un-subdivide any of the edge subdivisions, we get a planar embedding of $G$.