Date Created: 2024-04-02
References: #ref/NONE
Tags: #theorem #probabilistic-method #graph-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Property B Erdos Probabilistic Lower Bound

Every $n$-uniform hypergraph with less than $2^{n-1}$ edges has [[Property B]]. Therefore, $m(n) \geq 2^{n-1}$.

```

<i>Proof.</i> Let $H = (V,E)$ be a hypergraph with fewer than $2^{n-1}$ edges. Randomly color each vertex of $H$ red or blue (with equal probability, each vertex independently). Each edge is monochromatic with probability $2^{1-n}$ since there are two colors to choose from and each edge has exactly $n$ vertices. Union bounding over the fewer than $2^{n-1}$ edges shows that there is a monochromatic edge with probability strictly less than 1. [[Probabilistic Method Basic Idea|Consequently]], there is a two-coloring with no monochromatic edge and $H$ has property B.