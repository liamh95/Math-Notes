Date Created: 2024-03-04
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 2]]
Tags: #theorem #ramsey-theory/ramsey-numbers #probabilistic-method/first-moment-method 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Off-Diagonal Ramsey Numbers Random Lower Bound

$$
r(s,n) \geq c_s\left(\frac{n}{\log n}\right)^{(s-1)/2}.
$$

```

<i>Proof.</i> Set $N = c(\frac{n}{\log n})^{(s-1)/2}$. Two-color the edges of $K_N$ at random, choosing red with probability $p = 1/2N^{2/(s-1)}$. The expected number of red $K_s$'s is at most $N^s p^{\binom s2}$. and the expected number of blue $K_n$'s is at most $N^n (1-p)^{\binom n2}$. Adding these, we get an upper bound on the number of red $K_s$'s and blue $K_n$'s
$$
\begin{align}
N^sp^{\binom s2} + N^n(1-p)^{\binom n2} &\leq 2^{-\binom s2} + N^n e^{-p\binom n2}.
\end{align}
$$
Now since $s$ is a fixed constant, we can choose $c = c(s)$ such that $p = \frac{\log n}{2c n} \geq \frac{4s\log n}{n}$ , i.e. by choosing $c = \frac{1}{8s}$. In this case, the above expectation is at most
$$
2^{-\binom s2} + N^nn^{-2s(n-1)} \leq 2^{-\binom s2} + n^{-sn} < 1.
$$
In particular, there is some coloring of $K_N$ with no red $K_s$ and no blue $K_n$.

*Remark:* Spencer used the Local Lemma to get
$$
r(s,n) \geq c_s\left(\frac{n}{\log n}\right)^{(s+1)/2}.
$$
Kim improved this in the case where $s = 3$, giving the sharp (why?) bound of $r(3, n) \geq c\frac{n^2}{\log n}$. He used the "semi-random method". Erdős gave a more elementary proof of this.