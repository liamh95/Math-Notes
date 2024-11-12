Date Created: 2024-09-20
References: [[Sinnamon, Corwin - Fast and simple edge-coloring algorithms - 2019]]
Tags: #theorem #graph-theory/coloring #graph-theory/algorithms  #in-progress

Proved by: <i>Not Applicable</i>
References: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

Specializations: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

## Algorithms

### Deterministic version

```ad-theorem
title: Sinnamon's Edge Coloring Algorithm (Deterministic)

Let $G$ be a graph with $n$ vertices and $m$ edges with maximum degree $\Delta$. Then there is an algorithm that produces a proper $(\Delta+1)$-edge-coloring of $G$ in $O(m\sqrt n)$ time (in the RAM model of computation where $G$ is stored as an adjacency list).

```

By [[Vizing's Theorem#Vizing's Theorem|Vizing's theorem]], we can't in general hope to get by with fewer colors.
### Randomized version

```ad-theorem
title: Sinnamon's randomized edge coloring algorithm

Let $G$ be a graph with $n$ vertices and $m$ edges with maximum degree $\Delta$. Then there is a randomized algorithm that $(\Delta+1)$-edge-colors $G$ in $O(m\sqrt n)$ time with probability $1-e^{-\sqrt m}$ (the algorithm always succeeds, this is a bound on the probability that the runtime doesn't exceed this cutoff).

```

## General framework

Sinnamon outlines a general framework for several different edge-coloring algorithms. They break it down into a few high-level procedures. Say we're trying to edge color $G$, which has $n$ vertices, $m$ edges and maximum degree $\Delta$ with at most $N$ colors

1. **Partition.** Partition $G$ into two edge-disjoint subgraphs such that each subgraph has half of the edges ($\leq \lceil m/2\rceil$) and the maximum degree of each subgraph is at most half that of the original graph ($\leq \lceil \Delta /2 \rceil$). This can be done in $O(m)$ time by just removing maximal tours from $G$ until no edges remain. Then, for each tour, traverse it and alternately assign the edges to the two subgraphs.
2. **Recurse.** Color the two subgraphs from the partitioning step with at most $\lceil N/2\rceil$ colors each and with disjoint color palettes. Then take the union of the two colorings.
3. **Prune.** After recursing and putting the colorings together, we obtain a coloring that uses up to $2\lceil N/2\rceil$ colors, which could be more than $N$ (e.g. if we're trying to use $\Delta+1$ colors, then this could be up to $\Delta+3$). Let $t$ be the number of excess colors used (the number used minus $N$). Choose the $t$ least used colors and uncolor all edges that use these colors. The number of uncolored edges is at most $m\frac{t}{N+t}$.
4. **Repair.** Now we have to fix the uncolored edges.

Since steps 1-3 are pretty much entirely specified above, Sinnamon's main contribution is in the Repair step.

## Idea behind algorithms

### Deterministic case

We can do more than coloring one edge at a time. Sinnamon's deterministic algorithm makes use to two subroutines.
- `Color-One` colors a given uncolored edge in $O(n)$ time
- `Color-Many` colors $\Omega(\ell/\Delta)$ edges in $O(m)$ time, where $\ell$ is the number of uncolored edges at this time.
How do we decide which to use? Well `Color-Many` uses an average of $O(m\Delta/\ell)$ time per edge it colors, so this is (up to the constant in the asymptotic notation) better than `Color-One` when $\ell = \Omega(m\Delta/n)$. So at a high level, our algorithm should look like this.

1. `while` $\ell \geq 2m\Delta/n$:
	1. `Color-Many()`
2. `while` $\ell > 0$:
	1. Let $e$ be an uncolored edge
	2. `Color-One`$(e)$.

Assuming the runtimes of `Color-One` and `Color-Many` are as stated above, we can prove the runtime of the overall algorithm.

*Proof of correctness and runtime of [[Sinnamon's Edge Coloring Algorithm#Algorithms#Deterministic version|deterministic algorithm]]*. The correctness is immediate since `Color-One` and `Color-Many` each strictly increase the number of colored edges and it won't use more than $\Delta+1$ colors.

Now at the end of the recursion step there are at most $2(\lceil \Delta/2\rceil +1) \leq \Delta+3$ colors used, so we have at most 2 excess colors in play. Consequently, the number of uncolored edges $\ell$ at the start of the repair step is at most $\frac{2m}{\Delta+3}$. Comparing this to $2m\Delta/n$, we see that when $\Delta< \sqrt n$, `Color-Many` is run until $\ell$ decreases from $\leq \frac{2m}{\Delta+3}$ to $2m\Delta/n$. Notice that running `Color-Many` a constant number of times reduces the number of uncolored edges by a factor of $1-\frac 1\Delta$. We have that
$$
\ell\left(1 - \frac 1\Delta\right)^{2\Delta\ln(2\sqrt n/\Delta)} < \frac{2m}{\Delta+3}e^{-2\ln(2\sqrt n/\Delta)}< \frac{2m\Delta}{n},
$$
since $(1-\frac 1\Delta)^\Delta < \frac 1e$. So it takes $O(\Delta \ln(2\sqrt n/\Delta))$ repetitions of `Color-Many`, each of which takes $O(m)$ time, before `Color-One` becomes more efficient. Then we run `Color-One` on each of the remaining $\leq 2m\Delta/n$ uncolored edges, each taking $O(n)$ time. The total runtime of the repair step is then
$$
O\big( m\Delta\log(2\sqrt n/\Delta) \big).
$$
On the other hand, if $\Delta \geq \sqrt n$, then we never run `Color-Many` since
$$
\ell \leq \frac{2m}{\Delta+3} \leq \frac{2m}{\sqrt n + 3} \leq \frac{2m\Delta}{n}.
$$
Consequently, each uncolored edge is colored with `Color-One`, so the repair step takes $O(mn/\Delta)$ time.

That's the analysis of the repair step, but now let's include the Partition, Recursion and Pruning steps. Consider the recursion tree we get by executing the whole algorithm. This is a binary tree whose root node corresponds to the original graph $G$. The children of $G$ are $G_1$ and $G_2$, whose edge sets are defined by the Partition step and their children are defined recursively. The leaves of the recursion tree correspond to graphs with maximum degree 1. Identify nodes in this recursion tree with their corresponding subgraphs of $G$. For a subgraph $H$, we let $m_H$ and $\Delta_H$ be the number of its edges and its maximum degree, respectively.

For each subgraph $H$ in the recursion tree, let $T(H$) be the time spent on it (up to a constant factor), i.e.
$$
T(H):= \begin{cases}
m_Hn/\Delta_H &\text{if }\Delta_H\geq \sqrt n\\
m_H\Delta_H\log(2\sqrt n/\Delta_H) &\text{if }\Delta_H < \sqrt n
\end{cases}.
$$
Note that this is indeed the *total* time spent on $H$, since the Partition and Pruning steps each take $O(m_H)$ time. The total runtime of the algorithm is then the sum of $T(H)$ as $H$ ranges over all subgraphs in the recursion tree. We break the costs into cases based on $\Delta_H$.
- *High degree subgraphs*. We say that a subgraph has high degree if $\Delta_H \geq \sqrt n$. These subgraphs occupy a depth of at most $\log(2\Delta/\sqrt n)$ in the recursion tree, since the maximum degree roughly halves as we jump down a level. The subgraphs in a given level exactly partition the edge set of the original graph $G$, so the total cost of the high degree subgraphs is at most
  $$
   \sum_{i=0}^{\log(2\Delta/\sqrt n)}\sum_{H\text{ at level }i}\frac{m_Hn}{\Delta_H}\leq \sqrt n\sum_{i=0}^{\log(2\Delta/\sqrt n)}\sum_{H\text{ at level }i}m_H = \sqrt n\sum_{i=0}^{\log(2\Delta/\sqrt n)}m \leq m\sqrt n.
   $$
- *Low degree subgraphs.* Fix a low degree subgraph $H$, i.e., $\Delta_H <\sqrt n$. Let $H_1$ and $H_2$ be its children in the recursion tree. Notice that for $i = 1,2$,
  $$
   T(H_i) \leq \left(\frac{m_H+1}{2}\right)\left(\frac{\Delta_H+1}{2}\right)\log(4\sqrt n/\Delta_H)\approx \frac{1}{4}T(H).
   $$
   So the time spent drops by a factor of about 4 from parent to child. If we do this calculation a little more precisely, we can see that we definitely have $T(H_i) \leq \frac 13 T(H)$ for sufficiently large $\Delta_H$ (except possibly towards the bottom of the recursion tree where the max degrees are below some constant).
   This is great because the cost shrinks at a rate faster than the number of subgraphs grows. That is, the *combined* time spent on $H$ and *all* of its descendants is at most
   $$
   \sum_{t=0}^\infty \left(\frac 23\right)^tT(H) = O\big( T(H)\big).
   $$
   So the time spent on all low degree subgraphs is proportional to the combined cost of the "maximal" low degree subgraphs (i.e., those whose parents are high degree). When $\Delta \geq \sqrt n$, the maximal low degree subgraphs partition $E(G)$ and each such subgraph has $\Delta_H \in [\sqrt n/2, \sqrt n)$. The combined time spent on these is at most
   $$
   m\sqrt n \log(4\sqrt n/\sqrt n) = O(m\sqrt n).
   $$
   On the other hand, if $\Delta < \sqrt n$, the only maximal low degree subgraph is $G$ itself and the total cost is $O(m\Delta \log (2\sqrt n/\Delta)) = O(m\sqrt n)$ in this case.

### Randomized case

That analysis wasn't too complicated, but we haven't even specified what `Color-One` and `Color-Many` do. It turns out that `Color-Many` is pretty complicated. Sinnamon gives an alternative, `Random-Color-One` that colors a single uncolored edge in $O(md/\ell)$ time *in expectation* and $O(n)$ time in the worst case. This is huge since this is the same time per edge (but in expectation now) as the complicated `Color-Many`. It's also no worse than `Color-One`, so this randomized subroutine can replace *both* `Color-Many` and `Color-One`. So our randomized algorithm, at a high level, is just

1. `while` $\ell > 0$:
	1. `Random-Color-One()`

The runtime analysis is simpler in this case. It's just
$$
\sum_{\ell=1}^{2m/d}\min\left(\frac{md}{\ell}, n \right) = \begin{cases}
O(mn/d)&\text{if }d \geq \sqrt n\\
O(md \log(2\sqrt n/d)) & \text{if }d < \sqrt n
\end{cases},
$$
which comes out to $O(m\sqrt n)$ by the analysis we used in the deterministic case.

We claim that we can actually get a *high probability* runtime. Let $T(G)$ be the the number of calls to `Random-Color-One`. All other operations are deterministic and run in $o(m\sqrt n)$ time, so we just need to look at $T(G)$. Over the course of the randomized algorithm, we apply `Random-Color-One` to a bunch of partially-edge-colored graphs, $G_1, \ldots, G_k$, where $G_i$ has $m_i$ edges, $\ell_i$ of which are uncolored and maximum degree $\Delta_i$. These quantities are not random variables (although the colorings are) since the partition step is deterministic.

Let $R_i$ be runtime of `Random-Color-One` on $G_i$, a random variable. These variables are independent since the $G_i$ are deterministic (?) and $T(G) = \sum_{i=1}^k R_i$. By the above analysis, $E[T(G)] \leq C m\sqrt n$ for some constant $C$.

Now in the worst case, `Random-Color-One` runs in time $O(n)$, so $R_i \leq Cn$ (just relabel constants so we can use the same $C$). We then have $\text{Var}[R_i] \leq E[R_i^2] \leq Cn\cdot E[R_i]$. By independence,
$$
\text{Var}[T(G)] = \sum_{i=1}^k \text{Var}[R_i] \leq C^2mn^{3/2}.
$$
Now we can just apply [[Bernstein Inequalities#Tail bound with variance|Bernstein's inequality]]: set $t = 3m^{1/2}n^{-1/4}$ so that $t\sigma \leq 3Cm\sqrt n$ and
$$
\Pr[T(G) \geq E[T(G)] + 3Cm\sqrt n] \leq \exp \left(-\frac{\frac 92m/\sqrt n}{1 + \frac 13\frac{Cn}{Cm^{1/2}n^{3/4}}\frac{3m^{1/2}}{n^{1/4}}}  \right) = \exp\left(-\frac{\frac 92m\sqrt n}{2}  \right) < e^{-\sqrt m}.
$$
The last inequality holds because we assume there are no isolated vertices, so $m \geq n/2$. So the probability that the runtime exceeds $O(m\sqrt n)$ is $e^{-\sqrt m}$.

## The details

For a vertex $v$ and partial edge-coloring $c$, we let $M(v)$ be the set of colors (in $[\Delta+1]$) missing at $v$ (note that this set is always nonempty). We use some notions that come from the usual proofs of [[Vizing's Theorem#Vizing's Theorem|Vizing's theorem]]. 

### c-Fan

```ad-definition
title: c-Fan

A **c-fan** $F$ is a sequence $(\alpha, v, x_0, x_1, \ldots, x_k)$ such that
- $\alpha$ is a color in $M(v)$
- $x_1, \ldots, x_k$ are distinct neighbors of $v$
- $vx_0$ is uncolored
- $vx_i$ is colored $\beta_i$ for all $1\leq i \leq k$
- $c(vx_i)$ is missing at $x_{i-1}$ for $1 \leq i \leq k$.

Let $0 \leq j \leq k$. To **shift $F$ from $x_j$** means to set $c(vx_i)$ to $\beta_i$ for $i = 1, \ldots, j$ and uncolor $vx_j$.

The c-fan $F$ is **primed by $\beta$** if $\beta$ satisfies one of
- $\beta \in M(x_k)$ and $\beta \in M(v)$ or
- $\beta \in M(x_k)$ and there is a leaf $x_j$ so that $c(vx_j) = \beta$.
```

Other sources sometimes just call this a Vizing fan, except here the color missing at $v$ is a specified piece of data. Note that by the fan properties, shifting a c-fan $F$ produces another proper partial edge coloring that preserves $M(v)$ and produces another c-fan. As per the proof of Vizing's theorem, the point of a primed c-fan is that it lets us color an extra edge after some shifting.

### Data structures

Sinnamon uses the following data structures in their algorithm. Their dictionary implementation is a bit bespoke.

- $G$ is stored as an adjacency list, i.e., for each vertex, we keep a list of the edges incident to it.
- For each vertex $v$, the structure $\mu(v)$ will store colors missing at $v$, *but not all of them*. We will only store the colors in $M(v)\cap [d(v) +1]$ and this will always be nonempty. The structure $\mu(v)$ will consist of a [[Linked List#Doubly-linked list|doubly-linked list]] containing the colors in $M(v)\cap [d(v)+1]$ and an array of length $d(v)+1$, containing pointers to the $d(v)+1$ items that can be in the list (the integers $[d(v)+1]$?). Whenever we color an edge incident to $v$ with $\gamma \in [d(v)+1]$, find the node for $\gamma$ in the array and remove it from the list (which can be done in $O(1)$ time). If an edge incident to $v$ with color $\gamma \in [d(v)+1]$ is uncolored, find the color $\gamma$ in the array and append that color to the linked list. We can initialize $\mu(v)$ in $O(d(v))$ time.
- We use a dictionary $\mathcal D$ that maps vertex-color pairs $(v, \gamma)$ to the edge incident to $v$ colored $\gamma$, if such an edge exists. It can search, insert and delete in constant time. There is another section with its implementation details.

### Color-One

This procedure, which colors a single uncolored edge, is pretty much what Vizing described in his original paper. It chooses an uncolored edge $vx_0$ and picks a color $\alpha$ missing at $v$. It then calls the procedure `Make-Primed-Fan` that builds a c-fan $F = (\alpha, v, x_0, \ldots, x_k)$ primed by the color $\beta \in M(x_k)$. Then it "activates" the fan, i.e., colors the edge $vx_0$ by doing some shifting.

1. `Color-One()`
	1. Choose an uncolored edge $vx_0$
	2. Choose any $\alpha \in M(v)$
	3. $F\gets$ `Make-Primed-Fan`$(v, x_0, \alpha)$
	4. `Activate-c-Fan`$(F)$.

#### Make-Primed-Fan

The basic idea is to greedily add leaves to the fan until we can prime it.

1. `Make-Primed-Fan`$(v, x_0, \alpha)$
	1. $F\gets (\alpha, v, x_0)$
	2. $k\gets 0$
	3. `while` $F$ is not primed:
		1. Pick any $\beta \in M(x_k)$
		2. `if` $\beta \in M(v)$ `then` Prime $F$ with $\beta$ and `return`
		3. `else`:
			1. Find neighbor $x_{k+1}$ such that $c(vx_{k+1}) = \beta$
			2. `if` $x_{k+1} \in \{x_1, \ldots, x_k\}$ `then` Prime $F$ with $\beta$ and `return`
			3. `else`:
				1. Append $x_{k+1}$ to $F$
				2. $k\gets k+1$

We claim this returns a primed c-Fan in $O(d(v))$ time. Each execution of the outermost loop either primes $F$ or adds a vertex to the fan. No vertex can be added twice, so we have $O(d(v))$ executions of the loop. Each operation in the loop takes $O(1)$ time: we keep track of $M(v)$ for all $v$ at all times, so we can quickly grab a color from it; finding the neighbor $x_{k+1}$ of $v$ colored $\beta$ takes $O(1)$ time by our implementation of the dictionary data structure. We can make the step where we check to see if $x_{k+1}$ is already in the fan take $O(1)$ time by marking the leaves we add to the fan.

#### Activate c-Fan

Here we take a primed c-fan and use it to extend our partial coloring. If the color doing the priming is missing at both $x_k$ and $v$, then we just shift $F$ from $x_k$, thereby un-coloring $vx_k$. Then color $vx_k$ with $\beta$. Otherwise, there's some leaf $x_j$ with $vx_j$ colored $\beta$. Consider the $\alpha/\beta$-path, $P$, through $v$. Since $\alpha$ is missing at $v$ and $vx_j$ is colored $\beta$, it must be the case that $v$ is an endpoint of $P$. The path $P$ must end at some $w$, which is missing exactly one of $\alpha$ or $\beta$. Toggle the colors of the edges in $P$. Now $vx_j$ is colored $\alpha$ and $\beta$ is missing at $v$. An analogous situation happens at $w$. The set of missing colors doesn't change anywhere else. Now:
- If $w\neq x_{j-1}$ then $\beta$ is still missing at $x_{j-1}$. In this case, $F' = (\beta, v, x_0, \ldots, x_{j-1})$ is a c-fan, which we shift from $x_{j-1}$ and color $vx_{j-1}$ with $\beta$.
- If $w = x_{j-1}$ then $\beta$ is no longer missing at $x_{j-1}$, but $\alpha$ is missing instead and $\beta$ is missing at $v$. Consequently, $F' = (\beta, v, x_0, \ldots, x_k)$ is a c-fan. Since $\beta$ is still missing at $x_k$, we can shift $F'$ from $x_k$ and color $vx_k$ with $\beta$.

1. `Activate-c-Fan`$(F, \beta)$ (here, $F$ is primed by $\beta$)
	1. `if` $\beta\in M(v)$:
		1. Shift $F$ from $x_k$
		2. Color $vx_k$ with $\beta$
	2. `else`:
		1. Let $x_j$ be the leaf of $F$ with $c(vx_j) = \beta$
		2. Toggle the $\alpha/\beta$-path $P = v\ldots w$ beginning at $v$
		3. `if` $w\neq x_{j-1}$:
			1. Shift $F$ from $x_{j-1}$
			2. Color $vx_{j-1}$ with $\beta$
		4. `else`:
			1. Shift $F$ from $x_k$
			2. Color $vx_k$ with $\beta$

Let's look at the runtime of this subroutine (it's pretty straightforward that we always extend the coloring and we don't leave anything uncolored). All operations here take $O(d(v))$ time except for the part where we toggle the path $P$, and this takes time $O(|P|)$. Putting it all together, we see that `Color-One` takes time $O(d(v) + |P|)$.

### Random-Color-One

`Color-One` could take time $\Theta(n)$ when the path $P$ is long, even if $d(v)$ is small. One would hope, however, that this isn't often the case and randomization can help here.