Date Created: 2024-07-10
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #theorem #graph-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Fan Lemma

```ad-theorem
title: Fan Lemma

Let $G$ be a $k$[[k-Connectivity#$k$-Connectivity|-connected]], let $x$ be a vertex of $G$, and let $Y\subseteq V\setminus \{x\}$ be a set of at least $k$ vertices of $G$. Then there is a $k$-[[Fan#Fan|fan]] in $G$ from $x$ to $Y$.

```

## Proof

Before proving this, we need a quick lemma about $k$-connectivity.

```ad-proposition

Let $G$ be a $k$-connected graph and let $H$ be a graph obtained from $G$ by adding a new vertex $y$ and joining it to at least $k$ vertices in $G$. Then $H$ is also $k$-connected.
```

*Proof of Proposition:* Let $S$ be any subset of $H$ of size $k-1$. By [[Menger's Theorem#Menger's Theorem|Menger's theorem]], it suffices to show that $H\setminus S$ is connected. If $y \in S$, then throwing $S$ out of $H$ is like throwing a set of size $k-2$ out of $G$. Since $G$ is $k$-connected, $H\setminus S$ will be connected.

So we'll assume that $y\notin S$. Since we gave $y$ at least $k$ neighbors in $G$ and $|S| = k-1$, $y$ must have at least one neighbor, $z$, not in $S$. We have that $G\setminus S$ is connected and $z \in G\setminus S$, so $yz$ is an edge in $H\setminus S$. We then have that $(G\setminus S) + yz$ is a connected spanning subgraph of $H\setminus S$, so $H\setminus S$ is connected.

<i>Proof of Fan Lemma.</i> Create a new vertex $y$ and connect it to every vertex in $Y$. The resulting graph, call it $H$, by the above proposition, is $k$-connected. By Menger's theorem, there are $k$ internally disjoint $xy$-paths. By deleting $y$ from these paths, we obtain a $k$-fan from $x$ to $Y$.