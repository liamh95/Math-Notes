Date Created: 2024-04-29
References: [[de Wolf, Ronald - Quantum Computing Lecture Notes - 2023]] [[Santha, Miklos - Quantum walk based search algorithms - 2008]]
Tags: #theorem #quantum-computation #quantum-computation/graph-algorithms #probability/markov-chains #probability/random-walk 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


What should the quantum analogue of a random walk (on a graph $G$) look like? Well at each step, we jump from the current vertex to one of its neighbors. One way to put this into a quantum framework is to work in to work in the space $V \otimes C$, where $C$ is a "coin space". To take a step in the walk, we apply a unitary "coin flip" operation $F$, controlled by the vertex register. More specifically, we should have something like 
$$
F|x, c\rangle = |x\rangle \otimes F^x|c\rangle,
$$
where $F^x$ shuffles the state $|c\rangle$ based on the vertex $x$. For example, if $G$ is a $d$-regular graph, then we can take $C$ to just be the linear span of $\{|j\rangle: 1 \leq j\leq d\}$  and $F^x$ can just be the [[Quantum Fourier Transform]] independent of $x$.

After we apply a coin flip, we advance the vertex state controlled by the coin state. This operator, call it $S$ (for "shift") takes $|x, c\rangle$ to some $|y, c\rangle$, where $y$ is some neighbor of $x$, dependent on $c$. When $G$ is $d$-regular and our coin space is spanned by the integers 1 through $d$, we can just assign these integers to fixed neighbors of $x$, so $S|x, c\rangle = |y, c\rangle$, where $y$ is the $c$-th neighbor of $x$.

For general graphs, we can take the coin space to also be $V$. In this case, the flip $F$ takes $|x, y\rangle$ to $|x\rangle$ tensored with a uniform superposition of $x$'s neighbors (where the phases are such that this operation is indeed unitary) and $S$ just swaps the registers. So really, the states $|x,y\rangle$ we deal with will always correspond to (perhaps directed) edges of $G$.

If we let $F'$ be the flip controlled on the second register instead, notice that
$$
FS|x, y\rangle = F|y, x\rangle = |y\rangle \otimes F^y|x\rangle
$$
and
$$
SF'|x,y\rangle = S(F^y|x\rangle \otimes |y\rangle) = |y\rangle \otimes F^y|x\rangle.
$$
So in particular, $SFSF = F'F$ and we can do away with the flips. We can then think of a quantum walk as alternately flipping the left and right registers -- that is, it should take $|x, y\rangle$, which corresponds to some edge, mix the right endpoint over neighbors of the left, then take the left endpoints of the resulting superposition and mix them over neighbors of the new right register. If we let $\mathcal A$ be the span of the states $|x\rangle |p_x\rangle$ and $\mathcal B$ be the span of the states $|p_y\rangle|y\rangle$, where
$$
|p_x\rangle = \sum_{y\in V}\sqrt{P_{xy}}|y\rangle,
$$
then the reflections through $\mathcal A$ and $\mathcal B$ should be the operators that do this. Here, $P$ is the usual random walk matrix for the graph $G$. Apparently sometimes we want reflection through $\mathcal B'$, the span of the states $|p_y^*\rangle |y\rangle$, where $P^*$ is the matrix for the time-reversed walk defined by the [[Detailed Balance Equations]]
$$
\pi_xP_{xy} = \pi_yP^*_{yx}.
$$

