Date Created: 2024-09-19
References: [[Misra, Jayadev and Gries, David - A constructive proof of Vizing's theorem - 1992]]
Tags: #theorem #graph-theory/coloring #graph-theory/algorithms  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Result and runtime

```ad-theorem
title: Misra and Gries Edge Coloring Algorithm

Let $G$ be a graph with $n$ vertices and $m$ edges with maximum degree $\Delta$. Then there is an algorithm that properly colors the edges of $G$ using at most $\Delta+1$ colors in $O(mn)$ steps (in the RAM model of computation where $G$ is stored as an adjacency list).

```

By [[Vizing's Theorem#Vizing's Theorem|Vizing's theorem]], this is the best we can hope for in terms of number of colors.
## Vizing Fans

```ad-definition
title: Vizing fan

A **Vizing fan** at the vertex $x$ is a sequence of vertices $F[1:k]$ that satisfies the following
- $F[1:k]$ is a nonempty sequence of distinct neighbors of $x$;
- the edge $xF[1]$ is uncolored
- the color of $xF[i+1]$ is free at $F[i]$ for each $1\leq i < k$.

The act of **rotating $F[1:k]** consists of reassigning $xF[i]$ the color of $xF[i+1]$ for each $1\leq i < k$ and uncoloring $xF[k]$. This results in a valid (partial) coloring by the third property of Vizing fans.
```

The following procedure builds a maximal fan in the sense that it can't be extended to a larger one.

```ad-algorithm
title: Build maximal fan

**Input: ** A proper partial coloring $c$ of the graph $G$ and an uncolored edge $xv$.
**Output:** A maximal fan $F[1:k]$ at $x$.

1. $F[1] \gets v$
2. $i \gets 1$
3. `while` there is a vertex $u\in N(x)$ such that $c(xu)$ is missing at $F[i]$
	1. $F[i+1] \gets u$
	2. $i \gets i+1$
4. `return` $F[1:i]$
```

This algorithm finishes in $O(\Delta)$ steps (what are the implementation details? Naively it seems like it should be $O(\Delta^2)$?)
## Algorithm

```ad-algorithm
**Input: ** a graph $G$.
**Output: ** a proper coloring $c$ of the edges of $G$.

1. Let $U = E(G)$
2. `while` $U$ is nonempty
	1. Let $xv$ be any edge in $U$
	2. Let $F[1:k]$ be a maximal fan at $x$ with $F[1] = v$ (see subroutine above)
	3. Let $\alpha$ and $\beta$ be colors missing at $x$ and $F[k]$ respectively
	4. Toggle the maximal path through $x$ whose colors are $\alpha$ and $\beta$
	5. Let $\ell \in [k]$ be such that $F' = F[1:\ell]$ is a Vizing fan and and $\beta$ is free at $F[\ell]$
	6. Rotate $F'$
	7. Color $xF[\ell]$ with $\beta$
	8. $U\gets U\setminus \{xv\}$
```

### Correctness

This isn't too different from the proof of [[Vizing's Theorem#Vizing's Theorem|Vizing's theorem]].  The first thing we need to show is that when we toggle the $\alpha/\beta$ path in step 2.1, we obtain a fan $F'$ with $\beta$ available at $F[\ell]$. Before we toggle, there are two cases.
- The fan $F$ has no edge colored $\beta$. By maximality, if $\beta$ is free at $F[k]$, it must also be free at $x$ (otherwise we could set the endpoint of the $\beta$-colored edge to $F[k+1]$). So $\alpha$ and $\beta$ are both missing at $x$ and there is no $\alpha/\beta$ path through $x$ to begin with. We can then just set $\ell = k$ in step 2.5 above.
- The fan $F$ does have an edge colored $\beta$, say $xF[i+1]$ with $i<k$. By the definition of a fan, $\beta$ must be free at $F[i]$. Before we toggle, $\alpha$ is free at $x$ and $xF[i+1]$ has color $\beta$, and no other edges in the fan have color $\alpha$ or $\beta$. Toggling only affects edges colored $\alpha$ or $\beta$, so after we invert, we have that for all $j \in [k]\setminus i$, the color of $xF[j+1]$ is missing at $F[j]$. There are two cases to consider
	- $F[i]$ is not on the $\alpha/\beta$ path through $x$. Toggling won't affect the colors free at $F[i]$ and $\beta$ will still be missing here and $F' = F[1:i]$ is a valid fan.
	- $F[i]$ is on the $\alpha/\beta$ path through $x$. Before we toggled, $\beta$ was free at $F[i]$ and since it's on the $\alpha/\beta$ path through $x$, it must be an endpoint of the path and $\alpha$ will be free here after we toggle. Toggling changes the color of $xF[i+1]$ to $\alpha$ and $F$ remains a fan and $\beta$ remains missing at $F[k]$ since we didn't touch anything here (the only way it could have been on the $\alpha/\beta$ path through $x$ is if is an endpoint with an $\alpha$ edge. But $x$ and $F[i]$ are the endpoints).
Now that we know the algorithm is well-defined, we show that it produces a valid coloring. We can just induct on the number of colored edges. It's vacuously okay when there are none. If the partial coloring so far is valid, in the current step, after toggling in step 2.4, the color $\beta$ is free at $x$, and by the above reasoning, also free at $F[\ell]$. Rotating $F'$ doesn't invalidate the partial coloring by definition of a Vizing fan, so when we color $xF[\ell]$ with $\beta$, we still get a valid coloring.

This can indeed work with $\Delta+1$ colors. We can find the color $\beta$ missing at $F[k]$ since it has at most $\Delta$ neighbors, so there's always a color missing. This leaves $\Delta$ colors for $\alpha$. There is at least one uncolored edge incident to $x$, so it has at most $\Delta-1$ colored neighbors, so we can find a missing $\alpha$.

### Runtime

We color the edges one at a time, so the main loop executes $m$ times. Computing a maximal fan at $x$ takes $O(\Delta)$ steps (why?) and finding the missing colors $\alpha$ and $\beta$ takes $O(\Delta)$ steps. Finding and toggling the $\alpha/\beta$-path through $x$ takes $O(n)$ steps. Finding the vertex $F[\ell]$ and then rotating $F'$ takes $O(\Delta)$ steps. In total, we have
$$
O\big(m(\Delta +\Delta + n + \Delta) \big) = O(mn)
$$
steps.