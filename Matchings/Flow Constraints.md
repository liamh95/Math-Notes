Date Created: 2024-03-30
References: #ref/NONE
Tags: #definition #graph-theory

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

```ad-definition
title: Flow Network

A **flow network** consists of a directed graph $G = (V,E)$ with no loops or repeated arcs, a single **source** $s\in V$ (i.e., $s$ has only out-edges), a single **sink** $t\in V$ (i.e., $t$ has only in-edges) and a **capacity function** $c$ from $E$ to the nonnegative real numbers.

```

```ad-definition
title: Flow Constraints

A **flow** $f$ on a flow network $(G, c, s, t)$ is **feasible** if it satisfies the following flow constraints.

1. Capacity constraint: For any edge $e$, $0 \leq f(e) \leq c(e)$.
2. Flow conservation: For any vertex $v\notin \{s, t\}$, the flow into $v$ equals the flow out of $v$, i.e. $\sum_{u\in V} f(u,v) = \sum_{u\in V}f(v,u)$.

The **value** of the flow $f$ is the amount of flow eminating from $s$ (equal to the amount of flow entering $t$):
$$
|f| = \sum_{u\in V}f(s, u) = \sum_{u\in V}f(u, t).
$$

```