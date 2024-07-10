Date Created: 2024-07-09
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #definition #graph-theory 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Vertex Cut

```ad-definition
title: Vertex Cut

Let $x$ and $y$ be distinct nonadjacent vertices in $G$. An **$xy$-vertex-cut** is a subset $S$ of $V(G)\setminus \{x,y\}$ such that $x$ and $y$ belong to different components of $G\setminus S$. We say that $S$ **separates** $x$ and $y$.

A vertex cut separating some pair of nonadjacent vertices of $G$ is called a vertex cut of $G$, and one with $k$ elements is a **$k$-vertex cut**.

```

## Local Cut Function

```ad-definition
title: Local Cut Function

For vertices $x$ and $y$, the minimum size of a vertex cut separating $x$ and $y$, denoted by $c(x,y)$, is the **local cut function** (evaluated at $(x,y)$).
```