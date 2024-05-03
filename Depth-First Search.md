Date Created: 2024-04-03
References: #ref/NONE
Tags: #theorem #graph-theory/algorithms #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


We assume all vertices are initially marked as unexplored.

```ad-algorithm
title: Depth-First Search

**Input:** A vertex $v$ in the graph $G = (V, E)$
**Output:** A labelling of each edge in the component containing $v$ as a *tree edge* or a *back edge*, where the tree edges form a spanning tree of the component containing $v$.

`DFS`$(v)$
1. Mark $v$ as explored
2. `for` each out-edge $(v,w)$
	1. `if` $w$ is not explored
		1. Label the edge $(v,w)$ as a *tree edge*
		2. `DFS`$(w)$
	2. `else` label the edge $(v, w)$ as a *back edge*

```

Of course, if $G$ is an undirected graph, just replace the out-edges with regular edges.

```ad-theorem
title: Depth-First Search Correctness and Runtime

The Depth-First Search algorithm explores all vertices in the component containing $v$. The tree edges form a spanning tree of $G$ and the algorithm runs in time $O(|V| + |E|)$. 

```

<i>Proof.</i> Assuming correctness, runtime is easy. Each vertex is processed exactly once and each edge is traversed at most once (or labelled as a back edge), so the runtime is $O(|V|+|E|)$.