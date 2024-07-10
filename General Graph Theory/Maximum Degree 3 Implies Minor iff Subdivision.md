Date Created: 2024-07-08
References: #ref/NONE
Tags: #theorem #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Maximum Degree 3 Implies Minor iff Subdivision

Let $F$ be a graph with maximum degree at most three. Then $G$ contains an $F$-[[Graph Minor|-minor]] if and only if it contains an $F$-[[Subdivision|subdivision]].

```

<i>Proof.</i> Containing an $F$-subdivision automatically implies containing an $F$-minor: delete edges and vertices outside of the subdivision, then contract the subdivided edges. The reason this argument doesn't immediately reverse is because to show that we have an $F$-minor, we need to obtain $F$ from $G$ by vertex/edge deletions and edge contractions *but only contracting along edges where one of the ends has degree exactly two*. 

Say $G$ has an $F$-minor where $F$ has maximum degree at most three. There is then some sequence of deletions and contractions that creates $F$ from $G$. Let's look at a step where we contract $\{u,v\}$.

- If $u$ has degree one, then contracting this edge is essentially the same as just deleting $u$.
- If $u$ and $v$ both have degree 2, then contracting this edge is the same as just deleting one of these vertices.
- If $u$ and $v$ have a common neighbor $w$, contracting this edge can be replaced with the operation of first deleting, say, $uw$, and then contracting.
- If $u$ and $v$ both have degree at least 3 and no common neighbor, contracting this edge creates a vertex of degree at least 4. But $F$ has maximum degree at most 3 and this vertex' degree won't decrease with further contractions.

Putting this all together, we see that we can assume that all contractions are along edges, one of whose ends has degree exactly 2. This is exactly the process of producing a subdivision, so we conclude that there is an $F$-subdivision.

### Other proof

*Proof:* Say $G$ has an $F$-minor where $F$ has $k$ vertices. Then there is a partition $V(G) = V_0 \cup V_1 \cup \cdots V_k$ where we can delete $V_0$ and shrink the (connected) $V_i$'s to points, $i \geq 1$ to obtain $F$. In particular we can label $V(F) = \{w_1, \ldots, w_k\}$ so that for each edge $f_{ij} \in E(F)$, there are vertices $v_i \in V_i$ and $v_j\in V_j$ (not necessarily unique, but can be fixed) with $e_{ij}:= v_iv_j \in E(G)$. To find an $F$ subdivision, our plan is to find vertices $u_i \in V_i$,  $i\geq 1$, and for each edge $f_{ij}\in E(F)$ a path $P_{ij}$ in $G$ connecting $u_i$ to $u_j$ in such a way that $P_{ij}$ is internally vertex-disjoint from $P_{i'j'}$ for $ij \neq i'j'$. We'll construct these paths to be made of a path $P_i^j \subseteq V_i$ connecting $u_i$ to the vertex $e_{ij}\cap V_i$, followed by $e_{ij}$, followed by the path $P_j^i\subseteq V_j$ connecting vertex $e_{ij}\cap V_j$ to $u_j$. The $u_i$'s along with these paths will be the subdivision (not necessarily induced).

- Say $w_i \in V(F)$ has degree 1 and let $f_{ij} \in E(F)$ be the corresponding edge. In $G$ this corresponds to an edge $e_{ij}$. In this case, set $u_i = e_{ij} \cap V_i$ and $P_i^j = \emptyset$.

![[subdivision1.png]]
- If $w_i \in V(F)$ has degree 2, let $w_j, w_k \in V(F)$ be its neighbors. These correspond to edges $e_{ij}$ and $e_{ik}$ in $E(G)$. Let $x_j = e_{ij} \cap V_i$ and $x_k = e_{ik}\cap V_k$ (note that it could be the case that $x_j = x_k$). Set $u_i := x_j$, $P_i^j:= \emptyset$ and $P_i^k$ a shortest path in $V_i$ from $x_j$ to $x_k$. 

![[subdivision2.png]]

- If $w_i \in V(F)$ has degree 3, let $w_j, w_k, w_\ell$ be its neighbors. These give edges $e_{ij}, e_{ik}$ and $e_{i\ell}$ in $G$. Say these have endpoints $x_j$, $x_k$ and $x_\ell$, respectively, in $V_i$. Let $Q$ be a shortest path in $V_i$ connecting $x_j$ to $x_k$. Now let $Q'$ be a shortest path from $x_\ell$ to a vertex in $V(Q)$. Now set $u_i$ to be the unique vertex where $Q$ and $Q'$ meet. Set $P_i^j$ and $P_i^k$ to be the subpaths of $Q$ connecting $u_i$ to $x_j$ and $x_k$, respectively and set $P_i^\ell$ to be $Q'$.

![[subdivision3.png]]

In all three cases, we've constructed internally vertex-disjoint paths, and hence, an $F$-subdivision in $G$.

Why was it important that $F$ have maximum degree at most 3? If $F$ has a vertex of degree 4, then we can't guarantee that these paths we construct are internally vertex-disjoint. In the notation used above, if $w_i$ has neighbors $w_j$, $w_k$, $w_\ell$ and $w_m$, it could be the case that the corresponding vertices $x_j$, $x_k$, $x_\ell$ and $x_m$ are only joined by a (perhaps subdivided) path like so.![[subdivision4.png]]