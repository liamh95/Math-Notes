Date Created: 2024-08-05
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
Tags: #theorem #graph-theory/bipartite-graphs  

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Hall's Theorem

```ad-theorem
title: Hall's Theorem

Let $G$ be a bipartite graph with bipartition $X \cup Y$. Suppose that $|N(S)| \geq |S|$ for every $S\subseteq X$. Then $G$ contains a matching saturating $X$.

```

## Proof by Menger's Theorem

<i>Proof.</i> First we claim that every set [[Linking and Detaching#Detaching|detaching]] $X$ from $Y$ has at least $|X|$ elements. To see this, first note that $|Y| \geq |N(X)| \geq |X|$. Now let $S$ be a set of size $|X|-1$ and let $x = |S\cap X|$ and $y = |S\cap Y|$ so that $x+y = |X|-1$. Now by hypothesis we have
$$
\begin{align}
|N(X-S)| &\geq |X-S|\\
&= |X|-x\\
&= |X|-(x+y)+y\\
&= y+1\\
&= |Y\cap S| + 1.
\end{align}
$$
As a consequence, $X-S$ has a neighbor in $Y-S$, so deleting $S$ won't detach $X$ from $Y$. Therefore, a detaching set has size at least $|X|$. Since deleting $X$ clearly detaches it from $Y$, the size of a minimal detaching set is $|X|$. There is [[Linking and Detaching#Minimal Detaching Set|thus]] a set of size $|X|$ inside $X$, namely $X$ itself, [[Linking and Detaching#Linking|linked]] to a set of size $|X|$ inside $Y$. This linkage forms our $X$-saturating matching.