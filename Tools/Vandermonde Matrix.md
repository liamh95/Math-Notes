Date Created: 2024-07-07
References: #ref/NONE
Tags: #definition #linear-algebra

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

```ad-definition
title: Vandermonde Matrix

The (square) **Vandermonde matrix** has geometrix progressions in each row, given by
$$
V = V(x_1, \ldots, x_n) = \begin{bmatrix}
1 & x_1 & x_1^2 & \cdots & x_1^n\\
1 & x_2 & x_2^2 & \cdots & x_2^n\\
\vdots & \vdots & \vdots & \ddots & \vdots\\
1 & x_n & x_n^2 & \cdots & x_n^n\\
\end{bmatrix}
$$

```

## Determinant

```ad-theorem
title: Vandermonde determinant

The square Vandermonde matrix has determinant given by
$$
\prod_{1 \leq i < j\leq n} (x_j-x_i).
$$
In particular, the determinant is nonzero if and only if the $x_i$'s are distinct.
```

*Proof:* Just use row/column operations. Subtract from each column the previous column times $x_1$. This gives the following matrix (with the same determinant)
$$
\begin{bmatrix}
1 & 0 & 0 & \cdots & 0\\
1 & x_2-x_1 & x_2(x_2-x_1) & \cdots & x_2^{n-1}(x_2-x_1)\\
\vdots & \vdots & \vdots & \ddots & \vdots\\
1 & x_n-x_1 & x_n(x_n-x_1) & \cdots & x_n^{n-1}(x_n-x_1)\\
\end{bmatrix}.
$$
If we compute the determinant by expanding along the first row, we see that we can essentially ignore the first row and column. That is, this matrix has the same determinant as
$$
\begin{bmatrix}
x_2-x_1 & x_2(x_2-x_1) & \cdots & x_2^{n-1}(x_2-x_1)\\
x_3-x_1 & x_3(x_3-x_1) & \cdots & x_3^{n-1}(x_3-x_1)\\
\vdots & \vdots & \ddots & \vdots\\
x_n-x_1 & x_n(x_n-x_1) & \cdots & x_n^{n-1}(x_n-x_1)\\
\end{bmatrix}.
$$
Now factor out a $x_{i+1}-x_1$ out of row $i$. This gives a determinant of
$$
(x_2-x_1)(x_3-x_1)\cdots (x_n-x_1)\begin{vmatrix}
1 & x_2 & x_2^2 & \cdots & x_2^{n-1}\\
1 & x_3 & x_3^2 & \cdots & x_3^{n-1}\\
\vdots & \vdots & \vdots & \ddots & \vdots\\
1 & x_n & x_n^2 & \cdots & x_n^{n-1}
\end{vmatrix}.
$$
The claim then follows by induction.