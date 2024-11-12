Date Created: 2024-11-11
References: [[Jukna, Stasys - Extremal Combinatorics - 2011]]
Tags: #definition #in-progress #design-theory

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Design

```ad-definition
title: Design

Let $X = \{1, \ldots, v\}$ be a set of *points* (or *varieties*). A $(v,k,\lambda)$-**design** over $X$ is a collection $\mathcal D$ of distinct subsets of $X$ called *blocks* such that the following are satisfied:
1. each set in $\mathcal D$ contains exactly $k$ points;
2. every pair of distinct points is contained in eactly $\lambda$ blocks.

The number of blocks is denoted by $b$, and if we replace (2) above with
2'. every $t$-element subset of $X$ is contained in exactly $\lambda$ blocks,
then the corresponding family $\mathcal D$ is a $t-(v,k,\lambda)$-design.

If $b = v$, then we say that the design is **symmetric**.

```

## Steiner system

```ad-definition
title: Steiner system

A **Steiner system**, $S(t,k,v)$, is a $t-(v,k,\lambda)$-[[Design#Design|design]] with $\lambda=1$, i.e., every $t$ element subset is contained in one block, and each block has size $k$.
```

### Steiner triple system

```ad-definition
title: Steiner triple system

A **Steiner triple system** is a [[Design#Steiner system|Steiner system]] $S(2,3,v)$. That is, there are $v$ points, arranged into blocks of size 3, each pair of which appears in exactly one block.
```

## Design parameter equations

```ad-proposition
title: Design parameter equations

Let $\mathcal D$ be a $(v, k, \lambda)$-[[Design#Design|design]] with $b$ blocks. Then every point in the underlying set lies in exactly $r$ blocks, where $r$ satisfies the equations
$$
r(k-1) = \lambda (v-1)
$$
and
$$
bk=vr.
$$
```

*Proof.* Suppose the point $a$ appears in $r_a$ blocks. Consider the set
$$
S_a = \{ (x,B): B\in \mathcal D,\ a,b\in B,\ a\neq x \}.
$$
We do some double-counting. On one hand, each of the $v-1$ points not equal to $a$ appears in exactly $\lambda$ blocks with $a$, so $|S_a| = \lambda(v-1)$. On the other hand, for each of the $r_a$ blocks $B$ containing $a$, there are $|B|-1 = k-1$ ways to choose the element of $B$ that is not $a$, so $|S_a| = r_a(k-1)$. So we have
$$
\lambda(v-1) = |S_a| = r_a(k-1).
$$
Notice that the left-most expression is independent of $a$, so we have the first equation.

As for the second, consider the set
$$
S = \{(x,B): B\in \mathcal D,\ x\in B\}.
$$
For each point $x$, there are $r$ blocks containing it, so $|S| = vr$. On the other hand, each of the $b$ blocks contains $k$ elements, so $|S| = bk$.