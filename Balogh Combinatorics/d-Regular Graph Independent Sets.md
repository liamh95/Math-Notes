Date Created: 2024-03-12
References: #ref/NONE
Tags: #theorem #graph-theory/containers #graph-theory/regular-graphs

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Suppose $G$ is $n/2d$ disjoint copies of $K_{d,d}$. Then
$$
|\mathcal I(G)| = (2^{d+1}-1)^{n/2d} = 2^{n/2 + o(n)},
$$
if $d = \omega(1)$. We'll show that this is essentially tight for a certain range of $d$.

```ad-theorem
title: $d$-Regular Graph Independent Sets

Let $G$ be a $d$-regular graph on $n$ vertices where $\log n \ll d\ll n/2$. Then the number of independent sets in $G$ is at most $2^{n/2 + o(n)}$.

```

<i>Proof.</i> Applying the [[Graph Container Lemma]] for some $t$ gives us a collection $\mathcal C$ of containers satisfying
$$
|\mathcal I(G)| \leq |\mathcal C|\cdot 2^{\max_{C\in \mathcal C}|C|}.
$$
But our lemma doesn't tell us anything about the size of the individual containers, just that they have small maximum degree. The idea is then to show that, in this case, subgraphs of $d$-regular graphs with small max degree are small.

Set $t = \sqrt{d\log d}$ and apply the [[Graph Container Lemma]]. For any independent set $I$, the containers algorithm outputs a set $S(I)$ with $|S(I)| \leq n/\sqrt{d\log d}$. The container lemma also says that $G_S := G\setminus N(S)$ satisfies $\Delta(G_S) < \sqrt{d\log d}$. (The container is $C(S) = S\cup G_S$?)

Let's estimate the number of vertices in $G_S$, which we denote by $m$. Let's count the crossings between $G_S$ and $G\setminus G_S$. Since $G$ is $d$-regular and each vertex in $S$ had degree at least $t$ in $G_i$ when it was added to $S$, 
$$
md - mt \leq e(G_S, G\setminus G_S) \leq (n-m)d.
$$
Rearranging, we have
$$
m \leq \frac{n}{2}\cdot \frac{d}{d-t/2} \leq \frac{n}{2}\left( 1 + \sqrt{\frac{d}{\log d}}\right).
$$
This is a supersaturation result: if $G$ is $d$-regular and any set with more than $(1+\epsilon)\alpha(G)$ vertices has many edges. Note that $n/2$ is a reasonable threshold, since the $K_{d,d}$ example shows that we can get independent sets of size $n/2$.

Plugging this into our bound for the number of independent sets, we have that
$$
|\mathcal I(G)| \leq \binom{n}{\leq n/t}2^{\frac{n}{2}(1 + \sqrt{d/\log d})} \leq 2^{\frac n2(1 + 6\sqrt{d/\log d})}.
$$