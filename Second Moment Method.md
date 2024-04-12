Date Created: 2024-04-12
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


## Markov's inequality

```ad-theorem
title: Markov's inequality

If $X$ is a nonnegative random variable whose expectation is defined, then for any nonnegative real $t$,
$$
\Pr[X \geq t] \leq \frac{E[X]}{t}.
$$
```

*Proof.* For any nonnegative $t$, we have $t I_{X \geq t} \leq X$ with probability 1 (where $I_E$ is the indicator random variable that is 1 when $E$ occurs and 0 otherwise). Since expectation is monotone increasing, we have
$$
E[X] \geq E[tI_{X \geq t}] = t\cdot \Pr[X \geq t].
$$

## Chebyshev's inequality

```ad-theorem
title: Chebyshev's inequality

If $X$ is a random variable with defined expectation $\mu$ and variance $\sigma^2$, then for any real $t$,
$$
\Pr[|X-\mu| \geq t] \leq \frac{\sigma^2}{t^2}.
$$
```

*Proof.* 

```ad-theorem
title: Second Moment Method



```

<i>Proof.</i> <% tp.file.cursor(2) %>