Date Created: 2024-05-06
References: #ref/NONE
Tags: #theorem #linear-algebra/spectral-theory 

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

```ad-theorem
title: Perron-Frobenius Theorem

Let $A$ be a real matrix with nonnegative entries that is *regular*, i.e., all entries of $A^k$ are positive for some $k \geq 1$.
Then
1. There is an eigenvalue $\lambda_{pf}$ that is real and positive with positive (entrywise) left and right eigenvectors;
2. Any other eigenvalue $\lambda$ satisfies $|\lambda| < \lambda_{pf}$;
3. The eigenvalue $\lambda_{pf}$ is *simple*, i.e. has algebraic multiplicity 1, which corresponds to a $1\times 1$ Jordan block.

We call $\lambda_{pf}$ the *Perron-Frobenius eigenvalue* of $A$ and the above eigenvectors are its left and right *Perron-Frobenius eigenvectors*.

```

<i>Proof.</i> <% tp.file.cursor(2) %>