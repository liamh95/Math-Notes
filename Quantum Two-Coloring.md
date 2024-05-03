Date Created: 2024-05-02
References: [[D'Hondt, Ellie - Quantum approaches to graph colouring - 2009]]
Tags: #theorem #quantum-computation/graph-algorithms #graph-theory/coloring #in-progress 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-problem
title: Bipartite Decision Problem

Given a graph $G = (V, E)$ (stored as an adjacency list), determine whether or not $G$ is bipartite.

Optionally: output a bipartition if $G$ is indeed bipartite.
```

Say $G$ has $n$ vertices. We can represent a (vertex) two-coloring of $G$ as a vector in $(\mathbb C^2)^{\otimes n}$. That is, if we write $i$ in binary, then the vector $|i\rangle$ corresponds to the coloring where the $j$-th bit of $i$ corresponds to the color of vertex $j$. 

Start with a uniform superposition of all colorings,
$$
H^{\otimes n}|0\rangle^{\otimes n} = 2^{-n/2}\sum_{s\in \{0,1\}^n}|s\rangle.
$$
If $ij$ is an edge, then we want to get rid of any basis states in this superposition that contain $|00\rangle_{ij}$ or $|11\rangle_{ij}$ (that is, states whose $i$-th and $j$-th bits are both 0 or both 1). One idea is to consider the unitary operator $E_{ij}$, whose action on the basis states is defined by
$$
\begin{align}
|00\rangle_{ij} &\mapsto \frac{1}{\sqrt 2}\big(|01\rangle_{ij} + |00\rangle_{ij}\big)\\
|01\rangle_{ij} &\mapsto \frac{1}{\sqrt 2}\big(|01\rangle_{ij} - |00\rangle_{ij}\big)\\
|10\rangle_{ij} &\mapsto \frac{1}{\sqrt 2}\big(|10\rangle_{ij} + |11\rangle_{ij}\big)\\
|11\rangle_{ij} &\mapsto \frac{1}{\sqrt 2}\big(|10\rangle_{ij} - |11\rangle_{ij}\big).
\end{align}
$$
For example, if our graph consists of just two vertices connected by an edge, the uniform superposition of colorings is
$$
\frac 12 \big( |00\rangle + |01\rangle + |10\rangle + |11\rangle\big).
$$
When we apply $E_{01}$, then we'll be left with
$$
\frac{1}{\sqrt 2}\big( |01\rangle + |10\rangle \big),
$$
a uniform superposition on *proper* two-colorings. We can do this as long as we have all color combinations for $i$ and $j$ present in equal amplitude. The unitaries $E_{ij}$ preserve equality of amplitude of the endpoints. We can ensure that these color combinations are present by processing edges in [[Depth-First Search|DFS]] tree ordering.

For each back-edge $e_{ij}$, consider the projective measurement with operators $M_{ij}$ and $I-M_{ij}$, where
$$
\begin{align}
M_{ij} &= |01\rangle_{ij}\langle 01|_{ij} + |10\rangle_{ij}\langle 10|_{ij}\\
I-M_{ij} &= |00\rangle_{ij}\langle 00|_{ij} + |11\rangle_{ij}\langle 11|_{ij}
\end{align}
$$