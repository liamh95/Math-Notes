Date Created: 2024-03-02
References: #ref/NONE
Tags: #theorem #graph-theory

Proved by: <i>Not Applicable</i>
References: Conlon Ramsey theory notes: Lecture 1
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Goodman's Formula

Suppose that the edges of $K_n$ are 2-colored in red and blue. Let $G$ be the red graph. Then the number of monochromatic triangles, $\Delta$, is given by the formula

$$
\Delta = \frac{1}{2}\left( \sum_v \binom{d_G(v)}{2} + \sum_v \binom{d_{\overline{G}}(v)}{2} - \binom n3  \right).
$$

```

<i>Proof.</i>  A red triangle contributes 3 to the first sum, 0 to the second, and 1 to $\binom{n}{3}$. Therefore, each red triangle contributes 1 to the whole sum. Similarly, a blue triangle contributes 1. A triangle with two red edges and one blue edge contributes 1 to the first, and 0 to the second, so 0 contribution in total. The same holds for two blue edges and one red edge.