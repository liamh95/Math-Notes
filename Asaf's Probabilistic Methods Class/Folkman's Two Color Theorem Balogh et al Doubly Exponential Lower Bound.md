Date Created: 2024-04-19
References: [[Balogh, Jozsef et al - An improved lower bound for Folkman's Theorem]]
Tags: #theorem #ramsey-theory #arithmetic-combinatorics #probabilistic-method/first-moment-method

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

For $A\subseteq \mathbb N$, let $S(A)$ denote the set of all sums $a_1 + \cdots + a_t$, where $t$ is arbitrary and the $a_i$ are distinct elements of $A$. Let $F(k)$ denote the smallest $n$ so that if $[n]$ is two-colored, then there is a $k$-element set $A$ with $S(A)\subseteq [n]$ and $S(A)$ is monochromatic.

Erdos and Spencer [[Erdos, Paul and Spencer, Joel - Monochromatic Sumsets - 1989|showed]] that $F(k) > 2^{kn^2/\log k}$ for some small $c$. These authors have a simple argument that gives a huge improvement.

```ad-theorem
title: Folkman's Two Color Theorem Balogh et al Doubly Exponential Lower Bound

With $F(k)$ as defined above,
$$
F(k) > 2^{2^{k-1}/k}.
$$

```

<i>Proof.</i> We're going to choose our random coloring a bit more cleverly. Randomly two-color the *odd* elements of $[n]$ uniformly. Extend this to a two-coloring of $[n]$ by insisting that the color of $2x$ is different from the color of $x$.
$$
\begin{align}
\textcolor{red}{1} && \textcolor{blue}{2} && \textcolor{red}{4} && \textcolor{blue}{8} && \cdots \\
\textcolor{red}{3} && \textcolor{blue}{6} && \textcolor{red}{12} && \textcolor{blue}{24}\\
\textcolor{blue}{5} && \textcolor{red}{10} && \textcolor{blue}{20} && \textcolor{red}{40}\\
\textcolor{red}{7} && \textcolor{blue}{14} && \textcolor{red}{28} && \textcolor{blue}{56}\\
\vdots
\end{align}
$$
Now fix $A\subseteq [n]$ with $|A| = k$. If $A$ doesn't have distinct sums, i.e., $|S(A)| \leq 2^k-2$, then there are $B_1, B_2\subseteq A$ with $\sum_{x\in B_1}x = \sum_{x\in B_2}x$. By getting rid of the intersections, we can assume that $B_1$ and $B_2$ are disjoint. But then
$$
\sum_{x\in B_1 \cup B_2} x = \sum_{x\in B_1}x + \sum_{x\in B_2}x = 2\sum_{x\in B_1}x.
$$
That is, $S(A)$ contains an element and its double. By the construction of our coloring, $S(A)$ is not monochromatic. We can then assume that $S(A)$ has distinct sums, i.e. $|S(A)| = 2^k-1$. Consider the progressions $G_m = \{m, 2m, 4m, \ldots, \}$, where $m$ is odd. These progressions clearly partition $\mathbb N$.

We claim that $S(A)$ intersects at least $2^{k-1}$ of these progressions. If $A$ contains some odd integer $r$, then there are $2^{k-1}$ distinct odd elements in $S(A)$, and these integers live in distinct progressions $G_m$. If $S(A)$ contains no odd elements, there is some maximal power of 2, say $2^s$, that divides each element of $A$. There is some element $2^st$ for $t$ odd in $A$. There are then $2^{k-1}$ elements of $S(A)$ divisible by $2^s$, but not $2^{s+1}$, and these must all lie in different progressions $G_m$.

Now take $B_A\subseteq S(A)$ to be maximal with respect to the property that $|B_A\cap G_m| \leq 1$ for each $m$, e.g. $B_A$ could be the least elements from $S(A)$ in $G_m$ if they exist. Then our coloring is uniformly random when restricted to $B_A$ since the colors of each element in $G_m$ are determined by the color of $m$. Then the probability that $B_A$ is monochromatic is $2^{1-|B_A|} \leq 2^{2^{k-1}}$, and this upper bounds the probability that $S(A)$ is monochromatic. So if we let $X$ be the number of $k$-sets $A\subseteq [n]$ with $S(A)\subseteq [n]$ monochromatic, we have
$$
E[X] \leq \binom nk2^{1-2^{k-1}} \leq \left( \frac{ne}{k} \right)^k2^{1-2^{k-1}}.
$$
So if we set $n = \lfloor 2^{2^{k-1}/k}\rfloor$, this is at most $2(e/k)^k$, which is less than 1 when $k \geq 4$ (and the theorem is clearly-ish true when $k \leq 3$). By the [[First Moment Method]], for such $n$, there is an $S(A)$ that is not monochromatic, so $F(k) > n$.