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

*Proof:* Say $G$ has an $F$-minor where $F$ has $k$ vertices. Then there is a partition $V(G) = V_0 \cup V_1 \cup \cdots V_k$ where we can delete $V_0$ and shrink the $V_i$'s to points, $i \geq 1$ to obtain $F$. In particular we can label $V(F) = \{w_1, \ldots, w_k\}$ so that for each edge $w_iw_j \in E(F)$, there are vertices $v_i \in V_i$ and $v_j\in V_J$ with $v_iv_j \in E(G)$. To find an $F$ subdivision, our plan is to find vertices $u_i \in V_i$ and for each edge $w_iw_j\in E(F)$ a path $P_{ij}$ in $G$ connecting $u_i$ to $u_j$ in such a way that $P_{ij}$ is internally vertex-disjoint from $P_{i'j'}$ for $ij \neq i'j'$. The $u_i$'s along with these paths will be the subdivision (not necessarily induced).

