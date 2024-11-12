Date Created: 2024-09-24
References: #ref/NONE
Tags: #definition #data-structures #in-progress 

Types: <i>Not Applicable</i>
Examples: <i>Not Applicable</i>
Constructions: <i>Not Applicable</i>
Generalizations: <i>Not Applicable</i>

Properties: <i>Not Applicable</i>
Sufficiencies: <i>Not Applicable</i>
Equivalences: <i>Not Applicable</i>
Justifications: <i>Not Applicable</i>

## Linked list

```ad-definition
title: Linked List

A **linked list** `L` is a collection of objects `x`, each of which has two fields:
- `x.value`: the value stored in `x`
- `x.next`: a pointer to the next item in the list.

If `x.next` is `null`, then `x` is the **tail** of the list. Sometimes we consider `L` to come with pointers `L.head` and `L.tail`.

```

## Doubly-linked list

```ad-definition
title: Doubly-Linked List

A **doubly-linked list** `L` is a collection of objects `x`, each of which has three fields:
- `x.value`: the value stored in `x`
- `x.prev`: a pointer to the previous item in the list
- `x.next`: a pointer to the next item in the list.

If `x.prev` is `null`, then $x$ is the **head** of `L`. Similarly, if `x.next` is `null`, then `x` is the **tail** of the list. Sometimes we consider `L` to come with pointers `L.head` and `L.tail`.

```