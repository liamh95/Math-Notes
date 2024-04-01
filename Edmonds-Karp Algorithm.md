Date Created: 2024-03-31
References: #ref/NONE
Tags: #theorem #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>


The [[Ford-Fulkerson Algorithm]] for bipartite matchings works by constructing a flow network, finding a source-sink path, and then sending flow down it. It leaves the method of actually finding the source-sink path as a black box, however. In the following example, if the path-finding subroutine finds the $s\to a\to b\to t$ path and then the $s\to b \to a \to t$ path and so on, this algorithm will only add one unit of flow at a time, taking $2^{101}$ iterations in total. However, if it found the $s\to a\to t$ and then $s\to b \to t$ paths, then it'll just take 2 iterations.

![[Pasted image 20240331174604.png]]

```ad-theorem
title: Edmonds-Karp Algorithm



```

<i>Proof.</i> <% tp.file.cursor(2) %>