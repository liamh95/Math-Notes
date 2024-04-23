Date Created: 2024-04-09
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #proposition #estimates/polynomials

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-proposition
title: Homogeneous Polynomials Large At Same Point

Let $\mathcal P_k$ be the set of all homogeneous polynomials $f(p_1, \ldots, p_k)$ of degree $k$ with all coefficients having absolute value at most 1, and $p_1\cdots p_k$ has coefficient 1. Then for all $f\in \mathcal P_k$, there exist $p_1, \ldots, p_k \in [0,1]$ with
$$
|f(p_1, \ldots, p_k)| \geq c_k,
$$
where $c_k$ is some constant independent of $f$.

```

<i>Proof.</i> Set
$$
M(f) = \max_{p_1, \ldots, p_k\in [0,1]}|f(p_1, \ldots, p_k)|.
$$
Since $f$ is not the zero polynomial, $M(f) > 0$ for all $f$. Furthermore, $\mathcal P_k$ is a compact subset of the set of continuous functions on $[0,1]^k$ equipped with the sup-norm (as the image of $[-1,1]^{\binom{d+k-1}{d}-1}$ under a continuous function). $M$ is then a continuous function on a compact set, and so achieves its minimum value $c_k$. 