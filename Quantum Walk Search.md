Date Created: 2024-05-09
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


## The Problem

Say we have an undirected graph $G$ on $N$ vertices. Say an $\epsilon$-fraction of the vertices are "marked" and we want to find a marked vertex.
## Classical Random Walks

One way we could do this is to just sample vertices at random. This might not be feasible if we don't have access to all of $G$ at once. Another option is to randomly walk along $G$ as follows.
1. Start at some specific vertex $y\in V$ (deterministic or random)
2. `while` $y$ is not a marked vertex
	1. Let $x$ be a random neighbor of  $y$
	2. Set $y$ to $x$
This is lighter on memory since we only need to store our current vertex and have a reference to its neighbors (i.e. we only need local info about our graph).

A random walk on $G$ corresponds to an $N\times N$ stochastic matrix where $P_{uv} = 1/d(u)$ if $v\in N(u)$ and 0 otherwise. If $v\in \mathbb{R}^N$ is a probability distribution on $V(G)$, then $vP$ is the new probability distribution on the vertices after taking one step of the random walk (see [[Discrete-Time Markov Chain]]).

Let's assume that $G$ is regular and non-bipartite. Then $vP^t$ will converge to the uniform distribution on $V(G)$, and the speed of convergence depends on the gap between the largest and second largest eigenvalues of $P$. In particular (see [[Random Walk Spectral Gap Convergence Speed]]), 1 is the largest eigenvalue of $P$ and if we let $g$ be the gap between 1 and the (absolute value of) second largest eigenvalue, then
$$
\|vP^t - \pi\| \leq e^{-gt},
$$
which is less than some constant $\eta$ as long as $t \geq \frac{1}{g}\ln(1/\eta)$. So after this many steps, we have around an $\epsilon$ probability of hitting a marked state.

So if $S$ is the cost of setting up the walk data structure, $U$ is the cost of updating the walk state and $C$ is the cost of checking if a state is marked state, consider this procedure.
1. Start at some vertex $v$
2. while $v$ is not marked
	1. run $\frac{1}{g}\ln(1/\eta)$ steps of the random walk 
Then the expected number of queries we need is
$$
S + \frac{1}{\epsilon}(C + \frac{1}{g}U),
$$
up to constant factors.
