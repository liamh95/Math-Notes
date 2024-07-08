Date Created: 2024-07-07
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #definition #graph-theory

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

```ad-definition
title: Graph Minor

A **minor** of a grpah $G$ is any graph obtainable from $G$ by a sequence of vertex and edge deletions and edge contractions.

Alternatively, let $\{V_0, V_1, \ldots, V_k\}$ be a partition of $V(G)$ where each $G[V_i]$ is connected, $1\leq i\leq k$ and let $H$ be obtained by deleting $V_0$ and shrinking each $V_i$, $1\leq i\leq k$ to a point. Then any spannning subgraph $F$ of $H$ is a minor.

```

For example, $K_5$ is a minor of the Petersen graph since we can obtain $K_5$ by contracting the "spokes".

![[graphminor.png]]