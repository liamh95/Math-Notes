Date Created: 2024-05-07
References: #ref/NONE
Tags: #definition #quantum-computation 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

```ad-definition
title: Quantum Fourier Transform

The *quantum Fourier transform* is just the classical discrete Fourier transform applied to the the amplitudes of a quantum state.

If the length of the state is $N$ (usually we have $N= 2^n$ for some $n$, but not always), then the quantum Fourier transform maps the state $|x\rangle = \sum_{k=0}^{N-1} x_k|k\rangle$ to the state $|y\rangle = \sum_{k=0}^{N-1}y_k|k\rangle$, where
$$
y_k = N^{-1/2}\sum_{j=0}^{N-1}x_j\omega_N^{jk}.
$$
Here, $\omega_N = e^{2\pi i/N}$, is an $N$-th root of unity.

```

```ad-definition
title:Quantum Fourier Transform Matrix

With the quantum Fourier transform as defined above, the transformation takes the vector of amplitudes $(x_0, \ldots, x_{N-1})$ to the vector of amplitudes $(y_0, \ldots, y_{N-1})$ via
$$
\begin{bmatrix}y_0 \\ y_1\\ \vdots \\ y_{N-1} \end{bmatrix} = N^{-1/2} \begin{bmatrix} 1 & 1 & 1 & \cdots & 1\\
1 & \omega_N & \omega_N^2  & \cdots & \omega_N^{N-1}\\
1 & \omega_N^2 & \omega_N^4 & \cdots & \omega_N^{2(N-1)}\\
\vdots & \vdots & \vdots & &\vdots\\
1 & \omega_N^{N-1} & \omega_N^{2(N-1)} & \cdots & \omega_N^{(N-1)(N-1)}\end{bmatrix}\begin{bmatrix} x_0\\ x_1\\ \vdots \\ x_{N-1}\end{bmatrix}.
$$
```
