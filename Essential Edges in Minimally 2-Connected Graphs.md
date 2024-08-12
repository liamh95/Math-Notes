Date Created: 2024-08-07
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1.3
Tags: #theorem #graph-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Characterization of essential edges

```ad-theorem
title: Essential Edges in 2-Connected Graphs

Let $xy\in E(G)$ and $H = G - xy$. Then the following are equivalent.
- (i) $G$ is 2-[[k-Connectivity#$k$-Connectivity|connected]] and $xy$ is an [[k-Connectivity#Minimally $k$-connected|essential edge]].
- (ii) $H$ has no isolated vertex, $x$ and $y$ are not [[Cut Vertex and Bridge#Cut Vertex|cut vertices]] of $H$, the [[Block#Block-Cutvertex Graph|block-cutvertex graph]] of $H$, $bc(H)$, has a non-trivial $xy$-path, $x$ belongs to the initial block and $y$ belongs to the terminal block of $H$.

```

<i>Proof.</i>
- (ii) $\implies$ (i): In order for $G$ to be 2-connected, it better be the case that $H$, obtained by deleting a single edge of $G$, have no isolated vertex. Similarly, deleting $x$ or $y$ from $H$ better not increase the number of components of $H$ (and possibly $G$), so they can't be cut vertices of $H$. Finally, if there's an $xy$-path in $bc(H)$, there's an $xy$-path in $H$ as well. This path along with the edge $xy$ give two internally vertex disjoint $xy$-paths in $G$, so $G$ is 2-connected. The essentialness of $xy$ comes from the fact that the $xy$-path in $bc(H)$ is *nontrivial*, so $x$ and $y$ belong to different blocks, so any path between them in $H$ must go through a cut vertex. So there's only one $xy$-path in $H$.

- (i) $\implies$ (ii): $H$ is definitely connected since $G$ is 2-connected and we just snipped one edge to get $H$. We also have that $bc(H)$ is a nontrivial tree since $H$ is connected (so $bc(H)$ is a tree) but not 2-connected (there's a vertex whose deletion disconnects $H$ - this is a cut vertex). Notice that if we take a cut vertex of some graph and join it to any other vertex, it remains a cut vertex. Consequently, $x$ and $y$ are not cut vertices of $H$ (since joining them makes the 2-connected graph $G$).
  
  Now for the path in $bc(H)$. It suffices to show that $bc(H)$ does not have *any* [[Block#End Block|end block]] containing neither $x$ nor $y$. To this end, let $C$ be an end block of $bc(H)$ and let $c$ be its unique cut vertex, which we assume is neither $x$ nor $y$. Then adding the edge $xy$ to $H$ does not join a vertex of $C-c$ to something in $H-C$, so $c$ is still a cut vertex of $G$, contradicting the assumption that $G$ is 2-connected.


## Essential edges are not diagonals in 2-connected graphs

```ad-theorem
title: Essential edges are not diagonals

Let $G$ be a 2-[[k-Connectivity#$k$-Connectivity|connected]] graph. An edge $e = xy$ is an [[k-Connectivity#Minimally $k$-connected|essential]] edge of $G$ if and only if no cycle in $G - e$ contains both $x$ and $y$, i.e. $e$ is not a diagonal of a cycle in $G$.

In particular, a 2-connected graph is minimally connected if and only if no cycle has a diagonal.
```

*Proof.* If no cycle of $G-e$ contains both $x$ and $y$, by the [[Characterization of 2-Connected Graphs#Vertex Connected|characterization of 2-connected graphs]], $G-e$ is not 2-connected, so $e$ is essential. Conversely, suppose $e$ is essential. Then by our [[Essential Edges in Minimally 2-Connected Graphs#Characterization of essential edges|characterization of essential edges]] above, $x$ and $y$ belong to different [[Block#End Block|end blocks]] of the [[Block#Block-Cutvertex Graph|block-cutvertex graph]] of $G-e$. There is then only one $xy$-path in $G-e$, so there is no cycle containing $x$ and $y$ in $G-e$.

## 2-connected subgraphs

```ad-theorem
title: 2-Connected Subgraphs of Minimally 2-Connected Graphs

Every 2-[[k-Connectivity#$k$-Connectivity|connected]] subgraph of a [[k-Connectivity#Minimally $k$-connected|minimally 2-connected]] graph is minimally 2-conected.
```

*Proof.* Say $G$ is minimally 2-connected and let $H$ be a 2-connected subgraph of $G$. Say $e = xy$ is an edge of $H$. By the above result, since $e$ is essential in $G$, it is not the diagonal of any cycle in $G$. Cycles in $H$ *are* cycles in $G$, so $e$ is also not a diagonal of any cycle in $H$, and is therefore essential there as well.


## No triangles made of essential edges

```ad-theorem
title: 2-connected graphs have no triangles made of essential edges

Let $G$ be a 2-[[k-Connectivity#$k$-Connectivity|connected]] graph with at least four vertices. Then $G$ does not contain a triangle formed by essential edges
```

*Proof.* Suppose $G$ did have such a triangle, $xyz$ and let $u \in G - \{x,y,z\}$. By the [[Fan Lemma#Fan Lemma|fan lemma]] there is a 2-[[Fan#Fan|fan]] from $u$ into $\{x,y\}$. If the two paths that comprise this fan, $uP_1x$ and $uP_2y$ both avoid $z$, then the edge $xy$ is a diagonal on the cycle $uP_1xzyP_2u$, contradicting the fact that essential edges are never diagonals.

![[notri1.png]]

On the other hand, say one of the paths on this fan hits $z$, i.e., our fan has the paths (wlog) $uP_1x$ and $uP_2zy$. Then the edge $xz$ is a diagonal on the cycle $uP_1xyzP_2u$. 

![[notri2.png]]

