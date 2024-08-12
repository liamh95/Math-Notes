Date Created: 2024-07-09
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]; [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
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

## Local Vertex Connectivity (Bollobás)

```ad-definition
title: Local Vertex Connectivity

For non-adjacent vertices $x$ and $y$ in the graph $G$, the **local vertex connectivity** between $x$ and $y$, denoted by $\kappa (x,y)$ is the minimum number of vertices whose deletion separates $x$ from $y$. If $x$ and $y$ are adjacent, $\kappa(x,y)$ is defined to be $\kappa_H(x,y)+1$, where $H = G-xy$.

The **vertex connectivity** of $G$ is
$$
\kappa(G) := \min_{x,y\in V(G)}\kappa(x,y).
$$

```
## Local Edge Connectivity (Bollobás)

```ad-definition
title: Local Edge Connectivity

For vertices $x$ and $y$ in the graph $G$, the **local edge connectivity** between $x$ and $y$, denoted by $\lambda (x,y)$ is the minimum number of edges whose deletion separates $x$ from $y$.

The **edge connectivity** of $G$ is
$$
\lambda(G) := \min_{x,y\in V(G)}\lambda(x,y).
$$
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


## Connectivity (Bollobás)

```ad-definition
title: Connectivity (Bollobás)

The **(vertex) connectivity**, $\kappa(G)$ of a graph $G$ is the minimum number of vertices whose removal results in a disconnected graph or in the trivial graph. In terms of [[Separator#$k$-Separator|separators]]
$$
\begin{align*}
\kappa(G) &:= \min\{|G|-1,\ k: G\text{ has a $k$-separator} \}\\
&= \min\{|G|-1,\ |S|: S\text{ separates }G  \}.
\end{align*}
$$

**Edge connectivity**, $\lambda(G)$, is defined analogously by removing edges to disconnect $G$.

A graph is **$k$-connected** if $\kappa(G) \geq k$ and **$k$-edge-connected** if $\lambda(G) \geq k$.
```

Under this definition, 1-connectivity and 1-edge-connectivity coincide.

For any $v\in V(G)$ and $e\in E(G)$, deleting one of these reduces the connectivity (or edge connectivity) by at most one:
$$
\kappa(G) - 1 \leq \kappa(G-v) \leq \kappa(G),\quad \lambda(G)-1 \leq \lambda(G-e)\leq \lambda(G).
$$
Since deleting a non-isolated vertex deletes at least one edge and cutting all edges incident to a vertex of minimum degree disconnects a graph, we have
$$
\kappa(G) \leq \lambda(G) \leq \delta(G).
$$
## Minimally $k$-connected

```ad-definition
title: Minimally $k$-connected

We say that an edge $e$ of a graph is **essential** if $\kappa(G\setminus e) < \kappa(G)$. A $k$-connected graph, all of whose edges are essential, is **minimally $k$-connected**.

In particular, a graph is minimally $k$-connected if and only if it does not contain a $k$-connected graph as a proper [[Factor#Factor|factor]].
```


## $k$-Component

```ad-definition
title: $k$-Component

A **$k$-component** of a graph $G$ is a maximal [[k-Connectivity#$k$-Connectivity|$k$-connected]] subgraph of $G$.
```