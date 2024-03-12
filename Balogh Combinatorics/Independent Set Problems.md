Date Created: 2024-03-11
References: #ref/NONE
Tags: #example #graph-theory/triangle-free #graph-theory/containers #graph-theory/matchings #arithmetic-combinatorics/arithmetic-progressions #graph-theory/mantels-theorem #arithmetic-combinatorics/szemeredis-theorem 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Here are some graph theory problems that can be posed as problems revolving around independent sets.

```ad-example
title: Matchings

Say we want to count the matchings in some graph $G$. Consider the **line graph**, $L(G)$, whose vertex set is the edge set of $G$, where two edges are connected if and only if they are incident in $G$.

Then a set $M\subseteq E(G)$ is a matching in $G$ if and only if $M\subseteq V(L(G))$ is an independent set in $L(G)$. So counting matches in $G$ is equivalent to counting independent sets in $L(G)$.

```

```ad-example
title: Triangle-free graphs

Say we want to count the number of triangle-free graphs on $n$ vertices. We can build a 3-uniform hypergraph $\mathcal H$ as follows. Let $V(\mathcal H) = E(K_n)$, where $efg \in E(\mathcal H)$ if and only if $e$, $f$ and $g$ form a triangle in $K_n$.

Then a graph $G$, a subgraph of $K_n$, is triangle-free if and only if $E(G)$ corresponds to an independent set in $\mathcal H$. In particular, the Turán problem of maximizing the number of edges in a triangle-free graph, is the problem of estimating the independence number of this particular $\mathcal H$. Mantel's theorem says that $\alpha(\mathcal H) = \lfloor n^2/4\rfloor$.
```

```ad-example
title: Arithmetic Progressions

Say we want to count subsets of $[n]$ containing no $k$-term arithmetic progression ($k$-AP).
We can build a $k$-uniform hypergraph $\mathcal H$ with $V(\mathcal H) = [n]$ and $S\subseteq \binom{[n]}{k}$ is an edge in $H$ if and only if $S$ is a $k$-AP.

Then $A\subseteq [n]$ is $k$-AP-free if and only if it corresponds to an independent set in $\mathcal H$. The problem of finding a large $k$-AP-free set is equivalent to finding a large independent set in this $\mathcal H$. Szemer´edi's theorem says that $\alpha(\mathcal H) = o(n)$.
```
