Date Created: 2024-08-03
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
Tags: #definition #graph-theory 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Strict Path

```ad-definition
title: Strict Path

Let $G$ be a graph and let $X,Y \subseteq V(G)$. A **strict $X$-$Y$ path** is an $X$-$Y$ path is a path from $X$ to $Y$ whose only vertex in $X$ is initial and only vertex in $Y$ is terminal.
```
## Linking

```ad-definition
title: Linking

Let $G$ be a graph and let $X,Y\subseteq V(G)$. We say that $X$ is **linked** to $Y$ if $|X| = |Y|$ and there are $|X|$ vertex-disjoint strict paths from $X$ to $Y$.


```

## Detaching

```ad-definition
title: Detaching

A set $Z\subseteq V(G)$ **detaches** $X\subseteq V(G)$ from $Y\subseteq V(G)$ if in $G-Z$ there is no $X-Y$ path.
```

Note that a set $Z$ detaching $X$ from $Y$ also [[Separator#$k$-Separator|separates]] $X$ from $Y$ if and only if $Z$ is disjoint from both $X$ and $Y$.


## Minimal Detaching Set

```ad-proposition
title: Minimal Detaching Set

Let $X, Y\subseteq V(G)$ for some graph $G$. Let $k$ be the minimal number of elements in an $X$-$Y$ detaching set. Then there is a $k$-set $X_0\subseteq X$ [[Linking and Detaching#Linking|linked]] to some $Y_0\subseteq Y$.
```

*Proof.* This argument is due to J.S. Pym (where they just call this Menger's Theorem) and appears mostly unaltered in Bollobas' book.
We induct on $e(G)$. The claim is clearly true for graphs with a single edge, so let's say the claim holds for all graphs with fewer edges than $G$. Without loss of generality $G$ is connected. We split into two cases depending on how $X$ detaches from $Y$.

- *Case 1: Every $X$-$Y$-detaching $k$-set coincides with either $X$ or $Y$.* Without loss of generality, $|X| = k \leq |Y|$, and assume that $X$ is not contained in $Y$. Then there is some $x_0 \in X-Y$. By the minimality of $k$, $X - x_0$ does not detach $X$ from $Y$, so there is an edge $x_0y_0$ with $y_0\notin X$. (Do they mean $y_0 \in Y-X$? Shouldn't it be a *path*, maybe not an *edge*?) Let $G_0:= G - x_0y_0$.
  
  If $G_0$ also satisfies the hypothesis of this case, then the induction hypothesis just gives us the result. Otherwise, take a minimal separating set $Z_0$ in $G_0$, which will be of size $k-1$. Now $Z_0 \cup x_0$ and $Z_0  \cup y_0$ are detaching sets in $G$, so they'll have size $k$ by minimality. We then have $X = Z_0 \cup x_0$ and $Y = Z_0 \cup y_0$ (why?). Then the $k$-set $Z_0 \cup x_0$ links $X$ to $Y$ via the length zero paths with vertices in $Z_0$ along with the singular edge $x_0y_0$.
  ![[detach 1.png]]

- *Case 2: there is a detaching $k$-set that is neither $X$ nor $Y$.* Let $G_1$ be the subgraph of $G$ spanned by the vertices on strict $X$-$Z$ paths and let $G_2$ be the same for strict $Z$-$Y$ paths. In $G_1$ we need at least $k$ vertices to detach $X$ from $Z$. Since no vertex of $Y - Z$ belongs to $G_1$, this graph has fewer edges than $G$, so by the inductive hypothesis, there is a $k$-set $X_0\subseteq X$ that can be linked to $Z$ in $G_1$. Similarly we can link $Z$ to a $k$-set $Y_0 \subseteq Y$. Paste the paths from these links end to end to link $X_0$ and $Y_0$.
  
  ![[detach 2.png]]

## Linking Lemma

```ad-theorem
title: Linking Lemma

Let $|V(G)| \geq 2k$. Then $G$ is $k$-[[k-Connectivity#$k$-Connectivity|connected]] if and only if whenever $V_1$ and $V_2$ are disjoint $k$-sets of vertices, then $V_1$ is linked to $V_2$.
```

*Proof.* Say $G$ is $k$-connected. Then the minimum size of a set separating $V_1$ and $V_2$ is at least $k$. Since $V_1$ and $V_2$ are disjoint, separating sets are equivalent to detaching sets. By the above result, $V_1$ and $V_2$ are linked.

Conversely, say all disjoint $k$-sets are linked and $|V(G)| \geq 2k$. 