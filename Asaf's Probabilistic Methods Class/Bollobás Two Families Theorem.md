Date Created: 2024-04-08
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #combinatorial-set-theory #probabilistic-method 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Bollobás Two Families Theorem

Say $\mathcal F = \{(A_i, B_i)\}_{i=1}^t$ is a collection of pairs of sets where
- $A_i\cap B_i = \emptyset$,
- $A_i \cap B_j \neq \emptyset$ for $i\neq j$.

Then if $|A_i|=a_i$ and $|B_i| = b_i$, then
$$
\sum_{i=1}^t\binom{a_i+b_i}{a_i}^{-1} \leq 1.
$$
In particular, if $a_i = k$ and $b_i = \ell$ for all $i$, then $t\leq \binom{k+\ell}{k}$.

```

<i>Proof.</i> Let $X = \cup_{i=1}^t (A_i\cup B_i)$ be the union of all of these sets and let $\pi\in [|X|]\to X$ be a permutation of $X$ chosen uniformly at random. For each $i$, let $E_i$ be the event that all of the elements of $A_i$ precede all of the elements of $B_i$ under $\pi$. Notice that since $A_i \cap B_j \neq \emptyset$ for $i\neq j$, the events $E_i$ and $E_j$ are disjoint. Hence,
$$
\Pr[\cup_i E_i] = \sum_i \Pr[E_i] \leq 1.
$$
We also have that 
$$
\Pr[E_i] = \frac{a_i!b_i!}{(a_i+b_i)!}= \binom{a_i+b_i}{a_i}^{-1},
$$
and the claim follows.