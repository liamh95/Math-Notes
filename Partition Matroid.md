Date Created: 2024-07-16
References: [[Oxley, James - Matroid Theory - 2011]]
Tags: #definition #matroids #in-progress 

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
title: Partition Matroid

Let $\pi = E_1 \cup E_2 \cup \cdots \cup E_r$ be a partition of $E$ into non-empty sets and let $\mathcal B$ consist of those subsets of $E$ that contain exactly one element from each $E_i$. Then $\mathcal B$ is the set of [[Matroid Base#Definition|bases]] of a [[Matroid#Definition|matroid]], $M_\pi$ on $E$, which we call the **partition matroid** associated with $\pi$.

```


## Independent sets and circuits

The independent sets of $M_\pi$ are
$$
\mathcal I(M_\pi) = \{X\subseteq E: |X\cap E_i| \leq i\ \text{for all }1\leq i \leq r \}
$$
and its [[Circuit#Definition|circuits]] are
$$
\mathcal C(M_\pi) = \big\{ \{a,b\}: a\neq b\text{ and }a,b\in E_i\text{ for some }1\leq i \leq r  \big\}.
$$