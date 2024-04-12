Date Created: 2024-04-09
References: #ref/NONE
Tags: #theorem #probabilistic-method/first-moment-method #graph-theory/independence-number

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Caro-Wei Theorem

Let $G = (V, E)$ be a graph. Then
$$
\alpha(G) \geq \sum_{v\in V}\frac{1}{d_v + 1}.
$$

```

<i>Proof.</i> Let $n = |V|$ and let $\pi:V\to [n]$ be a labelling of $V$ chosen uniformly at random. Define $I$ by
$$
I := \{v\in V: \{u,v\}\in E \implies \pi(u) < \pi(v) \}.
$$
That is, $I$ is the set of vertices whose neighbors all appear before it with respect to $\pi$. Then $I$ is an independent set. By the linearity of expectation,
$$
E[I] = \sum_{v\in V}\Pr[v\in I] = \frac{1}{d_v+1}.
$$
By the [[First Moment Method]], there is an independent set of size at least $\frac{1}{d_v+1}$.