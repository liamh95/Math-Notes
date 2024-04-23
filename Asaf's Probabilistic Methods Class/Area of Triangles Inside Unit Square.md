Date Created: 2024-04-12
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method/first-moment-method #combinatorial-geometry #probabilistic-method/alterations 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Area of Triangles Inside Unit Square

For a set $S$ of points in the unit square $[0,1]^2$, let $T(S)$ be the minimum area of a triangle whose vertices are three distinct points in $S$. There is a set $S$ of $n$ points in $[0,1]^2$ such that $T(S) \geq 1/(100n^2)$.

```

<i>Proof.</i> Let $P$, $Q$ and $R$ be chosen from $[0,1]^2$ independently and uniformly at random and let $\mu(PQR)$ be the area of the resulting triangle. If we let $x$ be the distance from $P$ to $Q$, then if we just look at the area of an annulus,
$$
\Pr[r \leq x \leq r+\Delta r] \leq \pi(r+\Delta r)^2 - \pi r^2 = \pi(2r\Delta r + (\Delta r)^2).
$$
So in the limit, $\Pr[r \leq x \leq r+dr] \leq 2\pi r\ dr$. Now say we want to estimate $\Pr[\mu \leq \epsilon]$. If we condition on $x = r$, then the height of $R$ from the segment connecting $P$ and $Q$ can't exceed $2\epsilon/r$. This corresponds to a strip of width $4\epsilon / r$ and length at most $\sqrt 2$. This corresponds to a probability of at most $4\sqrt 2 \epsilon / r$. Since $0 \leq r \leq \sqrt 2$ (maximized when $\overline{PQ}$ is a diagonal), we have
$$
\Pr[\mu \leq \epsilon] \leq \int_0^{\sqrt 2}(4\sqrt 2 \epsilon / r) (2\pi r)dr = 16\pi \epsilon.
$$
If we choose $2n$ points $P_1, \ldots, P_{2n}$ uniformly and independently at random from $[0,1]^2$ and let $X$ be the number of triangles $P_iP_jP_k$ with area less than $1/(100n^2)$. By the above inequality, this occurs with probability at most $\frac{16\pi}{100 n^2}$, so
$$
E[X] \leq \binom{2n}{3}\cdot \frac{16\pi}{100n^2} < n.
$$
By the [[First Moment Method]], there is a set of $2n$ points in $[0,1]^2$ with fewer than $n$ triangles of area less than $1/(100n^2)$. If we delete one vertex from each such triangle, we have at least $n$ points left and no triangle with area less than $1/(100n^2)$.