Date Created: 2024-03-04
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 2]]
Tags: #theorem #ramsey-theory/ramsey-numbers #probabilistic-method/first-moment-method

Proved by: <i>Not Applicable</i>
References: Conlon Ramsey theory lecture notes: Lecture 2
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Diagonal Ramsey Number Random Lower Bound
$$
r(t) > \frac{t}{\sqrt 2 e}2^{t/2}.
$$
```

<i>Proof.</i> Two-color the edges of $K_n$ at random, where each color is chosen for each edge with probability $1/2$ independently. The expected number of monochromatic $K_t$'s is then
$$
2\binom{n}{t}2^{-\binom{t}{2}} < 2^{1-\binom t2}\frac{n^t}{t!} \leq 2^{-\binom t2}\left(\frac{ne}{t}\right)^t.
$$
Here we have used [[Stirling's Approximation]] to obtain $t! > 2(\frac{t}{e})^t$. Choosing $n = \frac{t}{\sqrt 2 e}2^{t/2}$ makes this expectation less than 1. There is then some coloring of $K_n$ with no monochromatic $K_t$.

*Remark*  This can be improved by a factor of 2 with the local lemma. See Alon-Spencer for this.