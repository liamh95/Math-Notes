Date Created: 2024-07-16
References: [[Oxley, James - Matroid Theory - 2011]]
Tags: #definition #matroids  #in-progress 

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
title: Matroid Base

Let $M$ be a [[Matroid#Definition|matroid]]. A maximal independent set in $M$ is a **base** or **basis** of $M$.

```


## All bases have the same size

```ad-proposition
title: All bases have the same size

If $B_1$ and $B_2$ are bases of a matroid $M$, then $|B_1| = |B_2|$.
```

*Proof.* Say $|B_1| < |B_2|$. Since $B_1$ and $B_2$ are independent, we can augment $B_1$ by $B_2$, i.e., there is some $e\in B_2\setminus B_1$ such that $B_1 \cup e$ is also independent, contradicting maximality.

## Basis exchange

```ad-proposition
title: Basis exchange

The set $\mathcal B$ of bases of a matroid has the following property:
- (B2): If $B_1$ and $B_2$ are members of $\mathcal B$ and $x\in B_1\setminus B_2$, then there is an element $y$ of $B_2\setminus B_1$ such that $(B_1\setminus x) \cup y$ is in $\mathcal B$.
```

*Proof.* By maximality, $B_1 \setminus x$ and $B_2$ are independent sets. We also have that $|B_1\setminus x| < |B_2|$ since all bases have the same cardinality. We can then augment $B_1\setminus x$ by $B_2$, i.e., there is an element $y$ of $B_2 \setminus (B_1\setminus x)$ such that $(B_1\setminus x)\cup y \in \mathcal I$. Note that $y\in B_2\setminus B_1$. The set $(B_1\setminus x)\cup y$ is independent, so it's contained in some maximal independent set $B_1'$. All bases have the same size, so $|B_1'| = |B_1| = |(B_1\setminus x)\cup y|$. So it must be the case that $(B_1\setminus x) \cup y$ is a basis of $M$ satisfying (B2).