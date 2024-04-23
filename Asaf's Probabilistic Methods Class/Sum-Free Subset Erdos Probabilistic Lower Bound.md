Date Created: 2024-04-09
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method #arithmetic-combinatorics

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

A subset $A$ of an abelian group $G$ is **sum-free** if $(A+A)\cap A = \emptyset$, i.e., there are no $a_1, a_2,a_3\in A$ for which $a_1+a_2 = a_3$.

```ad-theorem
title: Sum-Free Subset Erdos Probabilistic Lower Bound

Every set $B = \{b_1, \ldots, b_n\}$ of $n$ nonzero integers contains a sum-free subset $A$ of size $|A| > \frac{1}{3}n$.

```

<i>Proof.</i> Fix a prime $p$ of the form $p = 3k+2$ where $p > 2\max_i |b_i|$. Now let $C := \{k+1, \ldots, 2k+1\}$ be the "middle" third of $[p]$. Note that $C$ is a sum-free subset of $\mathbb Z / p\mathbb Z$ of size $k+1$ with $\frac{|C|}{p-1} > 1/3$. Now choose $x$ uniformly at random in $\mathbb Z/p\mathbb Z^{\times}$. Let $A$ be the set of all $b_i$ such that $xb_i \in C$ modulo $p$. Note that $A$ is sum-free as well since $C$ is sum-free and
$$
b_{i_1} + b_{i_2} \equiv b_{i_3}\pmod p \iff xb_{i_1} + xb_{i_2} \equiv xb_{i_3}\pmod p.
$$
We then have
$$
E[|A|] = n\cdot \Pr[b_1\in A] = n\cdot \frac{|C|}{p-1} > n/3.
$$
[[Probabilistic Method Basic Idea|Thus]], there is some subset $A\subseteq B$ of size greater than $n/3$.