Date Created: 2024-03-01
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 1]]
Tags: #theorem #ramsey-theory/ramsey-numbers 

Proved by: <i>Not Applicable</i>
References: Conlon Ramsey theory notes: Lecture 1
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Ramsey Number Binomial Coefficient Bound

$$
r(s+1, t+1) \leq \binom{s+t}{t}.
$$

```

<i>Proof.</i> Suppose we red-blue color the edges of $K_n$ in such a way that we have no red $K_s$ and no blue $K_t$. For any vertex $v$, its red neighborhood must be of size at most $r(s, t+1)-1$. Otherwise, we would have a red $K_s$ or blue $K_{t+1}$. Adding $v$ to the red $K_s$ would give us a red $K_{s+1}$. For the same reason, the blue neighborhood is of size at most $r(s+1, t) - 1$. Consequently,
$$
r(s+1, t+1) \leq 1 + (r(s+1, t)-1) + (r(s, t+1)-1) = r(s+1, t) + r(s, t+1).
$$
We proceed by induction. Note that $r(2, t+1) = t+1 = \binom{t+1}{1}$ and $r(s+1, 2) = s+1 = \binom{s+1}{1}$. Suppose then that $r(i+1, j+1) \leq \binom{i+j}{i}$ for all $i,j$ with $i<s$ or $j<t$. Then by the above inequality, we have
$$
r(s+1, t+1) \leq r(s, t+1) + r(s+1, t) \leq \binom{s+t-1}{s-1} + \binom{s+t-1}{s} = \binom{s+t}{s}.
$$