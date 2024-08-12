Date Created: 2024-07-20
References: [[Bollobas, Bela - Extremal Graph Theory- 1978]] - Chapter 1.3
Tags: #definition #in-progress 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Wheel

```ad-definition
title: Wheel Graph

A **wheel** consists of a chordless cycle $C$ called the **rim** and a vertex $v$ not in $C$ called the **center** where the center has at least three neighbors in the rim.

```



## Wheel (Bollobas)

```ad-definition
title: Wheel Graph (Bollobas)

For $n \geq 3$, the **wheel of $n$ spokes** is the graph $W_n$ consisting of the cycle $C_n$ and an additional vertex called the **center** connected to each vertex of the $C_n$. The edges incident to the center are the **spokes**.
```

Note that Bollobas *does* consider $K_4$ to be a wheel. This is jank because $W_3 = K_4$ doesn't have a unique center, but all other wheels do.

## Wheels are 3-connected

```ad-theorem
title: Wheels are 3-connected

Every wheel is [[k-Connectivity#$k$-Connectivity|3-connected]].
```

*Proof.* Deleting any two vertices on the rim still yields a connected graph. Similarly, deleting the center leaves a cycle, which is 2-connected.