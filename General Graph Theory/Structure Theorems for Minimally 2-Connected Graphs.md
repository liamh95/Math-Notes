Date Created: 2024-08-07
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1.3
Tags: #theorem #graph-theory

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Compatible Vertices

```ad-definition
title: Compatible Vertices

Let $G$ be a graph. We say that two vertices $x$ and $y$ are **compatible** if every edge joining two vertices on any $xy$-path belongs to that path.

```

In the following figure, vertices $x$ and $y$ are not compatible because $a$ and $c$ lie on a path connecting them, but edge $ac$ does not lie on this path.
![[incompatible.png]]

Note that in the cycle $C_k$, any two non-adjacent vertices are compatible. However, if $G$ has a cycle $C_k$ as a subgraph, non-adjacent vertices might not be compatible if this cycle isn't an *induced* subgraph.

The point of this definition comes from the fact that [[Essential Edges in Minimally 2-Connected Graphs#Essential edges are not diagonals in 2-connected graphs|essential edges in 2-connected graphs are not diagonals of cycles]]. When trying to staple minimally 2-connected graphs together at vertices, we hope that this stapling doesn't create a diagonal of a cycle.
## Decomposition into Smaller 2-Connected Graphs

```ad-theorem
title: Structure Theorem for Minimally 2-Connected Graphs

For each $0 \leq i \leq k$ ($k\geq 1$), let $G_i$ be either just an edge $x_ix'_{i+1}$ or a [[k-Connectivity#Minimally $k$-connected|minimally]] 2-[[k-Connectivity#$k$-Connectivity|connected]] graph containing [[Structure Theorem for Minimally 2-Connected Graphs#Compatible Vertices|compatible]] vertices $x_i$ and $x'_{i+1}$ (and we assume these graphs are on disjoint vertex sets?). Let $G$ be the graph obtained from $\cup_{i=0}^k G_i$ by identifying $x_i$ with $x_i'$ for $1 \leq i \leq k$ and joining $x_0$ to $x'_{k+1}$. Then $G$ is minimally 2-connected.

Conversely, every minimally 2-connected graph can be obtained in the way described above.

```

<i>Proof.</i> For the first part, since [[Essential Edges in Minimally 2-Connected Graphs#Essential edges are not diagonals in 2-connected graphs|essential edges in 2-connected graphs are not diagonals of cycles]], it suffices to show that no cycle in $G$ has a diagonal. If $C$ is a cycle in $G$ that lives only inside one of the $G_i$'s and doesn't touch either of the vertices $x_i$ or $x_{i+1}'$, then there's nothing to check since the $G_i$'s are already minimally 2-connected and this cycle has no diagonal. The only other kind of cycle goes through the compatible vertices, which by compatibility, makes a diagonal-less cycle.

For the second part, let $G$ be a minimally 2-connected graph. Any edge $e = xy$ is essential, so by our [[Essential Edges in Minimally 2-Connected Graphs#Characterization of essential edges|characterization of essential edges]], the graph $H = G-xy$ has blocks $B_0, B_1, \ldots, B_k$ with $k\geq 1$, blocks $B_{i-1}$ and $B_i$ share a single vertex $x_i$, $x$ is in the initial block $B_0$, $y$ is in the terminal block $B_k$, and the vertices $x, x_1, \ldots, x_k, y$ are distinct (i.e., the block graph of $H$ is a path, pictured below, with the edge $xy$ of $G$ in blue. Some of the blocks can just be single edges.). 

![[blockgraph.png]]

Because of the edge $xy$, there is an $x_{i+1}x_i$-path whose only vertices in the block $B_i$ are exactly $x_{i+1}$ and $x_i$ (just go the "other way" along the block graph then take the edge $xy$). Since essential edges (all edges of $G$) are not diagonals of cycles, we conclude that $x_i$ and $x_{i+1}$ are compatible in $G_i$, (otherwise, there'd be a diagonal on a cycle made by taking the offending $x_ix_{i+1}$-path in $G_i$ and then taking that aforementioned reverse path). Finally, the blocks are either edges or, since they're 2-connected subgraphs of a minimally 2-connected graph, [[Essential Edges in Minimally 2-Connected Graphs#2-connected subgraphs|also]] minimally 2-connected.


## Paths Between Compatible Vertices

```ad-theorem
title: Paths Between Compatible Vertices in Minimally 2-Connected Graphs

Let $G$ be a [[k-Connectivity#Minimally $k$-connected|minimally 2-connected]] graph and let $x,y$ be [[Structure Theorems for Minimally 2-Connected Graphs#Compatible Vertices|compatible vertices]] of $G$. Then every $xy$-path contains a vertex of degree 2.
```

*Proof. (unfinished)* Suppose we had an $xy$-path $P = x_0x_1\cdots x_k$ with $x_0 = x$ and $x_k = y$ where no vertex on this path has degree 2. Let $H$ be the graph obtained from $G$ by deleting all edges of $P$ (but keeping the vertices). Since no vertex in $P$ had degree 2 in $G$, the graph $H$ has no isolated vertices.

We claim that each $x_i$ is connected to some other $x_j$ by a path $Q$ that is internally vertex-disjoint from $P$. To see this, recall that by our [[Characterization of 2-Connected Graphs#Vertex Connected|characterization of 2-connected graphs]], any two edges in $G$ are contained in a cycle. Consider, then, the edges $x_ix_{i+1}$ (or $x_ix_{i-1}$) and $x_iy_i$, where $y_i$ is not on $P$ (note that $y_i$ could be the same as $y_j$ for some $i\neq j$). A cycle containing these edges must intersect $P$ at some $x_j \neq x_{i+1}$ (or $\neq x_{i-1}$) -- otherwise $x_ix_{i+1}$ would "shortcut" this path, violating the compatibility of $x$ and $y$.  We take this path $Q$ to be in $H$, e.g. by taking the first vertex along $Q$ that intersects $P$.

![[compat.png]]

Now let $P_1$ be an $x_ix_j$-path in $H$ such that $i<j$ (and so $i \leq j-2$), $V(P_1) \cap V(P) = \{x_i,x_j\}$ and $j-i$ minimal over all possible $j$. Similarly, let $P_2$ be an $x_{i+1}x_\ell$-path in $H$ such that $V(P_2)\cap V(P) = \{x_{i+1}, x_\ell\}$. The paths $P_1$ and $P_2$ are vertex disjoint, since otherwise the edge $x_ix_{i+1}$ would violate the compatibility of $x$ and $y$ (shown below in the case where $\ell < i$ -- the path $xPx_iP_1yP_2x_{i+1}Py$ is "shortcut" by $x_ix_{i+1}$; we get an analogous contradiction when $j < \ell$).

![[disjpaths.png]]

Now if $\ell < i$, then the edge $x_ix_{i+1}$ is a diagonal of the cycle $x_\ell Px_iP_1x_jPx_{i+1}P_2x_\ell$, which contradicts the fact that cycles have no diagonals in minimally 2-connected graphs. We obtain an analogous contradiction if $j< \ell$. 

![[diag_contradiction.png]]

We conclude that $P$ has a vertex of degree 2.
## Cycles in Minimally 2-Connected Graphs

```ad-theorem
title: Cycles in Minimally 2-Connected Graphs

Let $G$ be a [[k-Connectivity#Minimally $k$-connected|minimally 2-connected]] graph which is not a cycle. Then every cycle in $G$ contains two vertices of degree at least three which are separated on the cycle by two vertices of degree two.
```

*Proof.* Let $e = xy$ be an edge in a cycle $C$ of $G$. By our [[Structure Theorems for Minimally 2-Connected Graphs#Decomposition into Smaller 2-Connected Graphs|decomposition result]] above, this cycle has vertices $x_0 = x,\ x_1, \ldots, x_{k+1} = y$ (and possibly others), where the arc of $C$ between $x_i$ and $x_{i+1}$ is either just an edge or a path connecting compatible vertices in a minimally 2-connected graph. Since $G$ is not a cycle, this latter case must happen at least once. In this case $x_i$ and $x_{i+1}$ have degree at least 3 (the ends of this cycle plus the 2-connected subgraph $x_i$ and $x_{i+1}$ live in?), and by our above [[Structure Theorems for Minimally 2-Connected Graphs#Paths Between Compatible Vertices|result]], there is a vertex of degree 2 between them on this cycle.

## Vertices of Degree 2 Separate Minimally 2-Connected Graph

```ad-theorem
title: Vertices of Degree 2 Separate Minimally 2-Connected Graph

Let $G$ be a [[k-Connectivity#Minimally $k$-connected|minimally 2-connected]] graph that is not a cycle. Let $D$ be the set of vertices of degree 2. Then $F = G-D$ is a forest with at least two components. A component $P$ of $G[D]$ is a path and the endvertices of $P$ are not joined to the same tree in $F$.
```

*Proof.* Let  $T_1, \ldots, T_s$ be the components of $F$. [[Structure Theorems for Minimally 2-Connected Graphs#Cycles in Minimally 2-Connected Graphs|Since]] cycles in minimally 2-connected graphs that aren't cycles have at least two vertices of degree 3 that are separated by vertices of degree 2, the vertices of degree greater than 2 cannot form cycles, i.e., the $T_i$'s are trees. By the same reasoning, $G[D]$ has no cycles, so its components are just paths.

Suppose we had a path $P = v_0v_1\cdots v_k$ where $v_0$ and $v_k$ belong to the same tree $T_i$ in $F$. Then all vertices on the (unique) $v_0v_k$-path in $T_i$ would have degree greater than 2, contradicting the [[Structure Theorems for Minimally 2-Connected Graphs#Paths Between Compatible Vertices|fact]] that paths between compatible (why are they compatible?) vertices have at least one vertex of degree 2.

## Number of Vertices of Degree 2 in Minimally 2-Connected Graphs

```ad-theorem
title: Number of vertices of degree 2 in minimally 2-connected graphs

A [[k-Connectivity#Minimally $k$-connected|minimally 2-connected graph]] on $n$ vertices contains at least $\frac{1}{3}(n+4)$ vertices of degree two. For $n \equiv 0, 2\pmod 3$ this is the best possible.
```

*Proof.* Let $G$ be minimally 2-connected with $n$ vertices. Let $D$ be its vertices of degree two and let $F = G-D$. By our [[Structure Theorems for Minimally 2-Connected Graphs#Vertices of Degree 2 Separate Minimally 2-Connected Graph|above]] result, $F$ is a forest with components $T_1, \ldots, T_k$. Let $T_i$ have order $t_i$ in $F$. Since each vertex of $T_i$ has at least three neighbors in $G$ and a tree of order $t_i$ [[Tree#Number of Vertices|has]] $t_i-1$ edges, at least
$$
3t_i - 2(t_i-1) = t_i+2
$$
edges join $T$ to $D$. Now $k\geq 2$, so if we let $f$ be the order of $f$, then there are at least
$$
\sum_{i=1}^k (t_i+2) = f + 2k \geq f+4
$$
edges joining all of $F$ to $D$. We then have
$$
f+4 = n - |D| + 4 \leq 2|D|.
$$
Rearranging gives the claim.

Say $n = 3p-1$ for some integer $p$. Consider the disjoint union of two paths $x_1x_2\cdots x_{p-1}$ and $y_1y_2\cdots y_{p-1}$. Add vertices $z_1, z_1, \ldots, z_p$ and join $z_i$ to $x_i$ and $y_i$ for $1\leq i \leq p-1$. Then join $z_0$ to $x_1$ and $y_1$, and $z_p$ to $x_{p-1}$ and $y_{p-1}$. We can verify that this graph is minimally 2-connected by just counting the number of internally vertex disjoint paths between any pair of vertices and verifying that no cycle has a diagonal.

![[deg2_1.png]]

If $n = 3p$,...


## Number of Edges in Minimally 2-Connected Graphs

```ad-theorem
title: Number of Edges in Minimally 2-Connected Graphs

A minimally 2-connected graph on $n\geq 4$ vertices has at most $2n-4$ edges. Given $n \geq 4$ the complete bipartite graph $K_{2, n-2}$ is the only minimally 2-connected graph on $n$ vertices and $2n-4$ edges.
```

*Proof.* If $G$ is a cycle then the claim is clearly true. Suppose then that $G$ is minimally 2-connected and not a cycle. Let $D$ be the set of vertices of degree 2 in $G$. [[Structure Theorems for Minimally 2-Connected Graphs#Cycles in Minimally 2-Connected Graphs|Then]] $G$ has at least two vertices of degree greater than two. Since [[Structure Theorems for Minimally 2-Connected Graphs#Vertices of Degree 2 Separate Minimally 2-Connected Graph|the vertices of degree two separate]] $G$, the components of $G-D$ are trees $T_1, \ldots, T_k$. Then $2 \leq |D| \leq n-2$ and $2 \leq k \leq |D|$. Then
$$
\begin{align}
m &\leq 2|D| + \sum_{i=1}^k(|T_i| - 1)\\
& = 2|D| + \left(\sum_{i=1}^k|T_i|  \right) - k\\
&= 2|D| + n - |D| - k\\
&\leq |D|+n-2\\
&\leq 2n-4.
\end{align}
$$