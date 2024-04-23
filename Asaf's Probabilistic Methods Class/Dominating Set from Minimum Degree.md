Date Created: 2024-04-02
References: [[Alon, Noga and Spencer, Joel - The Probabilistic Method - 2015]]
Tags: #theorem #probabilistic-method/first-moment-method #graph-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Dominating Set from Minimum Degree

Let $G$ be a graph with minimum degree $\delta$. Then $G$ has a [[Dominating Set|dominating set]] of size at most
$$
n\cdot \frac{\ln(\delta+1)+1}{\delta+1}.
$$

```

<i>Proof.</i> Fix $p\in (0,1)$ to be determined later and let us randomly and independently pick each vertex with probability $p$ and place it into the set $X$. Let $Y_X$ be the set of vertices in $V\setminus X$ that have no neighbor in $X$ (i.e., $Y_X$ is the set of vertices that witness the failure of $X$ to be a dominating set). Now $X\cup Y_X$ is a dominating set and $|X\cup Y_X| = |X| + |Y_X|$.

It's clear that $E[X] = np$. If we write $Y_X = \sum_{v\in V}Y_v$, where $Y_v$ indicates $v\in Y_X$, then by the linearity of expectation, $E[Y_X] \leq n(1-p)^{\delta + 1} \leq ne^{-p(\delta+1)}$, since each $v$ fails to be in $X$ with probability $1-p$ and $v$ has at least $\delta$ neighbors (we have also used the [[Linear Bound for Exponential|bound]] $1+x\leq e^x$ for all real $x$). By the linearity of expectation,
$$
E[|X\cup Y_X|] = E[|X|] + E[|Y_X|] \leq np + ne^{-p(\delta+1)}.
$$
Since we want a small dominating set, we should choose $p$ to minimize this expression. Basic calculus tells us this happens when $p = \frac{\ln(\delta+1)}{\delta+1}$. Plugging this value of $p$ into the above expected value gives an expectation of at most $n\cdot \frac{\ln(\delta+1)+1}{\delta+1}$. Since the expected size of this dominating set is at most this value, the [[First Moment Method]] tells us that a dominating set of size at most this exists.