Date Created: 2024-04-05
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Tutte-Berge Formula

Let $G=(V,E)$ be a graph. Then the size of a maximum matching in $G$ is given by
$$
\min_{U\subseteq V}\frac 12 \left(|V| + |U| - \text{odd}(G-U)   \right),
$$
where $\text{odd}(H)$ is the number of connected components of $H$ with an odd number of vertices.

```

<i>Proof.</i> The idea is that in any maximal matching, in order to completely cover an odd component of $G-U$ with the matching, one of the matched edges has to touch $U$.