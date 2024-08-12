Date Created: 2024-08-11
References: #ref/NONE
Tags: #theorem #definition #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Tree

```ad-definition
title: Tree

A **tree** is a connected graph containing no cycles.
```

## Leaf

```ad-definition
title: Leaf

If $T$ is a tree, then a vertex of degree one in $T$ is called a **leaf**.
```

## Trees Have Leaves

```ad-theorem
title: Trees have leaves

Let $T$ be a tree. 
```

## Number of Vertices

```ad-theorem
title: Number of Vertices in a Tree

A connected graph $G$ on $n$ vertices is a tree if and only if it has $n-1$ edges.

```

<i>Proof.</i> Suppose $G$ is a tree on $n$ vertices. If $n = 1$ then it must have zero edges. Suppose then that all trees on $n$ edges have $n-1$ vertices. If $G$ is a tree on $n+1$. Since [[Tree#Trees Have Leaves|every tree has a leaf]], we can pick a leaf $v$ of $G$ and remove it. The graph $G-v$ is then a tree on $n$ vertices, which has $n-1$ edges by induction. Adding back the edge we deleted, we have $n = (n+1) - 1$ edges in total. The claim follows by induction.

Conversely, say $G$ is a connected graph with $n-1$ edges. If $G$ were not a tree, then it would contain a cycle. Cut one edge in this cycle. Cutting an edge of a cycle does not disconnect a graph, so we're left with a connected graph with $n-2$ edges. But this is impossible since any connected graph on $n$ vertices must have at least $n-1$ edges. To see this, start with $n$ isolated vertices. Adding an edge decreases the number of components by at most one. It then takes at least $n-1$ edge additions to bring us to one component.