Date Created: 2024-07-09
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]; [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
Tags: #theorem #graph-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Menger's Theorem

```ad-theorem
title: Menger's Theorem (Undirected Vertex Version)

In any graph $G$ where $x$ and $y$ are nonadjacent, the maximum number of pairwise internally disjoint $xy$-paths is equal to the minimum number of vertices in an $xy$-[[Vertex Cut#Vertex Cut|vertex-cut]]. In terms of the [[k-Connectivity#Local Connectivity|local connectivity]] and [[Vertex Cut#Local Cut Function|local cut]] functions,
$$
p(x,y) = c(x,y).
$$

```

## Inductive Proof

<i>Proof.</i> Let's induct on $e(G)$. Set $k: = c_G(x,y)$. Notice that $p(x,y) \leq  k$ since any collection $\mathcal P$ of internally vertex-disjoint paths must meet any $xy$-cut in at least $|\mathcal P|$ vertices. Our goal is then to show that $p(x,y) \geq k$. Also notice that there must be some edge $e = uv$ incident with neither $x$ nor $y$, as otherwise all $xy$-paths would have length 2.

Let $H$ be the graph obtained by contracting this edge $e$. Since $H$ is a subgraph of $G$, the number of $xy$-paths can only go down, so $p_H(x,y) \leq p_G(x,y)$. By induction, $c_H(x,y) = p_H(x,y)$. We have that $c_G(x,y) \leq c_H(x,y)+1$ since adding an end of $e$ to any $xy$-cut in $H$ makes an $xy$-cut in $G$. Thus,
$$
p_G(x,y) \geq p_H(x,y) = c_H(x,y) \geq c_G(x,y) - 1 = k-1.
$$
If this inequality is strict then $p_G(x,y) \geq k$ and we're done, so let's suppose equality holds. Then $c_H(x,y) = k-1$ and there's some minimal $xy$-cut $S = \{v_1, \ldots, v_{k-1}\}$ in $H$. Let $X$ be the component containing $x$ and let $Y$ be the component containing $Y$ in $H\setminus S$. Since $|S| = k-1$ and $c_G(x,y) = k$, $S$ is not an $xy$-cut in $G$, so there is an $xy$-path in $G\setminus S$. Since the only thing that changed from $G$ to $H$ was $e$ getting contracted and $S$ is an $xy$-cut in $H$, it must be the case that there is an $xy$-path in $G\setminus S$ that goes through $e$. Without loss of generality, $u\in X$ and $v\in Y$.

![[menger1.png]]

Now contract $Y$ to a single vertex $y$ and call the resulting graph $G/Y$. We claim that any $xy$-cut $T$ in $G/Y$ is also an $xy$-cut back in $G$. Otherwise, if we had an $xy$-path $P$ in $G$ avoiding $T$, then $P/Y$ in would be an $xy$-path in $G/Y$ also avoiding $T$. Then we must have that $c_{G/Y}(x,y) \geq c_G(x,y) = k$. But $S\cup \{u\}$ is an $xy$-cut of $G/Y$ of size $k$, so $c_{G/Y}(x,y) \leq k$ and hence, $S\cup \{u\}$ is a minimum $xy$-cut in $G/Y$.

By induction, $p_{G/Y}(x,y) = c_{G/Y}(x,y) = k$, so there are $k$ internally disjoint paths $P_1, \ldots, P_k$ in $G/Y$, and so each vertex of $S\cup \{u\}$ lies on exactly one of them. Without loss of generality, $v_i \in P_i$ for $1\leq i \leq k-1$ and $u \in P_k$. By the same reasoning applied to $G/X$, there are $k$ internally disjoint paths $Q_1, \ldots Q_k$ in $G/X$ with $v_i \in Q_i$ for $1\leq i \leq k-1$ and $v\in Q_k$.

![[menger2.png]]
![[menger3.png]]

Now just stitch these together to make the $xy$-paths $xP_iv_iQ_iy$ and $xP_kuvQ_ky$ in $G$. Hence, $p_G(x,y) \geq k$ and we're done.

![[menger4.png]]



## Pym's Proof (in Bollobas' book)

Bollobas formulates this slightly differently (but equivalently). For him, the [[k-Connectivity#Local Vertex Connectivity (Bollobás)|local vertex connectivity]] $\kappa(x,y)$ is the minimum number of vertices needed to kill all $xy$-paths. He then states Menger's theorem like this.

```ad-theorem
title: Menger's Theorem

Let $x,y\in V(G)$ for some graph $G$ with $x\neq y$. Then the maximum number of internally vertex disjoint $xy$-paths is $\kappa(x,y)$, where $\kappa$, the [[k-Connectivity#Local Vertex Connectivity (Bollobás)|local vertex connectivity function]] counts the number of vertices whose deletion separates $x$ and $y$.
```

*Proof.* Take any set of size $\kappa(x,y)$ whose deletion kills all $xy$-paths. Any collection $\mathcal P$ of internally vertex disjoint paths meets this set in at least $|\mathcal P|$ vertices, so the maximum number of internally vertex disjoint paths is at most $\kappa(x,y)$. It remains then to show the converse.

Bollobas (it's Pym's proof really) uses the notions of [[Linking and Detaching]]. He [[Linking and Detaching#Minimal Detaching Set|proves]] that for any sets $X$ and $Y$, if $k$ is the minimum size of an $X$-$Y$ [[Linking and Detaching#Detaching|detaching]] set, then there is a $k$-set [[Linking and Detaching#Linking|linking]] some $X_0\subseteq X$ to some $Y_0\subseteq Y$. The proof of this result is more or less the same as the induction proof above. Once we have this, set $X = N(x)$ and $Y = N(y)$. If $k$ is the minimum size of an $X$-$Y$ detaching set, then there is a $k$-set in $X$ linked to a $k$-set in $Y$. But the minimum size of an $X$-$Y$ detaching set is $\kappa(x,y)$. We then have $\kappa(x,y)$ internally vertex disjoint $xy$-paths.

## Flow Proof



## Edge Form

By considering the [[Line Graph#Line Graph|line graph]], we obtain the edge form of Menger's theorem.

```ad-theorem
title: Menger's Theorem (Edge Form)

Let $x\neq y$ be distinct vertices of the graph $G$. Then the maximum number of edge-disjoint $xy$-paths in $G$ is $\lambda(x,y)$, where $\lambda$, the [[k-Connectivity#Local Edge Connectivity (Bollobás)|local edge connectivity function]] counts the minimum number of edges whose deletion separates $x$ from $y$.
```

*Proof.* Like in the vertex form, first consider a set of $\lambda(x,y)$ edges whose deletion kills all $xy$-paths. Any set $\mathcal P$ of edge disjoint $xy$-paths meets this set in at least $|\mathcal P|$ edges, so the maximum number of edge disjoint $xy$-paths is at most $\lambda(x,y)$.

Consider the [[Line Graph#Line Graph|line graph]] $L(G)$ and let $X\subseteq V(L)$ be the set of edges (in $G$) incident to $x$ and let $Y$ be the edges incident to $Y$. We [[Linking and Detaching#Minimal Detaching Set|know]] that if $k$ is the minimum size of an $X$-$Y$ [[Linking and Detaching#Detaching|detaching]] set in $L(G)$, then there is a $k$-set in $X$ [[Linking and Detaching#Linking|linked]] to a $k$-set in $Y$ in $L(G)$. The minimum size of an $X$-$Y$ detaching set in $L(G)$ is $\lambda(x,y)$, so we get this many vertex-disjoint paths in $L(G)$. Vertex disjoint paths in $L(G)$ correspond to edge-disjoint paths in $G$.