Date Created: 2024-08-02
References: [[Nagle, R and Saff, E and Snider, A - Fundamentals of Ordinary Differential Equations - 2017]]
Tags: #theorem #ordinary-differential-equations 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Existence and Uniqueness of Solution to IVP

Consider the [[Initial Value Problem#Initial Value Problem]] 
$$
\frac{dy}{dx} = f(x,y),\quad y(x_0) = y_0.
$$
If $f$ and $\frac{\partial f}{\partial x}$ are continuous on some rectangle
$$
R = \{ (x,y): a \leq x \leq b,\ c\leq y \leq d \}\subseteq \mathbb{R}^2
$$
that contains the point $(x_0,y_0)$, then the IVP has a unique solution $\phi(x)$ in some interval $x_0-\delta < x < x_0 + \delta$, where $\delta$ is some positive number.

```

<i>Proof.</i> <% tp.file.cursor(2) %>