Date Created: 2024-03-01
References: [[Conlon, David - Ramsey Theory Lecture Notes - Lecture 1]]
Tags: #corollary #ramsey-theory/ramsey-numbers 

Proved by: [[Ramsey Number Binomial Coefficient Bound]], [[Stirling's Approximation]]
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-corollary
title: Diagonal Ramsey Number Stirling Bound

$$
r(t) = O\left(\frac{4^t}{\sqrt t}\right).
$$

```

<i>Proof.</i> By [[Ramsey Number Binomial Coefficient Bound]] and  [[Stirling's Approximation]], 
$$
r(t) \leq \binom{2t}{t} = \frac{(2t)!}{(t!)^2} \approx \frac{\sqrt{4\pi t}(\frac{2e}{t})^{2t}}{2\pi t(\frac te)^{2t}} = \frac{4^t}{\sqrt{\pi t}}.
$$