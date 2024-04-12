Date Created: 2024-04-09
References: #ref/NONE
Tags: #theorem #probabilistic-method/first-moment-method #combinatorial-geometry

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Balancing Vectors

Let $v_1, \ldots, v_n$ be unit vectors in $\mathbb R^n$. Then there are $\epsilon_1, \ldots, \epsilon_n \in \{\pm 1\}$ such that
$$
\|\epsilon_1v_1 + \cdots + \epsilon_nv_n\| \geq \sqrt n.
$$
There are also signs for which the opposite inequality holds.

```

<i>Proof.</i> Let $\epsilon_1, \ldots, \epsilon_n$ be selected uniformly and independently from $\{\pm 1\}$ and set
$$
X:= \|\epsilon_1v_1 + \cdots + \epsilon_nv_n\|^2.
$$
Then 
$$
E[X] = \sum_{i,j}E[\epsilon_i\epsilon_j]\langle v_i,v_j\rangle.
$$
Now when $i=j$, $\epsilon_i\epsilon_j = 1$ with probability 1. On the other hand, when $i\neq j$, $E[\epsilon_i\epsilon_j] = 0$, so the above expectation is exactly equal to $n$. By the [[First Moment Method]], there is then a choice of $\epsilon_1, \ldots, \epsilon_n$ for which $X$ exceeds (or fails to exceed) its epectation.