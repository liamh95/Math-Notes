Date Created: 2024-07-07
References: [[Bondy, J and Murty, U - Graph Theory - 2008]]
Tags: #theorem #graph-theory/planar-graphs 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: K_5 is Nonplanar

$K_5$ is nonplanar.

```

<i>Proof.</i> Suppose there were some planar embedding of $K_5$ and let $V(K_5) = \{v_1, \ldots, v_5\}$. Consider the cycle $v_1v_2v_3$. Now the vertex $v_4$ either lives in the interior of this cycle or the exterior. Say $v_4$ is in the interior, so the edges $v_1v_4$, $v_2v_4$ and $v_3v_4$ all lie in the interior of cycle $v_1v_2v_3$ as well. Now look at the cycles $C_1 = v_2v_3v_4$, $C_2 = v_3v_1v_4$ and $C_3 = v_1v_2v_4$. These are defined so that $v_i$ is in the exterior of $C_i$.

Now consider $v_5$. Since $v_iv_5$ is an edge for $i = 1,2,3$ and each $v_i$ is in the exterior of $C_i$, we must have that $v_5$ is in the exterior of each $C_i$. It then follows that $v_5$ is in the exterior of $C$ as well. But then edge $v_4v_5$ crosses over at least one of the edges of $C$, a contradiction.


![[k5_nonplanar.png]]