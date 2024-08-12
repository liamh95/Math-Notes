Date Created: 2024-08-11
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1.4
Tags: #theorem #in-progress #graph-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Separating sets in minimally $k$-connected graphs

```ad-theorem
title: Separating sets in minimally $k$-connected graphs

Let $G$ be a [[k-Connectivity#Minimally $k$-connected|minimally]] $k$-[[k-Connectivity#$k$-Connectivity|connected]] $k$-connected graph, let $e = xy$ be an edge and let $S$ be a separating $(k-1)$-set of $G_e = G-e$. Then $G_e - S$ has exactly two components, one of which contains $x$ and the other $y$.

```

<i>Proof.</i> The graph $G_e-S$ is disconnected (since $S$ is a separating set) but becomes connected if we add $e$ to it (since $G-S$ is still connected and removing $e$ disconnects $G-S$ because $S$ is given to separate $G-e$).

## Local connectivity of minimally $k$-connected graphs

```ad-theorem
title: Local connectivity of minimally $k$-connected graphs

A $k$-[[k-Connectivity#$k$-Connectivity|connected]] graph is [[k-Connectivity#Minimally $k$-connected|minimally]] $k$-connected if and only if the [[k-Connectivity#Local Vertex Connectivity (Bollobás)|local connectivity function]] satisfies $\kappa(x,y) = k$ for every pair of adjacent vertices.
```

*Proof.* If $\kappa(x,y) = k$ for every pair of adjacent vertices in $G$, then $\kappa_H(x,y) = k-1$ where $H = G-xy$. This means that $xy$ is an essential edge. Since this holds for all adjacent pairs, $G$ is minimally $k$-connected.

Suppose then that $G$ is minimally $k$-connected and that $xy\in E(G)$. Then $G_{xy} = G-xy$ can be separated by a $(k-1)$-set $S$. Since $S$ separates $x$ from $y$ in $G_{xy}$ there are at most $k-1$ independent $xy$-paths in $G_{xy}$. Then $\kappa(x,y) \leq k$. Since $\kappa(G) = k$, we must then have $\kappa(x,y) = k$.

## Counterexample: minimally $k$-connected graphs and vertices of degree $k$

If each edge of a $k$-connected graph is incident to at least one vertex of degree $k$, then the graph is minimally $k$-connected. Is this necessary?

Let $3 \leq k < \ell$ and take a tree $T$ where every vertex has either degree 1 or at least $\ell$. Draw $T$ inside of the closed unit disk in a way where the leaves and only the leaves touch the boundary (the unit circle). Let $H$ be the graph obtained by connecting the leaves that are adjacent on the circle. Take $k-2$ copies of $H$ and identify the vertices corresponding the leaves in $T$. In the following diagram, we've chosen $k = 4$ and $\ell = 5$.

![[4-connected.png]]

We claim that $H$ is minimally $k$-connected. Say $xy \in E(H)$. If $x$ and $y$ are on the "rim" of $H$, then there are exactly $k-1$ many $xy$-paths in $H-xy$: one by traversing the outer cycle and taking the unique $T$-path from $x$ to $y$ in the $k-2$ copies of $T$ that have their corresponding $x$'s and $y$'s identified. If $xy$ is an edge in $T$...

