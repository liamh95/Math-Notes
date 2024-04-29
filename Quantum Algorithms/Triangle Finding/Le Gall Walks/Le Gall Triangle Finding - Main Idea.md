Date Created: 2024-04-29
References: [[Le Gall, Francois - Improved quantum algorithm for triangle finding via combinatorial arguments - 2014]]
Tags: #theorem #quantum-computation/graph-algorithms #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Intro

Say we have an undirected, unweighted graph $G = (V,E)$. Our task is to find three vertices in $G$ that form a triangle, if such a triple exists. This is known to be no harder than Boolean matrix multiplication, which implies that triangle finding in an $n$-vertex graph can be solved in $O(n^{\omega+\epsilon})$ for any constant $\epsilon > 0$, where $\omega$ is the exponent of square matrix multiplication (the state of the art at time of this paper was apparently $\omega < 2.3729$) (I think this is *time* complexity, not query complexity).

### Quantum query complexity

Here we use **adjacency queries**, that is, we can submit pairs $\{u,v\}$ of vertices to an oracle, which tells us whether or not $uv\in E$. In the quantum query model, we can query this oracle in superposition.

The randomized classical query complexity is $\Omega(n^2)$, which matches the "trivial upper bound". We can do better with quantum. If we Grover search over all $\binom n3$ possible triangles, Grover search brings  the quantum query complexity down to $O(n^{3/2})$, already better than classical. Szegedy used amplitude amplification and combinatorics to get $\tilde O(n^{10/7})$.

The main tech used to beat this bound, and what is used here, is search via quantum walks, first due to Ambainis (originally used for the element distinctiveness problem). Magniez, Santha and Szegedy used quantum walk search to get $\tilde O(n^{13/10})$ for triangle finding.

Belovs was able to use the adversary method bring it down to $O(n^{35/27})$. Magniez and Santha then used learning graphs to get $O(n^{9/7})$: the best before this paper.

As for quantum query lower bounds here, the best is the "trivial" $\Omega(n)$. Belovs and Rosmanis showed that the edge-weighted version requires $\Omega(n^{9/7}\sqrt{\log n})$ queries. This paper beats this lower bound, which shows that the unweighted version of this problem is, in some sense, intrinsically different.

```ad-theorem
title: Le Gall Triangle Finding - Main Theorem

There exists a quantum algorithm, that, given as input the oracle of an unweighted graph $G$ on $n$ vertices, outputs a triangle of $G$ with probability at least $2/3$ if a triangle exists, and uses $\tilde O(n^{5/4})$ queries to the oracle.

```

## Overview

For notation, we let $\mathcal E(U)$ denote the set of all pairs $\{u,v\}$ with $u,v\in U\subseteq V$. Think of it as the set of "potential edges" in $U$.

First we take a uniformly random set $X\subseteq V$ of size $\Theta(\sqrt n \log n)$, then check to see if there is a triangle with a vertex in $X$. Using Grover, we can do this in
$$
O\left( \sqrt{|X|\cdot |\mathcal E(V)|}  \right)  = \tilde{O}(n^{5/4})
$$
queries. Let
$$
S := \bigcup_{x\in X}\mathcal E(N_G(x))
$$
be the set of pairs of common neighbors of vertices in $X$. If we didn't find a triangle with a vertex in $X$, then any triangle in $G$ has an edge in $\mathcal E(V) \setminus S$ (the author notes that this preliminary step has been used before in other algorithms for e.g. Boolean matrix multiplication and the $\tilde O(n^{10/7})$ algorithm for triangle-finding). The contribution of this paper is how we check for a triangle edge here.

For any $Y\subseteq V$ and $w\in V$, define
$$
\Delta_G(X, Y, w):= \mathcal E(Y\cap N_G(w))\setminus S
$$
to be the pairs in $Y\cap N_G(w)$ that are not common neighbors of any vertex in $X$. It's "easy" to see that with high probability on the choice of $X$, for any $\{v, v'\} \in \mathcal E(V)\setminus S$,
$$
|\{w\in V: vw\in E\text{ and }v'w\in E\}|\leq \sqrt n.
$$
From this it follows that for a randomly chosen $w$, the expected size of $\Delta_G(X, V, w)$ is at most $n^{3/2}$ or more generally, for a random $Y\subseteq V$, the expected size of $\Delta_G(X, Y, w)$ is at most $|Y|^2/\sqrt n$.

### Making an assumption

Let's assume there's a positive $c$ such that
$$
|\Delta_G(X, Y, w)| \leq \frac{c|Y|^2}{\sqrt n}\text{ for any }Y\subseteq V\text{ and any }w\in V.
$$
Now say we have a vertex $w$ and some $B\subseteq V$ of size $\sqrt n$ such that we now $\Delta_G(X, B, w)$. We can then check to see if there is a pair $\{v_1, v_2\}\in \mathcal E(B)\setminus S$ such that $\{v_1, v_2, w\}$ is a triangle with
$$
O\left( \sqrt{|\Delta_G(X, B, w)} \right) = O\left(\sqrt{\frac{c|B|^2}{\sqrt n}} \right) = O(n^{1/4})
$$
queries using Grover and our assumption. Without our assumption, this would take $\Theta(\sqrt{|B|^2}) = \Theta(\sqrt n)$  queries. The catch is that constructing $\Delta_G(X, B, w)$ is potentially expensive. Constructing $S$ off the bat requires $\Theta(n^{3/2})$ queries if we were to just Grover it (have to check every vertex to see if it's a neighbor of a vertex in $X$). Instead, find another set $A$ (via quantum walk) of size $n^{3/4}$ such that
$$
\left(\bigcup_{w\in V}\Delta_G(X, A, w) \right)\cap E \neq \emptyset
$$
and build $\mathcal E(A)\setminus S$ at the same time. Now do what we mentioned earlier, taking $B\subseteq A$ instead. Notice that $\Delta_G(X, B, w)$ can be built from $\mathcal E(A)\setminus S$, which we have. Indeed, we can build $\mathcal E(A)\setminus S$ in
$$
O(|A|\cdot |X|) = \tilde O(n^{5/4})
$$
queries. So basically...

1. Search for $A\subseteq V$ of size $n^{3/4}$ such that $(\cup_{w\in V} \Delta_G(X, A, w))\cap E \neq \emptyset$, whil e building $\mathcal E(A)\setminus S$ by quantum walk
2. Find a vertex $w\in V$ such that $\Delta_G(X, A, w)\cap E\neq \emptyset$
3. Find $B\subseteq A$ of size $\sqrt n$ such that $\Delta_G(X, B, w)\cap E\neq \emptyset$ while building $\Delta_G(X, B, w)$ by quantum walk and the fact that we already have $\mathcal E(A)\setminus S$.
4. Check if $\Delta_G(X, B, w)\cap E\neq \emptyset$ in $O(n^{1/4})$ queries
We still need to deal with what happens when our assumption doesn't hold.