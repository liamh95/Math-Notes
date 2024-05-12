Date Created: 2024-05-09
References: #ref/NONE
Tags: #example #quantum-computation #probability/random-walk 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>


As per the discussion on [[Quantum Walks]], let's build a quantum random walk on $\mathbb Z$. Using the formalism of the state consisting of a vertex on our graph and a "coin", our state should look like $|\psi\rangle |s\rangle$, where
$$
|\psi\rangle = \sum_{z\in \mathbb Z}\alpha_z |z\rangle
$$
is such that
$$
\sum_{z\in \mathbb Z} |\alpha_z|^2 = 1
$$
and
$$
|s\rangle = \beta_+|+1\rangle + \beta_-|-1\rangle
$$
is the "coin" (sometimes a "spin state"). The conditional shift operator $S$ is what we'll use to move our particle around $\mathbb Z$. We'll define it by its action on basis states
$$
\begin{align}
S |+1, z\rangle &= |+1, z+1\rangle\\
S |-1, z\rangle &= |-1, z-1\rangle.
\end{align}
$$
In other words, $S$ shifts the vertex register based on where the coin lands in the obvious way. Formally, $S$ is given by
$$
S = |+1\rangle\langle +1|\otimes \sum_{j\in \mathbb Z}|j+1\rangle\langle j| + |-1\rangle\langle -1|\otimes \sum_{j\in \mathbb Z}|j-1\rangle \langle j|.
$$
Depending on how we flip the coin, we'll get different distributions for our walk location.

## Hadamard Coin

Say we start with the sate $|0, +1\rangle$, i.e, our position is the origin and our coin is pointing to the right. Let's say we flip our coin by acting on it with a Hadamard gate, $H$,
$$
H = \frac{1}{\sqrt 2}\begin{bmatrix}
1 & 1\\
1 & -1
\end{bmatrix}.
$$
Then flipping our coin takes our state to
$$
|0\rangle \otimes\left(\frac{1}{\sqrt 2}|+1\rangle + \frac{1}{\sqrt 2}|-1\rangle \right).
$$
Applying the conditional shift $S$ then takes our first step, giving us the state
$$
\frac{1}{\sqrt 2}\big(|1, +1\rangle + |-1, -1\rangle\big).
$$
Now if we measure at this point, we'll get $|1, +1\rangle$ and $|-1, -1\rangle$ each with probability $1/2$. Repeating this procedure of "flip, step, measure" will give us the usual random walk on $\mathbb Z$. The interesting part is what happens when we postpone measurement and just walk "quantumly".

Say we walk another step without measuring. A two-step computation shows that we'll end up in the state
$$
\frac{1}{2}\big(|2, +1\rangle + |0, -1\rangle + |0, +1\rangle - |-2, -1\rangle  \big).
$$
If we measure here then we see the usual measurement statistics for the position. But notice the negative phase on $|-2, -1\rangle$. Another computation shows that the state after a third round is
$$
2^{-3/2}\big( |3, +1\rangle + 2|1, +1\rangle + |1, -1\rangle - |-1, +1\rangle +|-3, -1\rangle \big).
$$
Measuring at this stage has an asymmetric distribution! Notice that the particle has probability $5/8$ of being at $-1$. The asymmetry appears to be coming from phase interference (e.g. the phases on the $|-1, -1\rangle$ term cancelled each other on this step) and the fact that $H$ treats the $|+1\rangle$ and $|-1\rangle$ states differently. The first few iterations make it look like the peak of this distribution shifts to the right (prove this?).

If the starting state is instead
$$
|0\rangle \otimes \frac{1}{\sqrt 2}\big(|+1\rangle - i|-1\rangle  \big),
$$
then one can show that the walk now has a symmetric distribution. Interestingly though, it is *not* the same as a classical random walk. For example, on the fourth step, the state is
$$
2^{-5/2}\big[-(1+i)\big(|-4, -3\rangle + |-2, -3\rangle \big) + (1+3i)|-2,-1\rangle -(1-i)|0,-1\rangle + (1+i)|0,1\rangle - (3-i)|2,1\rangle + (1-i)\big(-|2,3\rangle + |4,3\rangle \big)  \big].
$$
At this point, measurement would give these outcomes

| Position | Probability |
| -------- | ----------- |
| $-4$     | $1/16$      |
| $-2$     | $3/8$       |
| $0$      | $1/8$       |
| $2$      | $3/8$       |
| $4$      | $1/16$      |
Whereas the classical random walk has these statistics

| Position | Probability |
| -------- | ----------- |
| $-4$     | $1/16$      |
| $-2$     | $1/4$       |
| $0$      | $3/8$       |
| $2$      | $1/4$       |
| $4$      | $1/16$      |

