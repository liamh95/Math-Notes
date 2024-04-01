Date Created: 2024-04-01
References: #ref/NONE
Tags: #theorem #probabilistic-method/first-moment-method

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: First Moment Method

Suppose we randomly configure some object and let $X$ be some real-valued function defined on the object. Then there is some configuration where $X$ is at least $E[X]$ and there is some configuration where $X$ is at most $E[X]$.

```

<i>Proof.</i> By [[Probabilistic Method Basic Idea]], if we can show that $X \geq E[X]$ (or $\leq$) with positive probability, then we are done. But if $X < E[X]$ with probability 1, then
$$
E[X] = \int_{\Omega}X\ dP < \int_{\Omega} E[X]\ dP = E[X],
$$
a contradiction.