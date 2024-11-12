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

## Difference Set

```ad-definition
title: Difference Set

Let $2\leq k  < v$ and $\lambda \geq 1$. A $(v, k, \lambda)$ **difference set** is a $k$-element set $D = \{d_1, \ldots, d_k\}\subseteq \mathbb Z_v$ such that the collection of values $d_i-d_j$, $i\neq j$ contains every element of $\mathbb Z_v \setminus \{0\}$ exactly $\lambda$ times.

```

## Design parameter equations

Say $D$ is a difference set with the parameters given above. Then the $k(k-1)$ pairs of indices $i\neq j$, correspond to differences $d_i - d_j$, giving the $v-1$ elements of $\mathbb Z_v \setminus \{0\}$ exactly $\lambda$ times each, so
$$
k(k-1) = \lambda (v-1).
$$
## Different translates are different

If $D$ is a difference set as above, then for any $a\in \mathbb Z_v$, we have the **translate**
$$
a + D := \{a + d_1,\ldots, a+d_k\}.
$$
We claim that our assumption that $k<v$ implies that all the translates of $D$ are different. Indeed, if $D+a = D$ for some $a\neq 0$, then there is some permutation $\pi$ of $[k]$ so that $\pi(i)\neq i$ and $a+d_i = d_{\pi(i)}$ for all $i\in [k]$. So then $a$ can be written as a difference $d_{\pi(i)} - d_i$ in $k$ ways. But our assumption that  $k<v$ and the equation $k(k-1) = \lambda (v-1)$ above implies that $\lambda < k$, so we have a contradiction.

## Translates form a design

```ad-proposition
title: Translates of a difference set form a design

If $D = \{d_1, \ldots, d_k\}$ is a $(v, k, \lambda)$ difference set, then the translates
$$
D, 1+D, \ldots, (v-1)+D
$$
are the blocks of a symmetric $(v, k, \lambda)$ [[Design#Design|design]].
```

*Proof.* We have $v$ blocks (they are indeed different by the observation above) over $v$ points, so if these really do form the blocks of a design, we have symmetry. We just need to show that every pair of points is contained in exactly $\lambda$ blocks.

Say $x,y\in \mathbb Z_v$ with $x\neq y$ and $x,y\in a+D$. Then $x = a+d_i$ and $y = a+d_j$ for some $i \neq j$. So $d_i - d_j = d:= x-y$. By the definition of a difference set, there are exactly $\lambda$ pairs $i\neq j$ such that $d_i-d_j = d$, and for each such pair, there is exactly one $a$ for which $x,y\in a+D$, namely $a = x-d_i = y-d_j$.

## Construction: quadratic residues

Where do difference sets come from? Here's one construction that uses quadratic residues.

```ad-theorem
title: Quadratic residues form a difference set

If $v$ is a prime power and $v\equiv 3 \pmod 4$, then the nonzero quadratic residues in $\mathbb Z_v$ form a $(v, k, \lambda)$ difference set with $k = (v-1)/2$ and $\lambda = (v-3)/4$.
```

The condition that $v\equiv 3\pmod 4$ is to ensure that $-1$ is not a square in $\mathbb Z_v$ (why would we care?).

*Proof.* Let $D$ be the set of all nonzero squares and set $k = |D|$. Notice that 