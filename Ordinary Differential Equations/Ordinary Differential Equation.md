Date Created: 2024-08-02
References: [[Nagle, R and Saff, E and Snider, A - Fundamentals of Ordinary Differential Equations - 2017]]
Tags: #definition #ordinary-differential-equations

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Ordinary Differential Equation

```ad-definition
title: Ordinary Differential Equation

An **$n$-th order ordinary differential equation** is an equation of the form
$$
F\left(x, y, \frac{dy}{dx}, \frac{d^2y}{dx^2}, \ldots, \frac{d^ny}{dx^n} \right) = 0,
$$
where $F$ is a function of $x$, $y = y(x)$ and the derivatives of $y$ up to order $n$.

```

## Explicit Solution

```ad-definition
title: Explicit Solution

A function $\phi(x)$, that when substituted for $y$ into an ordinary differential equation satisfies the equation for all $x$ in some interval $I$ is called an **explicit solution** to the equation on $I$.
```

## Implicit Solution

```ad-definition
title: Implicit Solution

A relation $G(x,y) = 0$ is an **implicit solution** to an ordinary differential equation on the interval $I$ if it defines one or more explicit solutions on $I$.
```

### Example

```ad-example
title: Implicit Solution
The relation
$$
x+y+e^{xy} = 0
$$
is an implicit solution to the differential equation
$$
(1+xe^{xy})\frac{dy}{dx}  + 1 +ye^{xy}=0,
$$
since differentiation just gives,
$$
\frac{d}{dx}(x+y+e^{xy}) = 1 + \frac{dy}{dx} + e^{xy}\cdot \left( y + x\frac{dy}{dx} \right),
$$
which rearranges to the ODE.
```
