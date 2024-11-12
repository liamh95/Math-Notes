Date Created: 2024-09-20
References: #ref/NONE
Tags: #definition #graph-theory/coloring #graph-theory/algorithms  #in-progress 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Edge coloring

```ad-definition
title: Edge coloring

Let $G = (V,E)$ be a graph. An **edge coloring** (or just **coloring** usually if it's clear from context that we're coloring edges) is a map $c: E\to [k]$ for some positive integer $k$. When $k$ is specified, we call $c$ a **$k$-edge-coloring**. The coloring $c$ is **proper** if $c$ assigns incident edges different colors. If $G$ admits a proper $k$-edge-coloring, we call $G$ **$k$-edge-colorable**.

```

## Chromatic index

### Definition

```ad-definition
title: Chromatic index

Let $G = (V,E)$ be a graph. The smallest positive integer $k$ such that $G$ admits a proper $k$-edge-coloring is the **chromatic index** of $G$ and is denoted by $\chi'(G)$.
```

### Lower bounds

If $G$ has maximum degree $\Delta$, then $\chi'(G) \geq \Delta$ since each edge incident to a vertex of maximum degree must be assigned a different color.

### Upper bounds

The celebrated theorem of Vizing says that $\chi'(G) \leq \Delta+1$:

```ad-theorem
title: [[Vizing's Theorem#Vizing's Theorem|Vizing's theorem]]

Let $G$ be a graph with maximum degree $\Delta$. Then
$$
\Delta \leq \chi'(G) \leq \Delta+1.
$$
```

## Algorithms

Sinnamon outlines a general framework for several different edge-coloring algorithms. They break it down into a few high-level procedures. Say we're trying to edge color $G$, which has $n$ vertices, $m$ edges and maximum degree $\Delta$ with at most $N$ colors

1. **Partition.** Partition $G$ into two edge-disjoint subgraphs such that each subgraph has half of the edges ($\leq \lceil m/2\rceil$) and the maximum degree of each subgraph is at most half that of the original graph ($\leq \lceil \Delta /2 \rceil$). This can be done in $O(m)$ time by just removing maximal tours from $G$ until no edges remain. Then, for each tour, traverse it and alternately assign the edges to the two subgraphs.
2. **Recurse.** Color the two subgraphs from the partitioning step with at most $\lceil N/2\rceil$ colors each and with disjoint color palettes. Then take the union of the two colorings.
3. **Prune.** After recursing and putting the colorings together, we obtain a coloring that uses up to $2\lceil N/2\rceil$ colors, which could be more than $N$ (e.g. if we're trying to use $\Delta+1$ colors, then this could be up to $\Delta+3$). Let $t$ be the number of excess colors used (the number used minus $N$). Choose the $t$ least used colors and uncolor all edges that use these colors. The number of uncolored edges is at most $m\frac{t}{N+t}$.
4. **Repair.** Now we have to fix the uncolored edges.

### Greedy algorithm

Using the framework above, we specify the repair step of a greedy algorithm (the other steps are basically already specified above). It will use $2\Delta - 1$ colors and take $O(m\log \Delta)$ time in the RAM model.

The idea is to prescribe how to color a single uncolored edge. If the edge $uv$ is uncolored, we look at the colors used at $u$ and at $v$. These vertices have at most $\Delta-1$ neighbors already colored, for a total of at most $2\Delta - 2$ colors used at both. By the pigeonhole principle, there is at least one color available to assign to $uv$. This results in a valid partial coloring and takes $O(\Delta)$ time.

```ad-algorithm
title: Greedy Edge Color

**Input:** A graph $G$, a valid partial coloring $c: V \to [2\Delta-1]$ and an uncolored edge $uv$
**Output:** Assigns a color from $[2\Delta - 1]$ to $uv$ that results in a legal partial coloring

1. `for each` color $\alpha \in [2\Delta-1]$:
	1. `if` $\alpha$ is missing at $u$ and at $v$:
		1. $c(uv) \gets \alpha$
		2. `return`
```

The whole repair step just consists of applying Greedy Edge Color to each uncolored edge and repairing takes $O(m)$ time and $\Delta$ is reduced by roughly 2 on each recursive call, resulting in a recursion tree depth of $O(\log \Delta)$ where the work done at each level is $O(m)$.

While this algorithm is greedy in the sense that it operates on the edges of $G$ sequentially, it is a bit more complicated than the [[Vertex Coloring#Algorithms#Greedy algorithm|greedy algorithm for vertex coloring]] because sometimes we have to recolor and possibly un-color edges.

### Sinnamon's Algorithm

Sinnamon gives an algorithm that produces a $(\Delta+1)$-edge-coloring in $O(m\sqrt n)$ time