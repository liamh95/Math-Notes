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

`DFS`$(v)$
1. Mark $v$ as explored
2. `for` each out-edge $(v,w)$
	1. `if` $w$ is not explored
		1. `DFS`$(w)$

```

Of course, if $G$ is an undirected graph, just replace the out-edges with regular edges.

```ad-theorem
title: Depth-First Search



```

<i>Proof.</i> <% tp.file.cursor(2) %>