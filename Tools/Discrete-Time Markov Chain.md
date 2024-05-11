Date Created: 2024-04-29
References: [[Durrett, Rick - Probability Theory - 2019]], [Wikipedia](https://en.wikipedia.org/wiki/Discrete-time_Markov_chain) [[Mitzenmacher, Michael and Upfal, Eli - Probability and Computing - 2017]]
Tags: #definition #probability/markov-chains #in-progress

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Markov Chains

```ad-definition
title: Discrete-Time Markov Chain

Let $X$ be a countable set (the *state space*). Then a stochastic process $X_1, X_2, \ldots$ is a **Markov chain** if it has the **Markov property**:
$$
\Pr[X_{n+1} = j\mid X_n = i_n,\ X_{n-1} = i_{n-1}, \ldots, X_0 = i_0] = \Pr[X_{n+1} = j\mid X_n = i_n].
$$
In other words, given the present state, predicting the next state is independent of the distant past.

We define $p_{ij} = \Pr[X_{n+1} = i\mid X_n = j]$ the **transition probability** and the matrix $P$ with entry $ij$ equal to $p_{ij}$ the **transition matrix**.

```

```ad-definition
title: Markov Chain Graph Representation

We can think of a Markov chain as being a sequence of directed weighted graphs $D_n = (V, E, w)$, where the vertex set is the state space, $V = X$, and we have an arc $ij\in E$ if and only if $p_{ij} > 0$, and the weight $w(i,j) = p_{ij}$. 
```

```ad-definition
title: Distribution Vector

If we have a countable state space $X$, then a vector $p \in \mathbb{R}^X$ is a distribution vector (or state vector) if $\sum_{x\in X}p_x = 1$. We think of $p$ as encoding the probability that we're in any state in $X$.

Let $p_i(t)$ denote the probability that the Markov chain is in state $i$ at time $t$ and let $p(t)$ be the vector of these probabilities. Then
$$
p(t) = p(t-1)P.
$$
```
## Irreducible Markov Chains

```ad-definition
title: Irreducible Markov Chain

We say that a Markov chain is **irreducible** if every state in $X$ is eventually reachable from any other state in $X$. More formally, we require that for any states $i$ and $j$, there is an integer $n_{ij} \geq 0$ such that
$$
\Pr[X_{n_{ij}} = j\mid X_0 = i] = p^{(n_{ij})}_{ij} > 0.
$$
```

Immediate from the definition, we have that a Markov chain is irreducible if and only if its graph representation is strongly connected.
## Aperiodic Markov Chains

```ad-definition
title: Aperiodic Markov Chain

State $i\in X$ has **period** $k$ if, beginning in state $i$, any return back to $i$ must be after a number of steps that is a multiple of $k$. Formally,
$$
k = \gcd\{n> 0: \Pr[X_n = i\mid X_0 = i] > 0\}.
$$

We say that a Markov chain is **aperiodic** if all periods are 1. We also say that an irreducible chain is **ergodic** if it is also aperiodic.
```

It's not hard to show that a Markov chain is ergodic if and only if its graph representation is non-bipartite.

### Expected Return Time

```ad-definition
title: Recurrent State

Let $r^t_{i,j}$ denote the probability that, starting at state $i$, the first transition to state $j$ occurs at time $t$.

A state $i$ is **recurrent** if $\sum_{t\geq 1}r^t_{i,i} = 1$ and is **transient** otherwise. We say that a Markov chain is recurrent if every state is recurrent.

The quantity $h_{i,i}:= \sum_{t\geq 1}t\cdot r^t_{i,i}$ is the expected time to return to state $i$.
```

## Stationary Distributions

```ad-definition
title: Stationary Distribution

A **stationary distribution** on the state space $X$ is a distribution $\pi$ such that $\pi = \pi P$.

```

```ad-theorem
title: Finite Ergodic Markov Chains Have Stationary Distributions

Any finite, irreducible and ergodic Markov chain has the following properties:
1. the chain has a unique stationary distribution, $\pi$;
2. for all $i$ and $j$, the limit $\lim_{t\to \infty}P^t_{j,i}$ exists and is independent of $j$;
3. $\pi_i = \lim_{t\to \infty}P^t_{j,i} = 1/h_{i,i}$.
```

## Reverse Markov Property

A quippy summary of the Markov property is that "the future depends only on the present, not the past." It turns out that we can sort of reverse this

```ad-proposition

If $X_n$ is a Markov chain, then for any $k\geq 0$,
$$
\Pr[X_{n-1} = x_{n-1} \mid X_n = x_n] = \Pr[X_{n-1}=x_{n-1} \mid X_n=x_n,\ldots, X_{n+k}=x_{n+k}].
$$
```
Put obnoxiously, "the past depends only on the present, not the future."

*Proof.* Repeated application of the Markov property tells us that for any $k\geq 0$,
$$
\Pr[X_{n+1}=x_{n+1}, \ldots, X_{n+k} = x_{n+k}\mid X_n = x_n, X_{n-1}=x_{n-1}] = \Pr[X_{n+1}=x_{n+1}, \ldots, X_{n+k} = x_{n+k}\mid X_n = x_n].
$$
If we multiply both sides of this by $\Pr[X_{n-1} =x_{n-1}\mid X_n = x_n]$, then we get
$$
\Pr[X_{n-1} = x_{n-1}, X_{n+1}=x_{n+1}, \ldots, X_{n+k}=x_{n+k}\mid X_n=x_n] = \Pr[X_{n+1}=x_{n+1}, \ldots, X_{n+k} = x_{n+k}\mid X_n = x_n]\Pr[X_{n-1} =x_{n-1}\mid X_n = x_n].
$$
Now divide both sides by the first term on the RHS to get
$$
\begin{align}
\Pr[X_{n-1}=x_{n-1}\mid X_n=x_n] &= \frac{\Pr[X_{n-1} = x_{n-1}, X_{n+1}=x_{n+1}, \ldots, X_{n+k}=x_{n+k}\mid X_n=x_n]}{\Pr[X_{n+1}=x_{n+1}, \ldots, X_{n+k} = x_{n+k}\mid X_n = x_n]}\\
&= \Pr[X_{n-1}=x_{n-1}\mid X_n = x_n, \ldots, X_{n+k}=x_{n+k}].
\end{align}
$$