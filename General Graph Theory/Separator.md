Date Created: 2024-08-03
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
Tags: #definition #graph-theory 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## $k$-Separator

```ad-definition
title: Separator

Let $G$ be a graph and let $V_1$ and $V_2$ be subsets of $V(G)$. If $V(G) = V_1 \cup V_2$, $S = V_1\cap V_2$ is a proper subset of both $V_1$ and $V_2$, $|S| = k$ and no vertex in $V_1 \setminus S$ is adjacent to a vertex in $V_2\setminus S$, then we say that $(V_1, V_2)$ is a **$k$-separator** with **separating set $S$**. We also say that the vertices of $S$ **separate** $G$.

If $X\subseteq V_1 \setminus S$ and $Y\subseteq V_2\setminus S$, then we say $S$ separates $X$ from $Y$. 

```

Note that for a connected graph $G$, $S\subseteq V(G)$ is a separator if and only if $G\setminus S$ is disconnected.

## Separable Graph

```ad-definition
title: Separable Graph

We say that a grpah is **separable** if it has a 1-separator, i.e., if there is a vertex whose deletion disconnects the graph.
```