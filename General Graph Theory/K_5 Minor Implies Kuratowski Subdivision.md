Date Created: 2024-07-08
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #proposition #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-proposition
title: K_5 Minor implies Kuratowski Subdivision

Any graph which has a $K_5$-[[Graph Minor|minor]] contains a $K_5$- or $K_{3,3}$-[[Subdivision|subdivision]].

```

<i>Proof.</i>  Say $G$ has a $K_5$-minor so that there is a partition $V(G) = V_0 \cup V_1 \cup \cdots \cup V_5$ so that we can delete the vertices from $V_0$ and shrink the (connected) $V_i$'s, $i \geq 1$, to points to get a $K_5$. For concreteness, let $V(K_5) = \{w_1, w_2, w_3, w_4, w_5\}$ and for each edge $w_iw_j\in E(K_5)$, there is an edge $e_{ij}$ in $E(G)$ between $V_i$ and $V_j$.

Following the proof of [[Maximum Degree 3 Implies Minor iff Subdivision]], for each edge $w_iw_j \in E(K_5)$, let $x_i^j$ be the vertex $e_{ij}\cap V_i$. If we can find vertices $u_i \in V_i$, $i\geq 1$, and internally vertex-disjoint paths $P_i^j$ connecting $u_i$ to each of the $x_i^j$'s, then we'll have made a $K_5$-subdivision.

We might not always be able to do this, so let's say that, without loss of generality, $V_1$ doesn't have the required internally vertex-disjoint paths. Note that in this case, the $x_1^i$'s are distinct, since otherwise we could find our internally vertex-disjoint paths. Let $Q$ be a shortest path in $V_1$ from $x_1^2$ to $x_1^3$ and let $Q'$ be a shortest path in $V_1$ from $x_1^4$ to a vertex on $Q$. Set $z_a$ to be the point where these paths meet. Let $Q''$ be the shortest path from $x_1^5$ to a vertex in $V(Q)\cup V(Q')$. Without loss of generality, $Q''$ hits $Q'$ in the point $z_b$. Now we have a couple of cases to consider depending on whether $z_a$ or $z_b$ coincides with one of the $x_1^i$'s.

- If $z_a$ and $z_b$ are both distinct from the $x_1^i$'s, then $x_1^2, x_1^3, z_a, z_b, x_1^4, x_1^5$ along with the paths $Q$, $Q'$, $Q''$ and the relevant subpaths form a subdivision of the tree with two vertices of degree 3 ($z_a$, $z_b$) and four leaves ($x_1^2, x_1^3, x_1^4, x_1^5$).
  
  Contract everything inside $V_1$ to this tree. Also contract $V_i$ and $x_1^i$, $i \geq 2$ to points called $Y_i$. Since we were working in a $K_5$-minor, there are edges between the $Y_i$'s as well (shown in yellow in the following diagram). Then $z_a, z_b$ along with the $Y_i$'s contain a $K_{3,3}$-subdivision.
  
  All of this shows that we have a $K_{3,3}$-minor. Since $K_{3,3}$ has maximum degree 3, [[Maximum Degree 3 Implies Minor iff Subdivision]] implies that we have a $K_{3,3}$-subdivision in $G$ as well.
  ![[kura1.png]]

- In the notation above, maybe $Q'$ hits $Q$ at (without loss of generality) $x_1^3$. Suppose $Q''$ hits (wlog) $Q'$ at a different point, $z$, though. Then if we contract $x^5$ and $V_5$ to get $Y_5$, $x^4$ and $V_4$ to get $Y_4$, $x^2$ and $V_2$ to get $Y_2$, but just contract $V_3$ to $Y_3$, then we still get a subdivision of $K_{3,3}$.
  ![[kura2.png]]

- Finally, say $Q'$ hits $Q$ at $x^3$ and $Q''$ hits $Q'$ at $x^4$. Then we do the same as above, except we don't contract $x^4$ into $V_4$.
  ![[kura3.png]]