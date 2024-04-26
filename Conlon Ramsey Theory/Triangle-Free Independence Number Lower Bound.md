Date Created: 2024-03-05
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 3]]
Tags: #theorem #graph-theory/independence-number #shearer #graph-theory/triangle-free 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Shearer's Lower Bound for Independence Number

Let $G$ be a triangle-free graph of order $N$ and average degree $d$. Then
$$
	\alpha(G) \geq f(d)N,
$$
where
$$
	f(d) = \frac{d\log d - d + 1}{(d-1)^2},\quad d\neq 0,1.
$$

```

<i>Proof.</i> It's easy to verify with basic calculus that $f$ is continuous, convex and strictly decreasing from 1 to 0. It also satisfies the differential equation
$$
(d-d^2)f'(d) - (d+1)f(d) + 1 = 0.
$$
We'll induct on $N$. The claim is vacuously true for $N = 0$ and also for all values of $N$ when $d=0$, so we'll assume that $d>0$ and that the claim holds for values up to some $N>0$.

For any vertex $x$, let the graph $G_x$ be obtained from $G$ by deleting $x$ and all of its neighbors. We let $\tilde{d}(x)$ denote the average degree of the neighbors of $x$ and we let $d_x$ be the average degree of $G_x$. Since $G$ is triangle free, no two neighbors of $x$ are joined by an edge, so
$$
e(G_x) = e(G) - \sum_{y\in N(x)}d(y) = \frac{Nd}{2} - \sum_{y\in N(x)}d(y) = \frac{Nd}{2} - d(x)\tilde{d}(x).
$$
By the convexity of $f$, $f(d_x) \geq f(d) + (d_x-d)f'(d)$, so by induction,
$$
\begin{align}
	\alpha(G) &= 1 + \frac 1N\sum_{v\in V}\alpha(G_x)\text{ (why?)}\\
	&\geq 1 + \frac 1N\sum_{v\in V}f(d_x)(N-1-d(x))\\
	&\geq 1 + \frac 1N\sum_{v\in V}\big( f(d) + (d_x-d)f'(d)\big)(N-1-d(x))\\
	& = 1 + Nf(d) - (d+1)f(d)+(d^2+d)f'(d)+\frac{f'(d)}{N}\sum_{v\in V}(d_x(N-d(x)-1)-Nd).
\end{align}
$$
Now by the expression we have for $e(G_x)$ above, so
$$
d_x(N - d(x) - 1) = Nd - 2d(x)\tilde{d}(x).
$$
Hence,
$$
\alpha(x) \geq 1 + Nf(d) - (d+1)f(d) + (d^2+d)f'(d)+\frac{f'(d)}{N}\sum_{x\in V}\big( -2d(x)\tilde{d}(x)\big).
$$
Now since
$$
\sum_{v\in V}d(x)\tilde{d}(x) = \sum_{x\in V}\sum_{y\in N(x)}d(y) = \sum_{y\in V}d^2(y) \geq Nd^2,
$$
and $f'<0$,
$$
\alpha(G) \geq 1 + Nf(d) - (d+1)f(d)+(d-d^2)f'(d).
$$
Now by that equation at the top of this proof, $1-(d+1)f(d)+(d-d^2)f'(d) = 0$, and we're done.