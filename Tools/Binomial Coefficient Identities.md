Date Created: 2024-04-11
References: #ref/NONE
Tags: #proposition #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Pascal's identity

```ad-proposition
title: Pascal's Identity

For any nonnegative integers $n$ and $k$,
$$
\binom nk + \binom{n}{k-1} = \binom{n+1}{k}.
$$
```
### Combinatorial proof
*Proof.* The right-hand side is the number of ways to choose a $k$-element set from a set of $n+1$ elements. Let $x$ be one of these $n+1$ elements. Then there are $\binom{n}{k}$ sets of size $k$ that *do not* contain $x$ and $\binom{n}{k-1}$ sets of size $k$ that *do* contain $x$. The result follows since these are the only ways to build a $k$-element set.

### Algebraic proof
*Proof.*


## Sum of binomial coefficients

```ad-proposition
title: Sum of binomial coefficients

For any nonnegative integer $n$,
$$
\binom{n}{0} + \binom n1 + \cdots + \binom nn = 2^n.
$$
```

### Combinatorial proof

*Proof.* The right-hand side is just the number of subsets of $[n]$. For any $0\leq j \leq n$, there are exactly $\binom nj$ subsets of $[n]$ of size $j$ (by definition). The left-hand side is just the number of subsets of $[n]$, grouped by the size of the subset.

### Inductive proof

### Algebraic proof

*Proof.* By the [[Binomial Theorem]], $(1+x)^n = \sum_{j=0}^n \binom nj x^j$. Just plug in $x=1$.



## Polynomially-weighted sum of binomial coefficients

```ad-proposition
title: Polynomially-weighted sum of binomial coefficients

For any nonnegative integer $n$,
$$
\begin{align}
\sum_{j=0}^nj\binom nj &= n2^{n-1}\\
\sum_{j=0}^nj^2\binom nj &= (n+n^2)2^{n-2}.
\end{align}
$$

```

### 