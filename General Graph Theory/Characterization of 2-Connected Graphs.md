Date Created: 2024-08-06
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1
Tags: #theorem #graph-theory #in-progress 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Vertex Connected

```ad-theorem
title: Characterization of 2-Vertex Connected Graphs

Let $G$ be a graph with at least 3 vertices. Then the following are equivalent

- (i) $G$ is [[k-Connectivity#$k$-Connectivity|2-vertex connected]]
- (ii) $G$ has no [[Cut Vertex and Bridge#Cut Vertex|cut vertex]]
- (iii) Given any two vertices, there is a cycle containing them
- (iv) Given any vertex and any edge, there is a cycle containing them
- (v) Given any two edges, there is a cycle containing them

```

<i>Proof.</i>
- (i) $\iff$ (ii): Say $G$ is 2-vertex connected. Then by [[Menger's Theorem#Menger's Theorem|Menger's theorem]], there are two internally vertex disjoint paths between any two vertices. Consequently, if we remove any one vertex, there will still be at least one path between any two vertices, so there are no cut vertices.
  
  Now say $G$ has no cut vertex. This means we have to delete at least two vertices to separate any pair of vertices $x,y$. This means that the [[k-Connectivity#Local Vertex Connectivity (Bollobás)|local vertex connectivity]], $\kappa(x,y)$ is at least 2 for all $x$ and $y$. This is exactly what it means to be 2-connected.

- (i) $\iff$ (iii): Say $G$ is 2-vertex connected. By Menger's theorem there are two internally vertex disjoint paths between any two vertices. Take two of the internally vertex disjoint paths between $x$ and $y$. Stick them together to get a cycle through $x$ and $y$.
  
  Say any two vertices have a cycle containing them. For vertices $x$ and $y$, let $C$ be a cycle through them. Traverse the cycle one way from $x$ to $y$ to get a path. Continue along the cycle in the same direction from $y$ to $x$ to get a path that is internally vertex disjoint from the previous one. This gives you two internally vertex disjoint $xy$-paths. This can be done for any two vertices, so by Menger's theorem, $G$ is 2-connected.

- (i) $\iff$ (iv): Say $G$ is 2-vertex connected and let $u$ and $e = vw$ be a vertex and an edge in $G$, respectively. If $u$ is in $e$, then this just reduces to (iii). Otherwise, by the [[Fan Lemma#Fan Lemma|fan lemma]], there is a 2-fan from $u$ to $\{v,w\}$. The $uv$- and $uw$-paths in this fan are internally vertex disjoint, so when we add the edge $vw$, we get a cycle containing $u$ and $e$.
  
  Conversely, if, for every vertex $u$ and edge $e = vw$ there is a cycle containing them, then this cycle gives a 2-fan from $u$ to $\{v,w\}$. Since the ability to always create a 2-fan is equivalent to 2-connectivity by the fan lemma, $G$ is 2-connected.

- (i) $\iff$ (v): Say $G$ is 2-vertex connected and let $e = uv$ and $f = xy$ be two edges. If these edges are the same, then this reduces to (iii). If $e$ and $f$ have exactly one vertex in common, say $e = uv$ and $f = uy$, then by Menger's theorem, there must be a $vy$-path that is internally vertex disjoint from the path $vuy$. Gluing this path to $vuy$ gives a cycle. 


## Edge Connected

```ad-theorem
title: Characterization of 2-edge connected graphs

- (i) $G$ is 2-edge connected
- (ii) $G$ has no isolated vertices or bridges
- (iii) $G$ is connected, has no isolated vertices and every edge is contained in a cycle
- (iv) Given any two edges there is a circuit containing them
- (v) Given any vertex and any edge, there is a circuit containing them
- (vi) Given any two vertices, there is a circuit containing them
```