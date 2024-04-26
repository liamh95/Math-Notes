Date Created: 2024-04-22
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 4]]
Tags: #theorem #ramsey-theory/hypergraph-ramsey-numbers #ramsey-theory/ramsey-numbers #author/erdos-paul #author/rado-richard

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: 3-Uniform Ramsey Upper Bound Erdős-Rado

The [[Hypergraph Ramsey Numbers|hypergraph Ramsey number]] $r_3(s,t)$ satisfies
$$
r_3(s,t) \leq 2^{\binom{r(s-1, t-1)}{2}},
$$
where $r(s,t)$ is the usual [[Ramsey Number]].

```

<i>Proof.</i> Let $N = 2^{\binom{r(s-1, t-1)}{2}}$ and let $\chi$ be a two-coloring of the the edges of $K_N^{(3)}$, whose vertex set we take to be $[N]$. Our plan is to construct a set of vertices $\{v_1, \ldots, v_{r(s-1, t-1)}\}$ such that, for any pair $1\leq i < j \leq r(s-1, t-1)$, all triples $\{v_i, v_j, v_k\}$ with $k > j$ are of the same color, $\chi'(v_i, v_j)$. If we two-color the edges of $K_{r(s-1, t-1)}$ with the coloring $\chi'$, then there is either a red $K_{s-1}$ or a blue $K_{t-1}$. This clique with $v_{r(s-1, t-1)+1}$ forms a red set of size $s$ or a blue set of size $t$ with respect to $\chi$.

We'll construct this set greedily. First, pick an arbitrary vertex $v_1$ and set $S_1:= V\setminus \{v_1\}$. Assume that after we've picked $\{v_1, \ldots, v_i\}$, we also have a set $S_i$ such that for any $1\leq a<b \leq i$, all triples $\{v_a, v_b, w\}$, with $w\in S_i$ are the same color. Let $v_{i+1}$ be an arbitrary vertex in $S_i$ and let $S_{i, 0} = S_i\setminus \{v_{i+1}\}$. Now say we've already constructed $S_{i,j}\subseteq S_{i, 0}$ such that, for every $h\leq j$ and $w\in S_{i,j}$, all triples $\{v_h, v_{i+1}, w\}$ have the same color. If the number of edges $\{v_{j+1}, v_{i+1}, w\}$ with $w\in S_{i,j}$ that are red is at least $|S_{i,j}|/2$, then let
$$
S_{i, j+1}:= \{w: \{v_{j+1}, v_{i+1}, w\}\text{ is red and }w\in S_{i,j} \}
$$
and set $\chi'(i+1, j+1)$ to be red. Otherwise, let
$$
S_{i, j+1}:= \{w: \{v_{j+1}, v_{i+1}, w\}\text{ is blue and }w\in S_{i,j} \}
$$
and set $\chi'(i+1, j+1)$ to be blue. Then let $S_{i+1} = S_{i,i}$. Now $\{v_1, \ldots, v_{i+1}\}$ and $S_{i+1}$ can continue the algorithm. At worst, for each edge $v_{i+1}v_{j+1}$ that we color $\chi'$, the set $S_{i,j}$ is at most halved. We then lose a factor of at most two for each of the $\binom{r(s-1, t-1)}{2}$ edges colored by $\chi'$.