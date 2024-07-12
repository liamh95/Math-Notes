Date Created: 2024-07-09
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

## Local Connectivity

```ad-definition
title: Local Connectivity

For vertices $x,y$ in the graph $G$, we define the **local connectivity** between $x$ and $y$ to be the maximum number of pairwise internally vertex-disjoint $xy$-paths. We denote this by $p(x,y)$. Local connectivity is undefined when $x = y$.
```

## $k$-Connectivity

```ad-definition
title: $k$-Connectivity

A graph $G$ is **$k$-connected** if every pair of distinct vertices has at least $k$ pairwise internally vertex-disjoint paths between them.

In other words, $G$ is $k$-connected when $p(x,y) \geq k$ for all $x\neq y$. By convention, an edgeless graph is 0-connected and 1-connected, but not $k$-connected for any $k > 1$.

By [[Menger's Theorem#Menger's Theorem|Menger's theorem]], $G$ is $k$-connected if and only if $G\setminus S$ is connected for any $|S| \leq k-1$.

```

## Connectivity

```ad-definition
title: Connectivity

The **connectivity**, $\kappa(G)$, of $G$ is the maximum value of $k$ for which $G$ is $k$-connected. In other words,
$$
\kappa(G):= \min\{p(x,y):\ x\neq y\}.
$$
```
