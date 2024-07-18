Date Created: 2024-07-12
References: [[Oxley, James - Matroid Theory - 2011]]
Tags: #definition #matroids #in-progress 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Definition

```ad-definition
title: Circuit

If $M = (E, \mathcal I)$ is a [[Matroid#Definition|matroid]], then a minimal dependent subset of $E$ is called a **circuit** of $M$. We let $\mathcal C(M)$ denote the set of circuits of $M$. A circuit of $M$ with $n$ elements is an **$n$-circuit**. 

```

## Properties

If we know the independent sets $\mathcal I$ of a matroid $M$, then we can clearly determine $\mathcal C(M)$. We can go the other way too. If we know $\mathcal C(M)$, then the members of $\mathcal I(M)$ are the subsets of $E(M)$ that contain no member of $\mathcal C(M)$. So a matroid is determined by its circuits too.

Immediate from the definition of a circuit, we have
- (C1): $\emptyset \notin \mathcal C(M)$
- (C2): If $C_1$ and $C_2$ are circuits and $C_1\subseteq C_2$, then $C_1 = C_2$.

How do we invert the augmentation axiom?

## Circuit Elimination

```ad-proposition
title: Circuit Elimination

If $M$ is a matroid, then the set of circuits of $M$ has the following property:
- (C3): If $C_1$ and $C_2$ are distinct elements of $C$ and $e\in C_1 \cap C_2$, then there is a circuit $C_3$ such that $C_3 \subseteq (C_1 \cup C_2)\setminus e$.
```

*Proof.* Say $(C_1 \cup C_2)\setminus e$ didn't contain a circuit. Then it would be in $\mathcal I$. By (C2) there is some $f$ in $C_2 \setminus C_1$ and by minimality, $C_2 \setminus f$ is in $\mathcal I$. Now take a subset $I$ of $C_1 \cup C_2$ that is maximal with respect to the properties that it contains $C_2 \setminus f$ and is independent. We definitely have $f\notin I$, since then $I$ would contain the circuit $C_2$. Now since $C_1$ is a circuit, it must have some element $g$ that is not in $I$. Since $f\in C_2\setminus C_1$, we have that $f\neq g$ and
$$
|I| \leq |(C_1 \cup C_2)\setminus \{f,g\}| = |C_1\cup C_2| - 2 < |(C_1\cup C_2)\setminus e|.
$$
Now by the independent set augmentation axiom of matroids, we can add something from $(C_1\cup C_2) \setminus e$ to $I$ to get a new independent set. But this would contradict the maximality of $I$.


## Circuit Characterization of Matroids

```ad-theorem
title: Circuit characterization of matroids

Let $E$ be a finite set and $\mathcal C$ a collection of sets satisfying
- (C1): $\emptyset \notin \mathcal C(M)$;
- (C2): If $C_1$ and $C_2$ are circuits and $C_1\subseteq C_2$, then $C_1 = C_2$;
- (C3): If $C_1$ and $C_2$ are distinct elements of $C$ and $e\in C_1 \cap C_2$, then there is a circuit $C_3$ such that $C_3 \subseteq (C_1 \cup C_2)\setminus e$.

Let $\mathcal I$ be the collection of subsets of $E$ that contain no member of $\mathcal C$. Then $(E, \mathcal I)$ is a matroid having $\mathcal C$ as its collection of circuits.
```

*Proof.* By (C1) $\emptyset$ isn't in $\mathcal C$, so it contains no member of $\mathcal C$ and is thus in $\mathcal I$. If $I\in \mathcal I$ contains no element of $\mathcal C$ and $I' \subseteq I$, then $I'$ also contains no member of $\mathcal C$, so $I' \in \mathcal I$.

Now say $I_1$ and $I_2$ are in $\mathcal I$ with $|I_1| < |I_2|$. Say we couldn't augment $I_1$ with anything in $I_2$. The collection $\mathcal I$ has a subset of $I_1\cup I_2$ with more elements than $I_1$ (namely $I_2$). Let $I_3$ be such a subset for which $|I_1\setminus I_3|$ is minimal (this minimum is nonzero, otherwise $I_3$ would be an augmentation of $I_1$ by $I_2$). Take $e \in I_1\setminus I_3$. For every $f \in I_3 \setminus I_1$ (which is nonempty - $I_3$ has more elements than $I_1$ so it's not contained in $I_1$), let $T_f$ be $(I_3 \cup e)\setminus f$. Now $T_f\subseteq I_1\cup I_2$ and $|I_1 \setminus T_f| <|I_1 \setminus I_3|$ (we put $e$ in and took $f$ out). By the minimality of $I_3$, $T_f \notin \mathcal I$, so $T_f$ contains a member $C_f$ of $\mathcal C$. By definition of $T_f$, we have that $f\notin C_f$. We also have that $e\in C_f$, because otherwise $C_f \subseteq I_3$, contradicting the assumption that $I_3 \in \mathcal I$.

Now take $g\in I_3 \setminus I_1$. If $C_g \cap (I_3 \setminus I_1) = \emptyset$ then $C_g \subseteq ((I_1 \cap I_3) \cup e)\setminus g \subseteq I_1$, which would be a contradiction since independent sets don't contain circuits. So there must be some $h \in C_g \cap (I_3 \setminus I_1)$ with $C_g \neq C_h$ since $h\notin C_h$. But we do have $e\in C_g\cap C_h$, so by (C3) there is some circuit $C$ with $C\subseteq (C_g \cup C_h)\setminus e$. However, $C_g$ and $C_h$ are contained in $I_3 \cup e$, so $C\subseteq I_3$, a contradiction. So we conclude that we have independent set augmentation and $(E, \mathcal I)$ is a matroid $M$.

Now we need to show that $\mathcal C$ is the set of circuits of $M$. Note that the following are equivalent.
- $C$ is a circuit of $M$;
- $C\notin \mathcal I(M)$ but $C\setminus x \in \mathcal I(M)$ for all $x\in C$;
- $C$ has some $C' \in \mathcal C$ as a subset, but $C'$ is not a proper subset of $C$;
- $C\in \mathcal C$.

## Application of circuit elimination

```ad-proposition

Suppose that $I$ is an independent set in matroid $M$ and $e$ is an element of $E(M)$ such that $I\cup e$ is dependent. Then there is a unique circuit of $M$ contained in $I\cup E$ and this circuit contains $e$.
```

*Proof.* Since $I\cup e$ is dependent, it must contain a circuit. Any such circuit must contain $e$, since otherwise, it would just be contained in $I$, contradicting the assumption that $I$ was independent. If $C$ and $C'$ were distinct such circuits, then there would be some third circuit $C''$ contained in $(C\cup C')\setminus e$. But $(C\cup C')\setminus e$ is contained in $I$, which contradicts the independence of $I$.