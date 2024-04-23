Date Created: 2024-03-04 
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 1]]
Proved by: [[Goodman's Formula]]
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-corollary
title: Monochromatic Triangles in Two Coloring of K_n

Suppose that the edges of $K_n$ are 2-colored. Then the number of monochromatic triangles $\Delta$ satisfies

$$
\Delta \geq \frac{1}{4}\frac{n(n-1)(n-5)}{6} = \frac{1}{4}\binom{n}{3} + O(n^2).
$$

```

<i>Proof.</i> The expression $\binom{d}{2} + \binom{n-1-d}{2}$ is minimized when $d = (n-1)/2$. Plug this into [[Goodman's Formula]] and we obtain
$$
\begin{aligned}
	\Delta &\geq \frac{1}{2}\left( 2\sum_v \binom{(n-1)/2}{2} - \binom n3\right)\\
	& = \frac{1}{2}\left( \frac{2n(\frac{n-1}{2})(\frac{n-3}{2})}{2} - \frac{n(n-1)(n-2)}{6} \right)\\
	&= \frac{n(n-1)}{2}	\left(\frac{n-3}{4} - \frac{n-2}{6}\right)\\
	&= \frac{n(n-1)(n-5)}{24}.
\end{aligned}
$$
