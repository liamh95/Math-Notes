Date Created: 2024-05-07
References: #ref/NONE
Tags: #theorem #probability/markov-chains 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Irreducible Markov Chains Can Be Reversed

If the [[Discrete-Time Markov Chain#Irreducible Markov Chains|irreducible markov chain]] $X_n$ is started from the [[Discrete-Time Markov Chain#Stationary Distributions|stationary distribution]] $\pi$, then the reversed chain $(Y_n)_{n=0}^N$, defined by $Y_n = X_{N-n}$ is also irreducible with transition probabilities
$$
\hat{P}_{xy} = \frac{\pi_y}{\pi_x}P_{xy}.
$$
The stationary distribution for $Y$ is also $\pi$.

```

<i>Proof.</i>  We just compute the relevant conditional probabilities. For any states $x_0, \ldots, x_{k+1}$,
$$
\Pr[Y_{k+1}=x_{k+1}\mid Y_k=x_k, \ldots, Y_0=y_0] = \Pr[X_{N-k-1} = x_{k+1}\mid X_{N-k}=x_k, \ldots, X_N=x_0].
$$
Now we apply the [[Discrete-Time Markov Chain#Reverse Markov Property|reverse Markov property]], so this is just
$$
\begin{align}
\hat{P}_{k, k+1} = \Pr[X_{N-k-1}=x_{k+1}\mid X_{N-k}=x_k] &= \frac{\Pr[X_{N-k-1}=x_{k+1}, X_{N-k}=x_k]}{\Pr[X_{N-k}=x_k]} = \frac{\pi(x_{k+1})P_{k+1, k}}{\pi(x_k)}.
\end{align}
$$