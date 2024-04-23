Date Created: 2024-04-16
References: [[Erdos, Paul and Spencer, Joel - Monochromatic Sumsets - 1989]]
Tags: #theorem #ramsey-theory #arithmetic-combinatorics #probabilistic-method/first-moment-method

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>
Improved by: 

For $A\subseteq \mathbb N$, let $S(A)$ denote the set of all sums $a_1 + \cdots + a_t$, where $t$ is arbitrary and the $a_i$ are distinct elements of $A$. Let $F(k)$ denote the smallest $n$ so that if $[n]$ is two-colored, then there is a $k$-element set $A$ with $S(A)\subseteq [n]$ and $S(A)$ is monochromatic. 

```ad-theorem
title: Folkman's Two Color Theorem Erdos Spencer Exponential Lower Bound

With $F(k)$ defined as above,
$$
F(k) > 2^{2k^2/\log k}.
$$

```

<i>Proof.</i> Write $A\subseteq [n]$ as $A = \{a_1 < \cdots < a_k\}$. We have that $|S(A)| \leq 2^k-1$, and this is witnessed by $\{1, 2, 2^2, \ldots, 2^{k-1}\}$. As for a lower bound, consider the following sums.
$$
\begin{align}
a_1 && && &&\\
a_1 + a_2 && a_2\\
a_1 + a_2 + a_3 && a_2+a_3 && a_1 + a_3\\
a_1 + a_2 + a_3 + a_4 && a_2+a_3+a_4 && a_1 + a_3 + a_4 && a_1+a_2 + a_4\\
\vdots
\end{align}
$$
These are all unique and have a canonical ordering (the first element of any row is less than the last element of the next row). We then have that $|S(A)| \geq \frac{1}{2}k(k+1)$.

Let's count the number of sets $A\subseteq [n]$ with $|S(A)| \leq u$. Whenever we add an element to $A$, the size of $|S(A)|$ at most doubles. With this in mind, call an index "doubling" if
$$
|S(\{a_1, \ldots, a_i\})| = 2|S(\{a_1, \ldots, a_{i-1}\})|.
$$
If $|S(A)| \leq u$, then there are at most $\log u$ many doubling indices. There are then at most $\binom{k}{\log u}$ ways to choose these indices and at most $\binom{n}{\log u}$ ways to choose the actual identities of these $a_i$'s. As for the elements in the non-doubling spots, if $a_i$ is not doubling, then $x+a_i = y$ for some $x,y\in S(\{a_1, \ldots, a_{i-1}\}) \subseteq S(A)$. There are then at most $u^2$ ways to choose such an $a_i$, for a total of at most $u^{2k}$ ways to choose all of the non-doubling elements. In total, there are then at most
$$
\binom{k}{\log u}\binom{n}{\log u}u^{2k} \leq (kn)^{\log u}u^{2k}
$$
subsets $A\subseteq [n]$ with $|S(A)| \leq u$.

Now just randomly two-color $[n]$. If we let $X$ be the number of $k$-sets $A\subseteq [n]$ with $S(A)\subseteq [n]$ and $S(A)$ monochrome, then
$$
E[X] = \sum_{|A| = k,\ S(A)\subseteq [n]}2^{1-|S(A)|} \leq \sum_{u\geq \frac{1}{2}k(k+1)}2^{1-u}(kn)^{\log u}u^{2k}.
$$
Now This last sum can be rewritten as $2\sum_{u\geq M} u^p 2^{-u}$, where $p = 2k + \log(kn)$. If we choose $n = \lfloor 2^{ck^2/\log k}\rfloor$, then bounding this sum by the appropriate integral and doing some calculus, we see that this sum is $o(1)$. By the [[First Moment Method]], there is then a monochromatic $S(A)$ for this value of $n$, and therefore, $F(k) > n$.