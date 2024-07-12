Date Created: 2024-07-11
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #theorem #graph-theory #author/dirac-gabriel

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Theorem

```ad-theorem
title: Dirac's Theorem on Cycles in $k$-Connected Graphs

Let $S$ be a set of $k$ vertices in a $k$-[[k-Connectivity#$k$-Connectivity|connected]] graph $G$, where $k\geq 2$. Then there is a cycle in $G$ which includes all of the vertices of $S$.

```

## Proof

<i>Proof.</i> Let's induct on $k$. The base case, $k=2$ follows directly from [[Menger's Theorem#Menger's Theorem|Menger's theorem]]: any two vertices have at least two internally disjoint paths connecting them and these make a cycle.

Say $k \geq 3$. Take $x\in S$ and let $T = S\setminus x$. Since $G$ is $k$-connected, it's also $(k-1)$-connected, so by induction, there's a cycle $C$ through $T$. If $x\in C$ already then we're done, so let's assume that $x\notin C$.

- If $|C| \geq k$, then the [[Fan Lemma#Fan Lemma|Fan lemma]] tells us there's a $k$-[[Fan#Fan|fan]] in $G$ from $x$ to $C$. The set $T$ divides $C$ into $k-1$ edge-disjoint segments. By the pigeonhole principle, two paths of the fan, $P$ and $Q$ land in the same segment of $C$. The subgraph $C \cup P \cup Q$ contains three cycles, one of which contains $T\cup \{x\} = S$.
- If $|C| = k-1$, the Fan lemma gives us a $(k-1)$-fan from $x$ into $C$, where each vertex of $C$ is the endpoint of one path and we get the same conclusion as above.

![[dirac_kconnect.png]]