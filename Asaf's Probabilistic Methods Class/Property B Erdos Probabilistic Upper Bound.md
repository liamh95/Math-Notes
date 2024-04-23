Date Created: 2024-04-08
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method #graph-theory

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

We sort of invert Erdős' argument for [[Property B Erdos Probabilistic Lower Bound]]. This time, the edges are random and the colorings are deterministic.

```ad-theorem
title: Property B Erdos Probabilistic Upper Bound

There is an $n$-uniform hypergraph with $(1+o(1))\frac{e\ln 2}{4}n^22^n$ edges that does not have [[Property B]]. That is,
$$
m(n) < (1+o(1))\frac{e\ln 2}{4}n^22^n.
$$

```

<i>Proof.</i> Let $V$ be a set with $N$ points, where we will optimize $N$ later. Choose the sets $S_1, \ldots, S_m\in \binom Vn$ uniformly and independently at random. Fix a two-coloring $\chi$ of $V$. Say $\chi$ colors $a$ of the vertices of $N$ red and $N-a$ of them blue. Then for any of our edges,
$$
\Pr[S_i\text{ is }\chi\text{-monochrmatic}] = \frac{\binom an + \binom{N-a}{n}}{\binom Nn} \geq \frac{2\binom{N/2}{n}}{\binom Nn} =:p.
$$
We've used the convexity of the binomial coefficient to say that the numerator of the second term is minimized when the arguments are the same. Now let $A_\chi$ be the event that no edge is $\chi$-monochromatic. If we can show that $\Pr[\cup_\chi A_\chi] < 1$, then we will be [[Probabilistic Method Basic Idea|done]], since there will exist a choice of edges such that all colorings have a monochromatic edge. By a union bound and the [[Linear Bound for Exponential]],
$$
\Pr\left[\bigcup_\chi A_\chi\right]\leq 2^N(1-p)^m \leq 2^Ne^{-mp},
$$
since there are $2^N$ two-colorings $\chi$. The idea is to then set $m = \lceil \frac{N \ln 2}{p}\rceil$, so then this quantity is less than 1 and we'll have $m(n) \leq m$. So we want to choose $p$ so as to minimize $N/p$. Well,
$$
p = \frac{2\binom {N/2}{n}}{\binom Nn} = 2^{1-n}\prod_{j=0}^{n-1}\frac{N-2j}{N-j}.
$$
Now if $n$ is small compared to $N$, say $N = \omega(n^{3/2})$, then 
$$
\frac{N-2j}{N-j} = 1 - \frac{j}{N-j} = 1 - \frac{j}{N} + O\left(\frac{j^2}{N^2}\right).
$$
So this expression for $p$ is about
$$
2^{1-n}\prod_{j=0}^{n-1}\left(1-\frac jN\right) \leq 2^{1-n}\prod_{j=0}^{n-1}e^{-j/N} \approx 2^{1-n}e^{-n^2/2N}.
$$
Now we just do some calculus to see that this is minimized when $N = n^2/2$, which gives the desired conclusion.