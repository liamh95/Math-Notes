Date Created: 2024-04-04
References: #ref/NONE
Tags: #theorem #graph-theory/matchings #graph-theory/algorithms  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

By [[Berge's Theorem]], a matching $M$ in a graph $G$ is maximum if and only if $G$ contains no $M$-augmenting path. At a high level, we can build a maximum matching by starting with some (maybe empty) matching and successively augmenting it (if $P$ is an $M$-augmenting path, then $M\triangle P$ is a larger matching). Ostensibly, it comes down to how we find these augmenting paths.



```ad-theorem
title: Edmonds' Blossom Algorithm



```

<i>Proof.</i> <% tp.file.cursor(2) %>