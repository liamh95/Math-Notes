Date Created: 2024-03-31
References: #ref/NONE
Tags: #theorem #graph-theory/flows #graph-theory/algorithms 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Min Cut Max Flow Theorem

In any flow network $(G, c, s, t)$, the maximum flow from $s$ to $t$ equals the minimum capacity of an $s$-$t$ cut.

```

<i>Proof.</i> For any integer flow, the [[Ford-Fulkerson Algorithm]] finds a flow whose value equals the capacity of a minimum cut. Since the value of any flow is at most the capacity of any cut, it must be a max flow.