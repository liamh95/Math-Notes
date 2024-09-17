Date Created: 2024-09-09
References: [[Diestel, R - Graph Theory - 2017]]; [[Bollobas, Bela - Graph Theory An Introductory Course - 1979]] - Chapter V Section 2
Tags: #theorem #graph-theory/coloring #graph-theory/algorithms   #in-progress

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

This proof is from Diestel's book.

<i>Proof.</i> The first inequality is straightforward: any proper edge coloring of $G$ must assign every edge incident to a vertex of maximum degree a separate color. We induct on the number of edges in $G$. The claim is clearly true when $e(G) = 0$, so now let's suppose the claim is true for all graphs with fewer edges than our graph $G$.

By the induction hypothesis, for any edge $e\in E(G)$, there is a $(\Delta+1)$ edge coloring of $G\setminus e$. If we pick some vertex $v$, then since $d(v) \leq \Delta$, there is some color $\beta \in [\Delta+1]$ missing at $v$ (i.e. no edge incident to $v$ is colored $\beta$ under this coloring). For any other color $\alpha$, there is a unique maximal walk starting at $v$ whose edges are alternately colored $\alpha$ and $\beta$ (it's unique because the coloring is proper). This walk is a path (if it intersected itself, then some vertex would have two $\alpha$- or two $\beta$-colored edges touching it). Call this the $\alpha/\beta$-path from $v$. 

Now suppose that $G$ has no proper $(\Delta+1)$-edge coloring. We claim this is equivalent to the following.
- For any edge $xy$ and any coloring of $G-xy$ in which the color $\alpha$ is missing at $x$ and $\beta$ is missing at $y$, the $\alpha/\beta$-path from $y$ ends at $x$.
Otherwise, we could toggle the colors along the $\alpha/\beta$-path from $y$ (so that $y$ has an edge colored $\beta$ at it) and then color $xy$ with $\alpha$ to obtain a $(\Delta+1)$-edge coloring of $G$. Conversely, if there was a proper $(\Delta+1)$-edge coloring, we could delete the edge $xy$ and the coloring restricted to $G-xy$ would fail to satisfy this property.

Let $xy_0$ be an edge in $G$. By induction, there is a $(\Delta+1)$-edge coloring of $G-xy_0$, $c_0$. Say the color $\alpha$ is missing at $x$ in this coloring. Let $y_0, \ldots, y_k$ be a maximal sequence of distinct neighbors of $x$ in $G$ so that the color $c_0(xy_{i+1})$ is missing at $y_i$ in $c_0$ for each $i<k$. For each graph $G_i = G-xy_i$, define the coloring $c_i$ by
$$
c_i(e) = \begin{cases}
c_0(xy_{j+1}) &\text{for }e=xy_j\text{ with }0\leq j \leq i-1\\
c_0(e) &\text{otherwise}
\end{cases}.
$$That is, for each $j < i$, we shift the colors back by one. Note that as a consequence of this shifting, in each of the colorings $c_i$, the same colors are missing at $x$ as in $c_0$ and these colorings are valid because we chose the $y_i$'s so that shifting the colors back doesn't cause any conflicts.

![[vizing1.png]]

By the definition of $c_i$, we have that $\beta = c_0(xy_i) = c_{i-1}(xy_i) = c_k(xy_{i-1})$ (think of how each $c_j$ shifts the colors). Let $P$ be the $\alpha/\beta$-path from $y_k$ with respect to $c_k$. By the bulleted claim, $P$ must end in $x$. Since $\alpha$ is missing at $x$, $P$ must end in a $\beta$-colored edge -- it must then end with the edge $y_{i-1}x$. Now let $P'$ be the $\alpha/\beta$-path from $y_{i-1}$ with respect to $c_{i-1}$. The internal edges of $P$ are not changed as we change the color $c_i$ (these colors only differ on the edges incident to $x$), so $P'$ uses the relevant edges from $P$ (but in reverse order), and thus visits $y_k$. The edge leading to $y_k$ in $P'$ must be colored $\alpha$ since $\beta$ is missing at $y_k$. So $P'$ ends at $y_k$, but this contradicts the bulleted claim, which insists that $P'$ should end at $x$ -- a contradiction.

![[vizing2.png]]


## Algorithm

Here's Vizing's original algorithm idea. We present it here for multigraphs like he did. The multigraph form of the theorem looks like this

```ad-theorem
title: Vizing's theorem (multigraphs)

Leg $G$ be a multigraph with maximum degree $\Delta$ where each pair of vertices has at most $p$ parallel edges (so a simple graph has $p = 1$). Then $\chi'(G) \leq \Delta + p$
```

*Proof.* Let's assign the edges colors from $[\Delta + p]$. Say $(a,b)$ is an uncolored edge. Let $A$ and $B$ be the sets of colors missing at $a$ and $b$ respectively. Note that $|A|$ and $|B|$ are both at least $p$. If $A\cap B \neq \emptyset$, i.e., if there is a color missing at both $a$ and $b$, just color $(a,b)$ with that color.

Suppose then that $A\cap B = \emptyset$. 





We can turn the above proof of Vizing's theorem into an algorithm that actually constructs the coloring. Suppose the edge $xy_0$ is uncolored. We will construct the special neighbors $y_0, \ldots, y_k$ as used in the above proof, i.e., there are colors $\beta_1, \ldots$ so that $\beta_i$ is missing at $y_i$ and $xy_{i+1}$  has color $\beta_i$. Say we already have the neighbors $y_0, \ldots, y_i$ and the colors $\beta_0, \ldots, \beta_i$. There is at most one edge $xy$ colored $\beta_i$. If such an edge exists and $y\notin \{y_0, \ldots, y_i\}$, put $y_{i+1} = y$ and let $\beta_{i+1}$ be any color missing at $y_{i+1}$. Otherwise, stop the sequence. Say we stop at $y_k$. The sequence terminates for one of two reasons.
- No edge $xy$ has color $\beta_i$. Recolor the edges $xy_i$ with $i < k$, giving $xy_i$ the color $\beta_i$ (shift the colors back one). This colors everything except for $xy_k$, so just assign it color $\beta_k$.
- For some $j<k$, the edge $xy_j$ already has the color $\beta_k$. Start by recoloring $xy_i$, $i<j$, with $\beta_i$. This just leaves $xy_j$ uncolored. Let $H(s,t_h)$ be the subgraph of $G$ formed by 