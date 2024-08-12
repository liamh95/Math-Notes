Date Created: 2024-08-03
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1; [[Bondy, J and Murty, U - Graph Theory - 2008]] - Chapter 5
Tags: #definition #graph-theory 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Block

```ad-definition
title: Block

A **block** of a grpah $G$ is a maximal [[Separator#Separable Graph|non-separable]] nontrivial subgraph.

```

## Blocks and cut vertices

```ad-proposition
title: Blocks and cut vertices

Any two blocks have at most one vertex in common and that vertex is a [[Cut Vertex and Bridge#Cut Vertex|cut vertex]].
```

*Proof.* Suppose that blocks $B_1$ and $B_2$ have two common vertices. Then $B_1$ and $B_2$ both have at least two vertices, so by maximality, they are loopless. Also by maximality, neither contains the other, so $B:= B_1 \cup B_2$ properly contains both. Take $v \in V(B)$. Then $B-v = (B_1-v) \cup (B_2 - v)$ is connected since $B_1 -v$ and $B_2-v$ are connected (since $B_1$ and $B_2$ are non-separable) and have at least one common vertex by hypothesis. Then $B$ is non-separable as well, contradicting the maximality of $B_1$ and $B_2$.

So let's say that $B_1$ and $B_2$ do intersect and let $v$ be the one vertex they have in common. Then $B_1 - v$ and $B_2 - v$ are connected since $B_1$ and $B_2$ are non-separable. If $B_1-v$ were connected to $B_2-v$ in $G$, then there must be a path $P$ connecting them in $G-v$. But each edge induces a non-separable subgraph, so each edge is contained in a block. But blocks $B_1$ and $B_2$ have exactly one vertex in common, so we conclude that there is no such path $P$, so $v$ is a cutvertex.

## Block Decomposition

```ad-proposition
title: Block Decomposition

Let $I$ be the set of isolated vertices of $G$ and let $B_1, \ldots, B_k$ be the blocks of $G$. Then $I \cup \bigcup_{i=1}^k V(B_i)$ is a decomposition of $V(G)$ and $\bigcup_{i=1}^k E(B_i)$ is a decomposition of $E(G)$.
```

*Proof.* Each edge induces a non-separable subgraph (on one or two vertices), so it must be contained in a maximal non-separable subgraph, i.e. a block. Since any two blocks intersect in at most one vertex, the blocks form a decomposition of $G$.


## Blocks and Cycles

```ad-proposition
title: Blocks and Cycles

Every cycle of a graph $G$ is contained in a block of $G$.
```

*Proof.* A cycle is non-separable subgraph, so it is contained in a maximal non-separable subgraph, i.e. a block.

## Block Graph

```ad-definition
title: Block Graph

Let $G$ be a graph and let $B_1, \ldots, B_k$ be its blocks. The **block graph**, $B(G)$, has vertex set $\{B_1, \ldots, B_k\}$ and $B_iB_j$ is an edge if and only if $B_i$ and $B_j$ have a vertex in common.
```

## Block-Cutvertex Graph

```ad-definition
title: Block-Cutvertex Graph

Let $G$ be a graph, $\mathcal{B}$ its collection of blocks and $S$ its collection of [[Cut Vertex and Bridge#Cut Vertex|cut vertices]]. The **block-cutvertex graph**, $bc(G)$ (or **block tree** according to Bondy and Murty) is the bipartite graph with vertex set $\mathcal B \cup S$, where $Bv$ is an edge for $B\in \mathcal B$ and $v\in S$ if and only if $v\in B$.
```

Note that $bc(G)$ is a forest. If it contained a cycle, then we could pull it back to a cycle in $G$. But cycles are contained in blocks, so this can't happen.

The leaves of $bc(G)$ are all blocks. To see this, suppose a cut vertex $v$ was a leaf of $bc(G)$. Since $v$ is a cut vertex, its deletion increases the number of components of $G$. But since $v$ is a leaf of $bc(G)$, it is contained in just one block, say $B$. But $B$ is non-separable, so $B-v$ is still connected. All edges incident to $v$ must lie in $B$, so removing $v$ didn't disconnect anything outside of $B$ either. Deleting $v$ then doesn't increase the number of components of $G$, so $v$ wasn't a cut vertex at all, a contradiction.

## End Block

```ad-definition
title: End Block

A block of $G$ is an **end block** if it corresponds to a leaf in the [[Block#Block-Cutvertex Graph|block-cutvertex graph]] of $G$.
```