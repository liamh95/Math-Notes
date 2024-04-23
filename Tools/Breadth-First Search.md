Date Created: 2024-04-01
References: #ref/NONE
Tags: #theorem #graph-theory/algorithms

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

How do we explore the connected components of a graph? This treatment of the algorithm assumes that the graph is stored as an adjacency list, so that each vertex has immediate access to its neighbors. It also assumes that every vertex can be marked as "explored" and have a "parent" vertex assigned to it in constant time.
## Algorithm

```ad-algorithm
title: Breadth-Frist Search

**Input: **A graph $G$ and a vertex $s\in V(G)$.
**Output: **An assignment of a parent to every vertex in the component of $s$. These parents trace out a shortest path to $s$ in $G$.

1. Let $Q$ be an empty queue
2. Mark $s$ as explored and enqueue it into $Q$
3. (Optionally) Set $s$`.d = 0`
4. `while` $Q$ is not empty
	1. $v \gets$ $Q$`.dequeue()`
	2. `for` each vertex $w$ adjacent to $v$
		1. `if` $w$ is unexplored
			1. Label $v$ as the parent of $w$
			2. (Optionally) Set $w$`.d = `$v$`.d + 1`
			3. Mark $w$ as explored and `enqueue` it into $Q$

```

## Correctness and Runtime

```ad-theorem
title: Breadth-First Search Correctness and Runtime

The Breadth-First Search (BFS) algorithm visits every vertex in the component of $s$ and parents trace a shortest path to $s$. The runtime of this algorithm is $O(m+n)$, where $n = |V(G)|$ and $m = |E(G)|$.
```

<i>Proof.</i> Assuming correctness, it's easy to analyze the runtime. Each vertex in the component of $s$ is enqueued and dequeued exactly once and labeled exactly once. Similarly, each edge is queried at most twice (when we get the neighbors of each vertex). Assuming we store the graph as an adjacency list, this comes out to $O(m+n)$ queries and basic operations (labeling, queue operations).

Assume that $v$`.d` is initially set to $\infty$. We claim that for any vertex $v$, $v$`.d` is at least the distance from $v$ to $s$ in $G$, $d(s, v)$. We can easily prove this by induction on the number of `enqueue` operations. On the first step, $s$`.d = 0`$=d(s,s)$. For the inductive hypothesis, assume we just discovered some vertex $v$ and enqueued it. This must have happened while exploring the neighbors of some just-dequeued vertex $u$. The inductive hypothesis says that $u$`.d`$\geq d(s, u)$. We then have
$$
v\text{.d} = u\text{.d}+1 \geq d(s, u) + 1 \geq d(s, v).
$$
Since we never enqueue $v$ again (as we marked it as "explored"), we never update $v$`.d`, so the above inequality remains true.

Let's say that at the current step, $Q = (v_1, \ldots, v_r)$, where $v_1$ is the head and $v_r$ is the tail. We claim that $v_r$`.d`$\leq v_1$`.d`$+1$ and that $v_i$`.d`$\leq v_{i+1}$`.d`$+1$. We again induct on the number of `enqueue` operations. This clearly holds when $Q$ just consists of $s$. When we `dequeue`, the head of $Q$ becomes $v_2$ (if the queue becomes empty, then the claim is vacuously true). By the inductive hypothesis, $v_1$`.d`$\leq v_2$`.d` and we have $v_r$`.d`$\leq v_1$`.d`$+1\leq v_2$`.d`$+1$, and the other inequalities are unaffected. The claim is then true after every `dequeue`. When we `enqueue`, it is because we are scanning the neighbors of some vertex $u$. We get a new vertex $v_{r+1}$. If this is the only item in $Q$, then the claim is vacuously true. Since we're scanning the neighbors of $u$, it was the previous head of the queue and we had $u$`.d`$\leq v_1$`.d` and $v_r$`.d`$\leq v_1$`.d`$+1$ by the inductive hypothesis. Now we have $v_{r+1}$`.d`$= u$`.d`$+1\leq v_1$`.d`$+1$ and $v_r$`.d`$\leq u$`.d`$+1 = v_{r+1}$`.d` and the remaining inequalities are unaffected.

From the above paragraph, it follows that if vertices $v_i$ and $v_j$ get enqueued during the run of BFS and $v_i$ was enqueued at some point before $v_j$, then $v_i$`.d`$\leq v_j$`.d` a the time where $v_j$ is enqueued. This is because at all points in time, the `d` value of the tail of the queue is at least the `d` value of the head of the queue (and we only update the `d` value of any vertex at most once).

Now let's suppose that some vertex receives a `d` value not equal to its true distance to $s$ in $G$. Of all such vertices, let $v$ be a vertex with shortest $d(s, v)$. We've shown that it's always the case that $v$`.d`$\geq d(s, v)$, so it must be the case that $v$`.d`$> d(s, v)$. We clearly can't have $v = s$ since we've set $s$`.d`$=0$ right off the bat. It must also be the case that $v$ is actually reachable from $s$, otherwise we would have $v$`.d`$>d(s, v) = \infty$. Then let $u$ be the vertex immediately preceding $v$ on some shortest $s$-$v$ path, which much exist since $v$ is reachable from $s$. Then we have $d(s, v) = d(s,u)+1$. By the minimality of how we chose $v$, we must have $u$.`d`$= d(s, u)$. Putting it all together, we have
$$
v\text{.d} > d(s, v) = d(s, u) + 1 = u\text{.d}+1.
$$
Let's look at where the BFS algorithm dequeued $u$. If $v$ was unexplored, then we're going to set $v$`.d` to $u$.`d`$+1$, which contradicts the above inequality. If $v$ was already explored, then it is either currently in $Q$ or has already been dequeued. If $v$ is currently in $Q$, then it was placed there after exploring the neighbors of some $w$, which was removed from $Q$ earlier than $u$ was. Then $v$`.d`$= w$`.d`$+1$, but since $w$ was removed from $Q$ earlier, $w$`.d`$\leq u$`.d`, so $v$`.d`$=w$`.d`$+1\leq u$`.d`$+1$, which contradicts the above inequality as well. Finally, if $v$ has already been dequeued, then $v$`.d`$\leq u$`.d`, contradicting the above inequality again.

In all cases, we have a contradiction, so we conclude that $v$`.d`$=d(s, v)$. This tells us that all vertices $v$ reachable from $s$ are indeed discovered, otherwise we'd have $\infty = v$`.d`$> d(s, v)$.

As for the claim about parents, notice that if $u$ is the parent of $v$, then $v$`.d`$=u$`.d`$+1$. Hence, to form a shortest $s$-$v$ path, first form a shortest $s$-$u$ path, then take an edge $u$-$v$.