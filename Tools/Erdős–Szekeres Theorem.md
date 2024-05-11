Date Created: 2024-05-09
References: [Wikipedia]([Erdős–Szekeres theorem - Wikipedia](https://en.wikipedia.org/wiki/Erd%C5%91s%E2%80%93Szekeres_theorem))
Tags: #theorem #ramsey-theory

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Erdős–Szekeres theorem

For any positive integers $r$ and $s$, any sequence of distinct real numbers of length at least $(r-1)(s-1)+1$ contains a monotone increasing subsequence of length $r$ or a monotone decreasing subsequence of length $s$.

```

<i>Proof.</i> Say we have a sequence of distinct reals of the given length and, for each $n_i$ in this sequence, let $a_i$ be the length of the longest monotone increasing subsequence ending at $n_i$, and $b_i$ the length of the longest decreasing subsequence. We claim that for different $i$ and $j$, the pairs $(a_i, b_i)$ and $(a_j, b_j)$ are different. To see this, say $i< j$. If $n_i < n_j$, then $a_i < a_j$ since we can make the increasing subsequence longer by adding $n_j$. If $n_i > n_j$, then $b_i < b_j$ for the same reason applied to the decreasing subsequence. If the longest increasing subsequence has length at most $r-1$ and the longest decreasing one has length at most $s-1$, then there are at most $(r-1)(s-1)$ possible labels for the pairs. Since we have $(r-1)(s-1)+1$ elements in our sequence, it must then be the case that we have an increasing subsequence of length $r$ or a decreasing subsequence of length $s$.