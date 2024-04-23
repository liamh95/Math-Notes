Date Created: 2024-04-12
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method #graph-theory 
Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Property B Cherkashin and Kozik Probabilistic Lower Bound

Any $n$-uniform hypergraph with at least $c\sqrt{\frac{n}{\log n}}2^n$ edges has [[Property B]]. In particular,
$$
m(n) = \Omega\left( \sqrt{\frac{n}{\log n}}2^n \right).
$$

```

<i>Proof.</i> The idea is to do a more careful analysis of [[Property B Pluhar Probabilistic Lower Bound|Pluhar's greedy algorithm]] for the $\Omega(n^{1/4}2^n)$ lower bound. The algorithm proceeds by randomly ordering the vertices $V = \{v_1, \ldots, v_N\}$ and coloring them one by one -- coloring the vertex $v_i$ red unless it would produce a monochromatic edge, in which case we color it blue.

The idea in that proof was to look at what happens when we make a monochromatic blue edge: then there are two edges $e$ and $f$ that intersect in exactly one vertex, where all of the vertices in (say) $e$ precede all of the vertices in $f$ with respect to this random ordering. Call such a pair of edges *conflicting* with respect to this ordering. We just used the [[First Moment Method]] to bound the probability that any pair of edges was conflicting.

Say the number of edges we have is $m = k2^{n-1}$. Here we'll choose the ordering by a different procedure (that still produces a uniformly random ordering). For each vertex, independently, choose a uniformly random number in $[0,1]$ and order the vertices according to these random values (note that with probability 1, these are all indeed distinct). Perform the greedy coloring algorithm as described above. Let's bound the probability that any pair of edges is conflicting. Partition $[0,1]$ into the intervals $L$, $M$ and $R$ with $L:= [0, \frac{1-p}{2})$, $M := [\frac{1-p}{2}, \frac{1+p}{2})$, and $R:= [\frac{1+p}{2}, 1]$.

How can a pair of edges be conflicting? The probability that $e$ and $f$ conflict with $e\subseteq L$ or $f\subseteq R$ is bounded by the probability that there is an edge in $H$ contained in $L$ or $R$. This probability is at most
$$
2k2^{n-1}\left(\frac{1-p}{2}\right)^n = k(1-p)^n.
$$
If we have any other conflicting pairs, the unique vertex in $e\cap f$ must lie in $M$. The probability that this happens is $p$. Given this, and given that the value of this vertex is $x$, the probability that all of the vertices in $e$ precede it and all of the vertices in $f$ proceed it is $x^{n-1}(1-x)^{n-1} \leq 4^{1-n}$. Therefore, the probability that a given pair conflicts is at most $p4^{1-n}$. After union bounding, the probability that we have a conflicting pair is at most
$$
k(1-p)^n + p\cdot 4^{1-n} \cdot m^2 = k(1-p)^n + k^2p.
$$
Now if we use the [[Linear Bound for Exponential]], then this is at most $ke^{-np}+k^2p$, which is minimized when $p = \ln(n/k)/n$. Substituting this back in, the probability that there are no conflicting pairs is less than 1 if
$$
\frac{k^2}{n}(1 + \ln\frac nk) < 1.
$$
If we set $k = c\sqrt{\frac{n}{\ln n}}$ for any $c < \sqrt 2$, then this holds. Under these conditions, there [[Probabilistic Method Basic Idea|exists]] an ordering for which no pairs conflict and the hypergraph has property B.