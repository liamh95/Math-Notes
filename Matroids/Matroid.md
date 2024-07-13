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

- (I1): $0\in \mathcal I$;
- (I2): If $I\in \mathcal I$ and $I'\subseteq I$, then $I' \in \mathcal I$;
- (I3): If $I_1$ and $I_2$ are in $\mathcal I$ and $|I_1| <|I_2|$, then there is an element $e\in I_2 \setminus I_1$ such that $I_1 \cup e \in \mathcal I$.

The elements of $\mathcal I$ are the **independent sets** of $M$ and $E$ is the **ground set**. We call axiom (I2) the *hereditary* axiom and (I3) the *independence augmentation* axiom. Any subset of $E$ not in $\mathcal I$ is **dependent**.

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

