Date Created: 2024-03-05
References: #ref/NONE
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
	\alpha(G) &= 
\end{align}
$$