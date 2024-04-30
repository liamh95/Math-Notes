Date Created: 2024-04-29
References: [[Magniez et al - Search via Quantum Walk - 2011]]
Tags: #theorem #quantum-computation/algorithms #probability/markov-chains #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Background

Lots of search problems can be phrased as trying to find a "marked" element in a set $X$ of $n$ elements. Let's call the set of all marked elements $M\subseteq X$. We could just randomly sample from $X$ until we hit something in $M$. If the set $X$ has some structure to it, it might be more efficient to generate these samples by a sort of random walk or Markov chain (that is, maybe we can reuse some of the resources used to generate the previous sample).

Quantum analogues of random walks have been used for a while to do some bullshit I don't really care about right now. Shenvi, Kempe and Whaley showed some algorithmic potential for walks by simulating Grover search with a walk. The first person to do something cool was Ambainis, who used quantum walks to beat Grover search for the element distinctness problem. Szegedy then developed a general theory of quantum walks based on Markov chains (complete with ideas like "quantum hitting times"). 

```ad-theorem
title: Magniez et al - Search via quantum walk - Main Idea



```

<i>Proof.</i> <% tp.file.cursor(2) %>