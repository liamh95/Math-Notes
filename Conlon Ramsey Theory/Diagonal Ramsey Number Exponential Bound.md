Date Created: 2024-03-01
References: #ref/NONE
Tags: #theorem #ramsey-theory/ramsey-numbers #technique/pigeonhole-principle

Proved by: <i>Not Applicable</i>
References: Conlon's Ramsey theory notes - Lecture 1
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Diagonal Ramsey Number Exponential Bound

$$
	r(t) \leq 2^{2t-3}.
$$

```

<i>Proof.</i> Suppose we have colored the edges of $K_n$, $n = 2^{2t-3}$, with red and blue. Initiate an empty string $S$. For an arbitrarily chosen vertex $v$, one of the colors must have at least $2^{2t-4}$ edges incident to $v$. If these edges are red, append an '$R$' to $S$. Otherwise, append a '$B$'. In either case, let $V_1$ be the vertices incident to these edges (not including $v$).

Repeat this process on $V_1$. At step $i$, the set $V_{i-1}$ has $2^{2t-3-i}$ vertices in it. Pick $v_i$ arbitrarily from $V_{i-1}$. Either its red or its blue neighborhood in $V_{i-1}$ has size at least $2^{2t-3-(i+1)}$. Let $V_i$ be this neighborhood and append the appropriate character to $S$.

Let's look at step $2t-3$. At each step, we preserve at least half of the vertices, so $|V_{2t-3}| \geq 1$. Pick $v_{2t-2}$ arbitrarily from here. At least $t-1$ of the characters in $S$ are either $R$ or $B$ (wlog they're $R$). Let $s_{j_1}, \ldots, s_{j_{t-1}}$ be indices that correspond to these $R$'s. Let's look at $\{v_{j_1}, \ldots, v_{j_{t-1}}, v_{2t-2}\}$. By construction, each $v_{j_i}$ is connected to each future vertex by a red edge, so we have a monochromatic red $K_t$. 