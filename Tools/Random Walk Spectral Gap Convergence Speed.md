Date Created: 2024-05-03
References: #ref/NONE
Tags: #theorem #probability/random-walk #linear-algebra/spectral-theory 

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

For concreteness, let's let $n = |V(G)|$ and $m = |E(G)|$. 

## Spectral Graph Theory

Let's look at the eigenvalues of the transition matrix. It's easy to see that $\pi$ is an eigenvector of $P$ with eigenvalue 1 since
$$
(\pi P)_u = \sum_v \pi_vP_{vu} = \frac{1}{2m}\sum_vd(v)P_{vu} = \frac{1}{2m}\sum_{vu\in E}1 = \frac{d(u)}{2m} = \pi_u.
$$

We claim that 1 is the largest eigenvalue. To see this, suppose $v$ is a (left) eigenvector with eigenvalue $\lambda$. Now let $a$ be the vertex that maximizes $|v(a)|/d(a)$. Then
$$
|\lambda||v(a)| = |\lambda v(a)| = \left| \sum_bv(b)P_{ba} \right| = \left| \sum_{ba\in E}v(b)/d(b) \right| \leq \sum_{ba\in E}\frac{|v(b)|}{d(b)} \leq \sum_{ba\in E}\frac{|v(a)|}{d(a)} = |v(a)|.
$$
Dividing through by $|v(a)|$ gives $|\lambda| \leq 1$.

Since $G$ is connected and non-bipartite, $P$ is a regular matrix, and by the [[Perron-Frobenius Theorem]], its largest eigenvalue, which we showed is 1, is simple.

Now let $A$ be the adjacency matrix of $G$ and let $D$ be the diagonal degree matrix, i.e., $D_{uu} = d(u)$. Notice that
$$
(D^{-1}A)_{uv} = \sum_w D^{-1}_{uw}A_{wv} = D^{-1}_{uu}A_{uv} = \begin{cases}1/d(u)&\text{if } uv\in E\\0&\text{otherwise} \end{cases} = P_{uv}.
$$
So $P = D^{-1}A$. In particular,
$$
D^{1/2}PD^{-1/2} = D^{1/2}(D^{-1}A)D^{-1/2} = D^{-1/2}AD^{-1/2}.
$$
The matrix on the far right, call it $M$, is symmetric. Since $P$ is similar to $M$, they have the same spectrum. By the [[Spectral Theorem for Real Symmetric Matrices]], $M$, and hence $P$, has an orthonormal basis of eigenvectors.


Notice that if $vP = \lambda v$, then $uD^{-1/2}M = \lambda(uD^{-1/2})$.  Say $v_1, \ldots, v_n$ are the normalized eigenvectors of $M$, ordered by eigenvalue (decreasing) so that $v_1$ has eigenvalue 1. Since $\pi$ is the 1-eigenvector of $P$, we should have
$$
v_1 = \frac{\pi D^{-1/2}}{\|\pi D^{-1/2}\|}.
$$
Now
$$
(\pi D^{-1/2})_u = \frac{1}{2m}\sum_v d(v)D_{vu}^{-1/2} = \frac{\sqrt{d(u)}}{2m}.
$$
Consequently, $\|\pi D^{-1/2}\| = 1/\sqrt{2m}$ and $v_1 = \sqrt{2m}\pi D^{-1/2}$. 

## Bounding the difference

Let $p_0$ be an arbitrary probability distribution on $V(G)$ and let $p_t = pP^t$. So
$$
p_1 = pP = p(D^{-1/2}MD^{1/2}) = (pD^{-1/2})MD^{1/2}.
$$
Now expand $pD^{-1/2}$ into the $M$-eigenbasis,
$$
pD^{-1/2} = \sum_i \alpha_i v_i,
$$
where $\alpha_i = pD^{-1/2}v_i^T$. The first coefficient is then
$$
\alpha_1 = pD^{-1/2}v_1^T = pD^{-1/2}(\sqrt{2m}D^{-1/2}\pi^T) = \sqrt{2m}pD^{-1}\pi^T = \frac{1}{\sqrt{2m}}p\overline{1}^T = \frac{1}{\sqrt{2m}}.
$$
In particular, when we expand $p_t$,
$$
\begin{align}
p_t &= pP^t\\
&= p(D^{-1/2}M^tD^{1/2})\\
&= \left(\sum_i \alpha_i v_i \right)M^t D^{1/2}\\
&= \alpha_1v_1D^{1/2} + \left(\sum_{i\geq 2}\alpha_i\lambda_i^tv_i  \right)D^{1/2}\\
&= \pi + \left(\sum_{i\geq 2}\alpha_i\lambda_i^tv_i  \right)D^{1/2}.
\end{align}
$$
Subtracting and taking the norm squared, we have
$$
\begin{align}
\|p_t-\pi\|_2^2 &= \left\| \left(\sum_{i\geq 2}\alpha_i\lambda_i^tv_i  \right)D^{1/2}  \right\|^2\\
&\leq \|D^{1/2}\|^2 \left\|\sum_{i\geq 2}\alpha_i\lambda_i^tv_i\right\|^2
\end{align}
$$
Now the operator norm of $D^{1/2}$ is at most $\Delta$. Since the $v_i$'s are orthonormal, this sum is at most
$$
\Delta \sum_{i\geq 2}(\alpha_i\lambda_i^t)^2 \leq \Delta |\lambda_2|^{2t}\sum_{i\geq 2}\alpha_i^2.
$$
We have
$$
\sum_{i}\alpha_i^2 = \|pD^{-1/2}\|^2 \leq \|p\|^2 \|D^{-1/2}\|^2 \leq 1/\delta.
$$
Consequently,
$$
\|p_t- \pi\|^2 \leq \frac{\Delta}{\delta}|\lambda_2|^{2t}.
$$
The theorem follows by setting $g = 1-|\lambda_2|$ and using [[Linear Bound for Exponential]].