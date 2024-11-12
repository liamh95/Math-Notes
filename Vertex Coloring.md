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

## Vertex coloring

```ad-definition
title: Vertex Coloring

Let $G = (V,E)$ be a graph. A **vertex coloring** (or just **coloring** usually if it's clear from context that we're coloring vertices) is a map $c: V\to [k]$ for some positive integer $k$. When $k$ is specified, we call $c$ a **$k$-coloring**. The coloring $c$ is **proper** if $uv\in E$ implies that $c(u) \neq c(v)$, i.e., adjacent vertices receive different colors. If $G$ admits a proper $k$ coloring, we call $G$ **$k$-colorable**.

```

## Chromatic number

### Definition

```ad-definition
title: Chromatic number

Let $G = (V,E)$ be a graph. The smallest positive integer $k$ such that $G$ admits a proper $k$-coloring is the **chromatic number** of $G$ and is denoted by $\chi(G)$.
```

### Lower bounds

In general, the maximum degree $\Delta$ of a graph $G$ does not give us a lower bound on the chromatic number. Indeed, if $G$ is any bipartite graph, then $\chi(G) = 2$ regardless of $\Delta$.

### Upper bounds


## Algorithms

### Greedy algorithm

Here is an algorithm that takes in a graph $G$ (stored as an adjacency list) of maximum degree $\Delta$ (we can either think of $\Delta$ as being given or we can determine $\Delta$ by just querying every vertex for its degree) and constructs a proper $(\Delta+1)$-coloring of $G$. In particular, the [[Vertex Coloring#Chromatic number#Definition|chromatic number]] of $G$ is at most $\Delta+1$.

```ad-algorithm
title: Greedy algorithm for vertex coloring

**Input:** a graph $G = (V,E)$ with maximum degree $\Delta$
**Output:** a proper coloring $c: V \to [\Delta+1]$

1. Let $c: V\to [\Delta+1]$ be a partial function, initialized to the null function
2. `for each` vertex $v\in V$:
	1. $S \gets [\Delta+1]$
	2. `for each` vertex $u\in N(v)$:
		1. `if` $c(u)$ is not null, remove it from $S$
	3. Let $c(v)$ be an arbitrary element in $S$
3. `return` the function $c$
```

Since the maximum degree of $G$ is $\Delta$, we remove at most $\Delta$ elements from $S$ in loop 2.2. Consequently, in line 2.3, $S$ is nonempty and we can assign a color to $c(v)$. 

The runtime of this algorithm depends on your model of computation. If you only care about queries to the adjacency list of $G$, then this algorithm uses at most $|V|\Delta$ queries (really, it uses exactly $2|E|$ queries since every edge gets queried once for each of its endpoints). We also have a bound of $O(|V|\Delta)$ queries in the RAM model since the only auxiliary data structure we use is the list $S$ and all we do with it is throw elements out of it (we need random access to throw elements out, but this costs $O(1)$ in the RAM model).