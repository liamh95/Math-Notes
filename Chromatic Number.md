Date Created: 2024-09-09
References: #ref/NONE
Tags: #definition #graph-theory/coloring   #in-progress 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Vertex chromatic number

```ad-definition
title: Vertex coloring and chromatic number

A **(vertex) coloring** of the graph $G = (V,E)$ is a map $c: V(G) \to [k]$ for some $k$.
The coloring is **proper** if $c(u) \neq c(v)$ whenever $uv\in E(G)$.
The smallest positive $k$ so that there exists a proper $k$-coloring is the **chromatic number** of $G$ and is denoted $\chi(G)$.

```

## Edge chromatic number

```ad-definition
title: Edge coloring and edge chromatic number

An **edge coloring** of the graph $G = (V,E)$ is a map $c: E(G) \to [k]$ for some $k$.
The coloring is **proper** if $c(e) \neq c(f)$ whenever $e$ and $f$ have exactly one vertex in common.
The smallest positive $k$ so that there exists a proper $k$-edge coloring is the **edge chromatic number** of $G$ and is denoted $\chi'(G)$.
```