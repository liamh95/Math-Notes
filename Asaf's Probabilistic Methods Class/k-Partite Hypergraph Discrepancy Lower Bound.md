Date Created: 2024-04-09
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method/first-moment-method #discrepancy

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Let $V = V_1 \cup \cdots \cup V_k$, where the $V_i$'s are disjoint sets of size $n$. Let $h: \binom{V}{k}\to \{\pm 1\}$ be a two-coloring of the $k$-sets of $V$. We say that a $k$-set $E$ is **crossing** if $E$ intersects each of the $V_i$'s exactly once. For any set $S\subseteq V$, define
$$
h[S]:= \sum_{E\in \binom Sk}h(E).
$$

```ad-theorem
title: k-Partite Hypergraph Discrepancy Lower Bound

With $V$ and $h$ as defined above, suppose that $h(E) = 1$ for all crossing $k$-sets. Then there is an $S\subseteq V$ for which
$$
h(S) \geq c_kn^k,
$$
where $c_k$ is a constant independent of $n$.

```

<i>Proof.</i> For each $i$, let $x$ be included in the set $S$ with probability $p_i$, where we will choose the $p_i$'s later. Let $X:= h[S]$. We compute $h[S]$ by evaluating $h(E)$ for all of the $k$-sets $E$ in $S$, so these contribute
$$
X_E := \begin{cases}
h(E)&\text{if }E\in \binom Sk,\\
0&\text{otherwise}
\end{cases}.
$$
We say that $E$ has type $(a_1, \ldots, a_k)$ if $|E\cap V_i| = a_i$ for each $i$. For these $E$,
$$
E[X_E] = h(E)\Pr[E\subseteq S] = h(E)p_1^{a_1}\cdots p_k^{a_k}.
$$
Collecting terms by type, we have
$$
E[X] = \sum_{a_1 + \cdots + a_k = k}p_1^{a_1}\cdots p_k^{a_k}\sum_{E\text{ is type }(a_1, \ldots, a_k)}h(E).
$$
The sets of type $(1, \ldots, 1)$ are the crossing sets, and $h(E) = 1$ for all of these by assumption. There are $n^k$ of these, so 
$$
\sum_{E\text{ is type }(1, \ldots, 1)}h(E) = n^k.
$$
For any other type $(a_1, \ldots, a_k)$, there are fewer than $n^k$ terms, and $h(E) = \pm 1$, so for these,
$$
	\left| \sum_{E\text{ is type }(a_1, \ldots, a_k)}h(E)\right| \leq n^k.
$$
Thus,
$$
E[X] = n^k f(p_1, \ldots, p_k),
$$
where $f$ is a homogeneous polynomial of degree $k$. By [[Homogeneous Polynomials Common Large Value]], we can select $p_1, \ldots, p_k$ so that $|f(p_1, \ldots, p_k)|\geq c_k$ for some constant $c_k$ independent of $n$. Thus,
$$
E[|X|] \geq |E[X]|  \geq c_kn^k.
$$
By the [[First Moment Method|first moment method]], there is some $S\subseteq V$ for which $|h(S)| \geq c_kn^k$.