Date Created: 2024-05-03
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Random Walk Spectral Gap Convergence Speed

Let $G = (V,E)$ be a connected, non-bipartite graph with maximum degree $\Delta$ and minimum degree $\delta$. Let $P$ be the transition matrix for the random walk on $G$ defined by $P_{uv} = 1/d(u)$ if $uv\in E$ and 0 otherwise. Let $\pi$ be the probability distribution on $V(G)$ defined by $\pi_u = d(u)/2|E|$. Let $|\lambda_1| \geq |\lambda_2|\geq \cdots$ be the eigenvalues of $P$, and let $g = |\lambda_1| - |\lambda_2|$ denote the *spectral gap* of $P$. Then for any probability distribution $v$ on $V(G)$ and any $t > 0$,
$$
\|vP^t - \pi\|_2 \leq \sqrt{\frac{\Delta}{\delta}}|\lambda_2|^t \leq \sqrt{\frac{\Delta}{\delta}}e^{-gt}.
$$

```

<i>Proof.</i>  Let's let $n = |V(G)|$ and $m = |E(G)|$. It's easy to see that $\pi$ is an eigenvector of $P$ with eigenvalue 1 since
$$
(\pi P)_u = \sum_v \pi_vP_{vu} = \frac{1}{2m}\sum_vd(v)P_{vu} = \frac{1}{2m}\sum_{vu\in E}1 = \frac{d(u)}{2m} = \pi_u.
$$
