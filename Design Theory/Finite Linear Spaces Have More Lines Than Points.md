Date Created: 2024-11-11
References: [[Jukna, Stasys - Extremal Combinatorics - 2011]]
Tags: #theorem #in-progress #design-theory #author/erdos-paul #author/conway-jh

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## De Bruijn - Erdos Theorem

```ad-theorem
title: De Bruijn - Erdos Theorem

If $\mathcal L$ is a [[Finite Linear Space#Finite linear space|finite linear space]] over $X$, then $|\mathcal L| \geq |X|$, with equality if and only if any two lines share exactly one point.

```

<i>Proof.</i> This proof from Jukna's book is attributed to JH Conway. Let $b = |\mathcal L|$ and $v = |X|$. For any point $x\in X$, let $r_x$ be the number of lines in $\mathcal L$ containing it (its *replication number* in the language of combinatorial set theory). If $x$ does not lie on the line $L\in \mathcal L$, then $r_x \geq |L|$ since there are $|L|$ lines joining $x$ to the points on $L$ (note that these lines are indeed distinct - otherwise we'd have two points that lie on some line with $x$ and on the line $L$). Suppose $b \leq v$. Then for $x\notin L$,
$$
bv + vr_x \geq bv + b|L| \implies b(v-|L|) \geq v(b - r_x).
$$
Hence,
$$
\begin{align*}
b &= \sum_{L\in \mathcal L}1\\
&= \sum_{L\in \mathcal L}\sum_{x: x\notin L}\frac{1}{v-|L|}\\
&\leq \frac bv \sum_{L\in \mathcal L}\sum_{x:x\notin L}\frac{1}{b-r_x}\\
&= \frac bv \sum_{x\in X}\sum_{L: x\notin L}\frac{1}{b-r_x}\\
&= \frac bv \sum_{x\in X}1\\
&= b.
\end{align*}
$$
So all inequalities here must be equalities, which gives $b = v$ and $r_x = |L|$ whenever $x\notin L$. 