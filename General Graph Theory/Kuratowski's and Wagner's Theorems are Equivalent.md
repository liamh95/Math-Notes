Date Created: 2024-07-08
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #theorem #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Kuratowski's and Wagner's Theorems are Equivalent

[[Kuratowski's Theorem]] and [[Wagner's Theorem]] are equivalent.

```

<i>Proof.</i> First note that any graph that contains an $F$-subdivision also has an $F$-minor: delete the vertices and edges not in the subdivision, then contract each subdivided edge into a single edge. Hence, Kuratowski implies Wagner.

Since $K_{3,3}$ has maximum degree 3, any graph with a $K_{3,3}$-minor also has a $K_{3,3}$-subdivision by [[Maximum Degree 3 Implies Minor iff Subdivision]]. We [[K_5 Minor Implies Kuratowski Subdivision|also]] have that any graph with a $K_5$-minor contains either a $K_5$-subdivision or $K_{3,3}$-subdivision, so Wagner's theorem implies Kuratowski's theorem. 

