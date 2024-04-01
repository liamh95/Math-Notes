Date Created: 2024-03-31
References: #ref/NONE
Tags: #theorem #graph-theory/flows #graph-theory/algorithms 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Integral Flow Theorem

Given a flow network $(G, c, s ,t)$ where all of the capacities are integers, there exists a maximum flow where the flow along every edge is an integer.

```

<i>Proof.</i> If the network has integral capacities, then the [[Ford-Fulkerson Algorithm]] always finds an integer-valued flow since it always pushes integer flows and creates integer-valued residual graphs. The resulting flow is always maximum.