Date Created: 2024-07-12
References: [[Oxley, James - Matroid Theory - 2011]]
Tags: #definition #matroids 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Definition

```ad-definition
title: Matroid

A **matroid** $M$ is a pair $(E, \mathcal I)$ consisting of a finite set $E$ and a collection $\mathcal I$ of subsets of $E$ having the following three properties:

- (I1): $\emptyset\in \mathcal I$;
- (I2): If $I\in \mathcal I$ and $I'\subseteq I$, then $I' \in \mathcal I$;
- (I3): If $I_1$ and $I_2$ are in $\mathcal I$ and $|I_1| <|I_2|$, then there is an element $e\in I_2 \setminus I_1$ such that $I_1 \cup e \in \mathcal I$.

The elements of $\mathcal I$ are the **independent sets** of $M$ and $E$ is the **ground set**. We call axiom (I2) the *hereditary* axiom and (I3) the *independence augmentation* axiom. Any subset of $E$ not in $\mathcal I$ is **dependent**.

Per the [[Circuit#Definition|circuit]] [[Circuit#Circuit Characterization of Matroids|characterization]] of matroids, we can also define a matroid $M$ as a pair $(E, \mathcal C)$ where $E$ is a finite set and $\mathcal C$ is a collection of subsets of $E$ having the following properties:
- (C1): $\emptyset \notin \mathcal C$;
- (C2): If $C_1$ and $C_2$ are in $\mathcal C$ and $C_1\subseteq C_2$, then $C_1 = C_2$;
- (C3): If $C_1$ and $C_2$ are distinct elements of $\mathcal C$ and $e\in C_1\cap C_2$, then there is a member $C_3 \in \mathcal C$ with $C_3 \subseteq (C_1\cup C_2)\setminus e$.

```


## Isomoprhism

```ad-definition
title: Matroid isomorphism

We say that matroids $M_1$ and $M_2$ are **isomorphic** (and write $M_1 \cong M_2$) if there is a map $\psi: E(M_1) \to E(M_2)$ such that $\psi(X)$ is independent in $M_2$ if and only if $X$ is independent in $M_1$.
```



## Examples

### Matrix example

```ad-example
title: Matroid from a matrix

Let $E$ be the column *labels* of an $m\times n$ matrix $A$ over some field $\mathbb F$, and let $\mathcal I$ be the subsets $X$ of $E$ for which the multiset of columns labelled by $X$ is is a set and is linearly independent over $\mathbb F$. Then $(E, \mathcal I)$ is a matroid.

We call this matroid $M[A]$ the **vector matroid** of $A$.
```

*Proof.* The empty set is always taken to be linearly independent, so (I1) is satisfied. Subsets of linearly independent sets are also linearly independent, so we have (I2) as well. Now say $I_1$ and $I_2$ are two subsets of $E$ that correspond to linearly independent sets with $|I_1| < |I_2|$. Let $W$ be the span of $I_1\cup I_2$, the dimension of which is at least $|I_2|$. If $I_1 \cup e$ is linearly dependent for all $e \in I_2 \setminus I_1$, then $W$ is in the span of $I_1$. But then
$$
|I_2| \leq \dim W \leq |I_1| < |I_2|,
$$
a contradiction. So there must be an $e\in I_2\setminus I_1$ such that $I_1 \cup e$ is in $\mathcal I$, so (I3) holds too.


### Graph example

```ad-example
title: Matroid from a graph

Let $E$ be the set of edges of a graph  $G$ and $\mathcal C$ the set of edge sets of cycles of $G$. Then $\mathcal C$ is the set of circuits of a matroid on $E$ called the **cycle matroid** of $G$, $M(G)$. 
```

*Proof.* The empty set isn't a cycle and cycles do not properly contain other cycles, so we have (C1) and (C2). Now say distinct cycles $C_1$ and $C_2$ share a common edge $e = \{u,v\}$. Let $P_i$ be the $uv$-path in $G$ whose edges are $G\setminus C_i$. Starting at $u$, go along $P_1$ until we hit vertex $w$, the first vertex at which the next edge of $P_1$ is not in $P_2$. Keep going along $P_1$ until the first time a vertex $x$ is reached that is not $w$, but is also in $P_2$. Join the section of $P_1$ from $w$ to $x$ to the section of $P_2$ from $x$ to $w$. This cycle is in $(C_1 \cup C_2) \setminus e$.