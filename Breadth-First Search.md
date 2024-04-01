Date Created: 2024-04-01
References: #ref/NONE
Tags: #theorem #graph-theory/algorithms #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

How do we explore the connected components of a graph?

```ad-algorithm
title: Breadth-Frist Search

**Input: **A graph $G$ and a vertex $s\in V(G)$.
**Output: **An assignment of a parent to every vertex in the component of $s$. These parents trace out a shortest path to $s$ in $G$.

1. Let $Q$ be an empty queue
2. Mark $s$ as explored and enqueue it into $Q$
3. `while` $Q$ is not empty
	1. $v \gets$ $Q$`.dequeue()`
	2. `for` each vertex $w$ adjacent to $v$
		1. `if` $w$ is unexplored
			1. Label $v$ as the parent of $w$
			2. Mark $w$ as explored and enqueue it into $Q$

```

```ad-theorem
title: Breadth-First Search Correctness and Runtime

The Breadth-First Search (BFS) algorithm visits every vertex in the component of $s$ and parents trace a shortest path to $s$. The runtime of this algorithm is $O(m+n)$, where $n = |V(G)|$ and $m = |E(G)|$.

```

<i>Proof.</i> Assuming correctness, it's easy to analyze the runtime. Each vertex in the component of $s$ is enqueued and dequeued exactly once and labeled exactly once. Similarly, each edge is queried at most twice (when we get the neighbors of each vertex). Assuming we store the graph as an adjacency list, this comes out to $O(m+n)$ queries and basic operations (labeling, queue operations).



