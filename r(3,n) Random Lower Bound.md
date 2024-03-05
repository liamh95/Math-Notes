Date Created: 2024-03-04
References: #ref/NONE
Tags: #theorem #ramsey-theory/ramsey-numbers #probabilistic-method/alterations #erdos #in-progress

Proved by: <i>Not Applicable</i>
References: Conlon Ramsey theory notes: Lecture 2
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: r(3,n) Random Lower Bound

$$
	r(3, n) \geq c\left(\frac{n}{\log n}\right)^2.
$$

```

<i>Proof.</i> Set $N = c\left(\frac{n}{\log n}\right)^2$ and let $p = \frac{a\log n}{n}$ for some constant $a$ to be determined later. Color each edge of $K_N$ red with probability $p$ and blue with probability $1-p$. The expected number of red triangles is $\Theta( (\frac{n}{\log n})^3)$, so we need to make some alterations. Let $E$ be a minimal set of red edges, that, when recolored blue, destroys all red triangles. We will show that with high probability, recoloring in this way gives no blue $K_n$.

For any subset of vertices $W$, let $C_W$ be the event that the red subgraph induced by $W$ contains an edge $xy$ that is not contained in any red triangle $xyz$ with $z \in V\setminus W$. To see the significance of $C_W$, let $H$ be a maximal triangle-free subgraph of the red graph after recoloring. If the edge $xy$ has been recolored blue, then by maximality, $H+xy$ contains a red triangle (I guess when we add $xy$ to $H$, recolor it red?), $xyz$. If $C_W$ holds, then $z$ is in $W$, in which case, $xz$ and $yz$ are both red. In particular, the blue complement of $H$ is not monochromatic on $W$.

If we can show that $\cap C_W$, where the intersection is over all subsets $W$ of size $n$, occurs with high probability, then there will be no blue $K_n$ and we'll be done. To this end, fix a subset of vertices $W$ of size $n$. Let's estimate $\Pr[\overline{C_W}]$. 

Let $d_i = e^{2i}pn/i$ for $1 \leq i \leq \log n$. By Chernoff, for any vertex $v \in V\setminus W$, 
$$
\Pr[d_W(v) \geq d_i] \leq \left(\frac{enp}{d_i} \right)^{d_i} = \left(ie\right)^{e^{2i}np/i}e^{-2e^{2i}np} \leq e^{-e^{2i}np}.
$$
If we let $N_i = n/e^{2i}$, then the probability $P_i$ that at least $N_i$ vertices in $V\setminus W$ have at least $d_i$ red neighbors in $W$ satisfies
$$
P_i \leq \binom{N}{N_i}e^{-e^{2i}np\cdot N_i} = \binom{N}{N_i}n^{-an} < n^{3ne^{-2i}-an} < n^{-2n-1}
$$
for $a$ sufficiently large (like $a=12$). Union bounding over all $i$, we have that at most $N_i$ vertices have at most $d_i$ red neighbors in $W$ with probability $1-n^{-2n}$.

Now for $i \geq i_0 = \frac{1}{2}(\log n - \log\log n)$, $d_i > 2Np$. By the [[Chernoff Bound]], all vertices have degree at most $2Np$ red neighbors with high probability. If we condition on this event, there are no vertices of red degree greater than $d_{i_0}$ in $W$. Let's count the number of pairs of vertices in $W$ with a common red neighbor in $V\setminus W$. By the above discussion, this is at most
$$
\begin{align}
	N\binom{d_1}{2} + \sum_{i=2}^{i_0-1}N_{i-1}\binom{d_i}{2}
\end{align}
$$