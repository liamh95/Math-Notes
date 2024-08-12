Date Created: 2024-08-07
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
Tags: #theorem #graph-theory

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Characterization of $k$-connected graphs

```ad-theorem
title: Halin and Lick's Characterization of k-connected graphs

- (a) A graph $G$ with at least $k \geq 2$ vertices is $k$-[[k-Connectivity#$k$-Connectivity|vertex connected]] if and only if for each $(k-2)$-set $U$ of vertices and for each pair $x,y$ of vertices of $G-U$, there is a cycle in $G-U$ containing the vertices $x$ and $y$.
- (b) A graph $G$ with at least $k \geq 2$ edges is $k$-edge connected if and only if for each $(k-2)$-set $F$ of vertices and for each pair $e,f$ of edges of $G-F$, there is a circuit in $G-F$ containing the edges $e$ and $f$.

```

<i>Proof.</i> 
- (a): Say $G$ is $k$-connected and let $U$ be a set of $k-2$ vertices of $G$ and let $x,y \in V(G-U)$. Since deleting a vertex drops the connectivity by at most one, $G-U$ has vertex connectivity at least 2. By the [[Characterization of 2-Connected Graphs#Vertex Connected|characterization of 2-connected graphs]], any two vertices of $G-U$ have a cycle through them.
  
  Conversely, suppose that deleting any $(k-2)$-set $U$ leaves a graph where any two vertices have a cycle through them. By the characterization of 2-connected graphs, $G-U$ is at least 2-connected for any $(k-2)$-set $U$. Now let $x$ and $y$ be any two distinct vertices in $G$ and let $W$ be a $(k-1)$-set containing neither $x$ nor $y$. Enumerate $W = \{w_1, \ldots, w_{k-1}\}$. For each $i\leq k$, the graph $(G-W) \cup w_i$ is 2-connected, so $G-W$ is connected. Since throwing out a $(k-1)$-set results in a connected graph, the connectivity of $G$ is at least $k$.

- (b): This follows by applying the above reasoning to the [[Line Graph#Line Graph|line graph]] of $G$.