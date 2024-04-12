Date Created: 2024-04-11
References: #ref/NONE
Tags: #theorem

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Binomial Theorem

For any nonnegative integer $n$ and any elements $x$ and $y$ of a commutative ring $R$,
$$
(x + y)^n = \sum_{j=0}^n\binom njx^jy^{n-j}.
$$

```

### Combinatorial proof
*Proof.* Expand the binomial on the left-hand side into a sum of $2^n$ products. Each product is of the form $x^jy^{n-j}$ for some $j$ between 0 and $n$. For any such $j$, each term equal to $x^jy^{n-j}$ comes from selecting $x$ a total of $j$ times and $y$ a total of $n-j$ times from the product $(x+y)\cdots (x+y)$. The number of ways to do this is equal to the number of ways to choose $j$ elements from a set of $n$ elements, $\binom nj$.

### Inductive proof
*Proof.* If $n=0$, then the result is immediate. Suppose then that the claim holds for $(x+y)^k$ for all $k$ up to some $n$. Then
$$
(x+y)^{n+1} = (x+y)(x+y)^n = (x+y)\cdot \sum_{j=0}^n\binom njx^jy^{n-j}.
$$
We can see that the powers of $x$ and $y$ here sum to $n+1$. Equating coefficients of the left- and right-hand sides, we see that
$$
[(x+y)^{n+1}]_{j, n+1-j} = [(x+y)^n]_{j-1, n-j+1} + [(x+y)^n]_{j, n-j} = \binom{n}{j-1} + \binom nj.
$$
Now by [[Binomial Coefficient Identities#Pascal's Identity|Pascal's identity]], this is equal to $\binom{n+1}{j}$ and the claim follows.