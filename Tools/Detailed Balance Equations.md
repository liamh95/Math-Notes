Date Created: 2024-05-09
References: #ref/NONE
Tags: #definition #probability/markov-chains 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

We can reverse [[Discrete-Time Markov Chain|Markov chains]] in time. If $Y_k := X_{N-k}$ is the time-reversal of the irreducible chain $X_n$, then if $\hat{P}$ is the transition matrix of $Y_n$, then by [[Irreducible Markov Chains Can Be Reversed]],
$$
\hat{P}_{xy} = \frac{\pi_y}{\pi_x}P_{yx}.
$$
Now what if we want the reversed chain to "look like" the forward chain, i.e., $\hat{P}_{xy} = P_{xy}$. Then the above condition gives us the following.

```ad-definition
title: Detailed Balance Equations

If $X_n$ is an irreducible Markov chain with stationary distribution $\pi$, then if $\pi$ and the transition matrix $P$ satisfy the **detailed balance equations**
$$
\pi_x P_{xy} = \pi_y P_{yx},
$$
then we call the chain $X_n$ **reversible**.

```

If we sum over $x$, then we see that satisfying the detailed balance equations implies the existence of the stationary distribution (the converse isn't true though - there are chains with stationary distributions that don't satisfy detailed balance).