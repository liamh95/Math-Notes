Date Created: 2024-04-29
References: [[de Wolf, Ronald - Quantum Computing Lecture Notes - 2023]] [[Santha, Miklos - Quantum walk based search algorithms - 2008]]
Tags: #theorem #quantum-computation #quantum-computation/graph-algorithms #probability/markov-chains #probability/random-walk 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


## Classical Random Walks

### Markov chain review

Say we have an undirected graph $G$ on $N$ vertices. Say an $\epsilon$-fraction of the vertices are "marked" and we want to find a marked vertex. One way we could do this is to just sample vertices at random. This might not be feasible if we don't have access to all of $G$ at once. Another option is to randomly walk along $G$ as follows.
1. Start at some specific vertex $y\in V$ (deterministic or random)
2. `while` $y$ is not a marked vertex
	1. Let $x$ be a random neighbor of  $y$
	2. Set $y$ to $x$
This is lighter on memory since we only need to store our current vertex and have a reference to its neighbors (i.e. we only need local info about our graph).

A random walk on $G$ corresponds to an $N\times N$ stochastic matrix where $P_{uv} = 1/d(u)$ if $v\in N(u)$ and 0 otherwise. If $v\in \mathbb{R}^N$ is a probability distribution on $V(G)$, then $vP$ is the new probability distribution on the vertices after taking one step of the random walk (see [[Discrete-Time Markov Chain]]).

If we assume that $G$ is connected and not bipartite, then $vP^k$ will converge to the uniform distribution on $V(G)$, and we'll see that the speed of convergence depends on the gap between the largest and second largest eigenvalues of $P$. 

Let $D$ be the *degree matrix* of $G$, i.e. $D_{uv} = d(u)$ if $v=u$ and 0 otherwise. While $P$ is not necessarily symmetric, it is similar to a symmetric matrix as
$$
D^{1/2}PD^{-1/2} = D^{1/2}(D^{-1}A)D^{-1/2} = D^{-1/2}AD^{-1/2} =: M.
$$
Here, $A$ is the adjacency matrix of $G$. We then have $P = D^{-1/2}MD^{1/2}$. Since $P$ and $M$ are similar, they have the same eigenvalues. Since $M$ is symmetric, is has an orthonormal basis of eigenvectors.

Let $|\lambda_1| \geq |\lambda_2| \geq \cdots \geq |\lambda_N|$ be the (left) eigenvalues of $P$ arranged by magnitude in the complex plane and let $v_i$ be the eigenvector for $\lambda_i$. By the Perron-Frobenius theorem, $\lambda_1 = 1$ and this eigenvalue is simple. Let $\delta:= 1-|\lambda_2|$ denote the *spectral gap* of $G$. 





```ad-theorem
title: Quantum Walks



```

<i>Proof.</i> <% tp.file.cursor(2) %>