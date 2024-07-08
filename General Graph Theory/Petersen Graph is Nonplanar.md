Date Created: 2024-07-07
References: #ref/NONE
Tags: #theorem #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Petersen Graph is Nonplanar

The Petersen graph is nonplanar.

```

<i>Proof.</i> Let's label the vertices of the Petersen graph like so.

![[449412638_507928268465215_5230786979578679201_n.png]]

A subdivision of $K_{3,3}$ is going to have six vertices of degree 3 and the rest will have degree 2. Our plan is to just try deleting vertices of the Petersen graph until we get this property, after which point we'll just check to see if what we get is indeed a $K_{3,3}$.

If we delete vertex 5 for instance, we can easily see that we have six vertices of degree 3 and three of degree 2, so there's hope. If we just rearrange the vertices, we see that we get the following subdivision of $K_{3,3}$.

![[449338864_403126846085555_6091283846882584301_n.png]]

The subgraph on these vertices is then nonplanar since [[K_{3,3} is Nonplanar|K_{3,3} is nonplanar]] and a [[Planar if and only if Every Subdivision Planar|graph is planar if and only if any subdivision of it is planar]]. Since this subgraph is nonplanar, we conclude that the whole Petersen graph is nonplanar.