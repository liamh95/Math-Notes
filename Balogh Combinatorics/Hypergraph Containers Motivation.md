Date Created: 2024-03-11
References: #ref/NONE
Tags: #example #graph-theory/containers 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>



Let $\mathcal H$ be some hypergraph and let $\mathcal I (\mathcal H)$ be the collection of its independent sets. Many problems in combinatorics can be phrased as estimating $|\mathcal I(\mathcal H)|$ for some $\mathcal H$ (see [[Independent Set Problems]]). How can we estimate $|\mathcal I(\mathcal H)|$? Well every independent set is contained in some maximal (not necessarily maximum) independent set, so we have
$$
2^{\alpha(\mathcal H)} \leq |\mathcal I(\mathcal H)| \leq \binom{|V(\mathcal H)|}{\alpha(\mathcal H)}2^{\alpha(\mathcal H)} \leq 2^{\alpha(\mathcal H)\cdot \log|V(\mathcal H)|}.
$$
These lower and upper bounds differ by a factor of $n$. Can we do better? Suppose we had a collection $\mathcal C$ of sets such that each independent set of $\mathcal H$ was contained in some $C\in \mathcal C$. For example, $\mathcal C = \binom{V(\mathcal H)}{\alpha(\mathcal H)}$ works. Then
$$
|I(\mathcal H)| \leq \sum_{C\in \mathcal C}2^{|C|} \leq |\mathcal C|\cdot 2^{\max_{C\in \mathcal C}|C|}.
$$
We can then beat the trivial estimate if we can find a small collection $\mathcal C$ such that each $C\in \mathcal C$ is also small.