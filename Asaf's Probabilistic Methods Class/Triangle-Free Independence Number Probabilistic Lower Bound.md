Date Created: 2024-04-11
References: #ref/NONE
Tags: #theorem #graph-theory/independence-number #graph-theory/triangle-free #probabilistic-method/first-moment-method 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Triangle-Free Independence Number Probabilistic Lower Bound

Let $G = (V,E)$ be a triangle-free graph on $n$ vertices with maximum degree at most $\Delta$. Then
$$
\alpha(G) \geq \frac{n\log \Delta}{8\Delta},
$$
where the logarithm is to the base 2.

```

<i>Proof.</i> If $\Delta$ is small, say less than 16, then the claim follows by the weaker bound $\alpha(G) \geq n/(\Delta+1)$, so we'll assume that $\Delta \geq 16$.

Let $W$ be an independent set of $G$, chosen uniformly at random. For each $v\in V$, define the random variable
$$
X_v := \Delta|\{v\}\cap W| + |N(v)\cap W|.
$$
Let $H:= G[V\setminus N[v]]$ (here $N[v] = N(v)\cup \{v\}$) and consider the conditional expectation $E[X_v \mid W\cap H = S]$, where $S$ is any independent set in $H$ (this intersection will be independent since $W$ is independent in $G$). Once we fix $W\cap H = S$, what are the possibilities for $W$? If $W$ contains $v$, then it cannot contain anything from $N(v)$ since $W$ is an independent set. On the other hand, if $W$ does not contain $v$, then it can contain any subset of $X:= N(v)\setminus N(S)$ since $N(v)$ is an independent set as $G$ is triangle-free. If we let $x:= |X|$, then there are $2^x + 1$ possibilities for $W$ after conditioning on $W\cap H = S$. Since $W$ was chosen uniformly from all independent sets in $G$, each of these possibilities is equally likely and it [[Binomial Coefficient Identities#Polynomially-weighted sum of binomial coefficients|follows]] that
$$
E[X_v \mid W\cap H = S] = \frac{\Delta}{2^x+1} + \frac{1}{2^x+1}\sum_{j=0}^xj\binom xj = \frac{\Delta + x2^{x-1}}{2^x+1}.
$$
If this quantity is less than $\frac{\log \Delta}{4}$, then it must be the case that $x \geq 1$ (otherwise we would have $\frac{\Delta}{2} < \frac{\log \Delta}{4}$, which is false for $\Delta \geq 16$). Consequently, we have
$$
2^x(\log \Delta - 2x) > 4\Delta - \log \Delta.
$$
Since the right-hand side is positive, we must have $\log \Delta > 2x \geq 2$, and
$$
4\Delta - \log \Delta < 2^x(\log \Delta -2x) \leq \sqrt\Delta(\log\Delta-2),
$$
which is false for all $\Delta \geq 16$. Thus, the above conditional expectation is at least $\frac{\log \Delta}{4}$. Summing over $v$ and using the law of total expectation gives
$$
E\left[\sum_v X_v\right] \geq \frac{n\log \Delta}{4}.
$$
The sum is always at most $2\Delta |W|$ since each vertex $u$ contributes $\Delta$ to the term $X_u$ and it also contributes 1 to $X_w$ for each of its at most $\Delta$ neighbors $w$. Consequently, the expected size of $W$ is at least $\frac{n\log \Delta}{8\Delta}$, so by the [[First Moment Method]], there is an independent set at least this large.