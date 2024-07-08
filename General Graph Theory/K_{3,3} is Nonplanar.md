Date Created: 2024-07-07
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #theorem #graph-theory/planar-graphs  

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: K_{3,3} is Nonplanar

$K_{3,3}$ is nonplanar.

```

<i>Proof.</i> Say there is some planar embedding. $K_{3,3}$ is bipartite, so let the parts be $\{a_1, a_2, a_3\}$ and $\{b_1,  b_2, b_3\}$. Take any five vertices. Without loss of generality, they're $a_1, a_2, a_3, b_1, b_2$. First draw the edges from $b_1$ to $a_1$, $a_2$ and $a_3$ to get something like this.


![[449175459_1200704657609914_6221967150434573349_n.png]]

Now add in $b_2$ and its edges to $a_1$, $a_2$ and $a_3$. We can always rearrange things so the picture we get looks like this.

![[449096299_1017998519921924_6417903340899934547_n.png]]

Vertex $b_3$ has to go in either the exterior of $b_1a_1b_2a_3$ or one of the two interior quadrilaterals. In any case, we can't draw an edge to one of the $a_i$'s.


It's interesting to note, however, that every proper subgraph of $K_{3,3}$ is planar. This can be verified by direct enumeration (there are only like five nontrivial subgraphs).

