Date Created: 2024-09-09
References: [[Diestel, R - Graph Theory - 2017]]
Tags: #theorem #graph-theory/coloring  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Vizing's Theorem

```ad-theorem
title: Vizing's Theorem

Let $G = (V,E)$ be a graph. Then the [[Chromatic Number#Edge chromatic number|edge chromatic number]], $\chi'(G)$, satisfies
$$
\Delta(G) \leq \chi'(G) \leq \Delta(G)+1,
$$
where $\Delta(G)$ is the maximum degree of $G$.

```

This proof is from Diestel's book. I think it's pretty much the same as Vizing's original proof.

<i>Proof.</i> The first inequality is straightforward: any proper edge coloring of $G$ must assign every edge incident to a vertex of maximum degree a separate color. We induct on the number of edges in $G$. The claim is clearly true when $e(G) = 0$, so now let's suppose the claim is true for all graphs with fewer edges than our graph $G$.

By the induction hypothesis, for any edge $e\in E(G)$, there is a $(\Delta+1)$ edge coloring of $G\setminus e$. If we pick some vertex $v$, then since $d(v) \leq \Delta$, there is some color $\beta \in [\Delta+1]$ missing at $v$ (i.e. no edge incident to $v$ is colored $\beta$ under this coloring). For any other color $\alpha$, there is a unique maximal walk starting at $v$ whose edges are alternately colored $\alpha$ and $\beta$ (it's unique because the coloring is proper). This walk is a path (if it intersected itself, then some vertex would have two $\alpha$- or two $\beta$-colored edges touching it). Call this the $\alpha/\beta$-path from $v$. 

Now suppose that $G$ has no proper $(\Delta+1)$-edge coloring. We claim the following.
- For any edge $xy$ and any coloring of $G-xy$ in which the color $\alpha$ is missing at $x$ and $\beta$ is missing at $y$, the $\alpha/\beta$-path from $y$ ends at $x$.
Otherwise, we could toggle the colors along the $\alpha/\beta$-path from $y$ (so that $y$ has an edge colored $\beta$ at it) and then color $xy$ with $\alpha$ to obtain a $(\Delta+1)$-edge coloring of $G$.

Let $xy_0$ be an edge in $G$. By induction, there is a $(\Delta+1)$-edge coloring of $G-xy_0$, $c_0$. Say the color $\alpha$ is missing at $x$ in this coloring. Let $y_0, \ldots, y_k$ be a maximal sequence of distinct neighbors of $x$ in $G$ so that the color $c_0(xy_{i+1})$ is missing at $y_i$ in $c_0$ for each $i<k$. For each graph $G_i = G-xy_i$, define the coloring $c_i$ by
$$
c_i(e) = \begin{cases}
c_0(xy_{j+1}) &\text{for }e=xy_j\text{ with }0\leq j \leq i-1\\
c_0(e) &\text{otherwise}
\end{cases}.
$$That is, for each $j < i$, we shift the colors back by one. Note that as a consequence of this shifting, in each of the colorings $c_i$, the same colors are missing at $x$ as in $c_0$. 

Say $\beta$ is missing at the last vertex $y_k$ in the coloring $c_0$. Then $\beta$ is also missing at $y_k$ in each $c_i$ for $0 \leq i \leq k$. Note that $\beta$ is *not* missing at $x$ in $c_0$, since then we could just extend the coloring $c_k$ to $G$ by coloring the edge $xy_k$ with $\beta$, creating a $(\Delta+1)$-edge coloring. Therefore, $x$ has a $\beta$-colored edge for each coloring $c_i$. By the maximality of the set $\{y_0, \ldots, y_k\}$, the $\beta$ colored edge $xy$ in $c_0$ must be of the form $xy_i$ for some specific $1 \leq i < k$, since otherwise we could just let $y = y_{k+1}$.

By the definition of $c_i$, we have that $\beta = c_0(xy_i) = c_{i-1}(xy_i) = c_k(xy_{i-1})$ (think of how each $c_j$ shifts the colors). Let $P$ be the $\alpha/\beta$-path from $y_k$ with respect to $c_k$. By the bulleted claim, $P$ must end in $x$. Since $\alpha$ is missing at $x$, $P$ must end in a $\beta$-colored edge -- it must then end with the edge $y_{i-1}x$. Now let $P'$ be the $\alpha/\beta$-path from $y_{i-1}$ with respect to $c_{i-1}$. The internal edges of $P$ are not changed as we change the color $c_i$ (these colors only differ on the edges incident to $x$), so $P'$ uses the relevant edges from $P$ (but in reverse order), and thus visits $y_k$. The edge leading to $y_k$ in $P'$ must be colored $\alpha$ since $\beta$ is missing at $y_k$. So $P'$ ends at $y_k$, but this contradicts the bulleted claim, which insists that $P'$ should end at $x$ -- a contradiction.