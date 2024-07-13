Date Created: 2024-07-12
References: [[Alon, Noga and Krivelevich, Michael - Divisible subdivisions]]
Tags: #theorem #probabilistic-method #combinatorial-number-theory  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## General Case

```ad-theorem
title: Zero-Sum Directed Cycles with Edge Weights in $\mathbb Z_q$

Let $q\geq 2$ be an integer and let $D$ be th e complete digraph on $N:= \lceil 2q\ln q\rceil$ vertices with edge weights $w(e) \in \mathbb{Z}_q$. Then $D$ contains a directed cycle $C$ of total weight divisible by $q$.

```

### Proof

<i>Proof.</i> Let $c: V(D) \to \mathbb{Z}_q$ be a random assignment of the elements of $\mathbb Z_q$ to the vertices of $D$. For every vertex $u$, let $A_u$ be the event that $u$ has an outneighbor $v$ satisfying $c(v) = c(u) + w(uv)$, i.e., that the change in label corresponds to incrementing by the edge weight. To calculate $\Pr[\overline{A_u}]$, let's condition on the value of $c(u)$:
$$
\begin{align}
\Pr[\overline{A_u}]  &= \sum_{x \in \mathbb Z_q}\Pr[\overline{A_u},\ c(u) = x]\\
&= \sum_{x\in \mathbb Z_q}\Pr[\overline{A_u}\mid c(u) = x]\Pr[c(u) = x]\\
&= \frac 1q \sum_{x \in \mathbb Z_q}\left(1 - \frac 1q\right)^{N-1}\\
&= \left(1 - \frac 1q\right)^{N-1}.
\end{align}
$$
By our choice of $N$, this quantity is strictly less than $1/N$, so by a union bound, [[Probabilistic Method Basic Idea|there is]] an assignment $c$ for which all of the $A_u$ hold. Fix such a $c$. and let $H$ be the subdigraph formed by, for each vertex $v\in V(D)$, choosing an outgoing edge $(u,v)$ so that $c(v) = c(u) + w(uv)$. Every outdegree in $H$ is 1, so it contains a directed cycle $C = u_1\cdots u_\ell$. If we sum all weights along the edges of $C$, letting $u_{\ell+1} = u_1$, we have
$$
\sum_{i=1}^\ell w(u_iu_{i+1}) = \sum_{i=1}^\ell\big( c(u_{i+1}) - c(u_i) \big) = 0.
$$

## Prime Case

In the case where $q = p$ is a prime, we can get rid of the $\ln q$ term in the number of vertices.

```ad-theorem
title: Zero-Sum Directed Cycles with Edge Weights in $\mathbb{Z}_p$.

Let $p \geq 2$ be a prime and let $D$ be a complete digraph on $2p-1$ vertices with edge weights $w(e) \in \mathbb{Z}_p$. Then $D$ contains a directed cycle $C$ of total weight divisible by $p$.
```

### Proof

*Proof.* If there are two opposite edges $uv$ and $vu$ with $w(uv) = -w(vu)$ then this 2-cycle does the trick, so we assume there is no such pair of edges.

In this case, we claim that for every $k<p$ there are distinct vertices $x_0, x_1, y_1, x_2, y_2, \ldots, x_k, y_k$ in $D$ and a set $S$ of $k+1$ distinct elements of $\mathbb Z_p$ so that for every $s\in S$ there is a directed $x_0x_k$-path $P_s$ of total weight $s$. This path will be made of $k$ subpaths $Q_1, \ldots Q_k$, in this order, where $Q_i$ is either just the edge $x_{i-1}x_i$ or the two-edge path $x_{i-1}y_ix_i$.

We prove this by induction on $k$. This vacuously holds for $k=0$ if we take any $x_0$ since the required path is just the empty path and $S = \{0\}$. Assume it holds for $k<q-1$. Our plan is to take the $x_0, x_1, y_1, \ldots, x_k, y_k$ and $S$ this gives us and introduce new $x_{k+1}, y_{k+1}$ and modify $S$ so that everything works. To this end, let $u$ and $v$ be any two vertices of $D$ that are not in $\{x_0, x_1, x_2, \ldots, x_k, y_k\}$. If it were the case that $w(x_ku) = w(x_kv) +w(vu)$ and $w(x_kv) = w(x_ku) + w(uv)$, then we would have $w(uv) = -w(vu)$, which would contradict our earlier assumption. Without loss of generality then, assume that $w(x_ku) \neq w(x_kv) + w(vu)$ and set $x_{k+1}:= u$ and $y_{k+1}:= v$.

Now by assumption, $w(x_ku) \neq w(x_kv)+w(vu)$, so let $T$ be the set consisting of these distinct elements of $\mathbb{Z}_p$. Now take an element $s'$ in the sumset $S+T$. Write $s' = s+t$ for some $s\in S$ and $t\in T$. By the induction hypothesis, there is an $x_0x_k$-path of weight $s$. If $t = w(x_ku)$, then append the edge $x_ku$ to this path. If $t = w(x_kv)+w(vu)$, then append $x_kvu$ instead. We then always have an $x_0x_{k+1}$ path of weight $s'$. By the [[Cauchy-Davenport Theorem]], $|S+T| \geq |S|+|T|-1 = k+1$, establishing our claim.

Now if we take $k = p-1$, our claim says  that for every $s\in \mathbb{Z}_p$ there is a directed $x_0x_{p-1}$-path of weight $s$. Choose $s = -w(x_{p-1}x_0)$ and add the edge $x_{p-1}x_0$ to get a zero-sum cycle.