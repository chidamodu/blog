---
published: false
---
# Linked List

A linked list is a data structure that comprises a sequence of nodes that are connected by links. In simplest terms, a linked list is a chain of nodes. So what’s a node, you ask?

A node as the fundamental block is an atomic data structure of the linked list. It consists of the following basic components:
	1.Data component which stores value at the node.
	2.Link component that acts as a reference to the next node.

A simple node consists of one data block and a single reference to another node. 



<img src="http://chidamodu.github.io/blog/images//singly linked list.png">



The node on the far left represents the head of the linked list and as the first element, it plays an integral role in referring to the entire list. In other words, we return the head if we ought to return the entire linked list. The last node, 5 refers to a black dot to demonstrate that the last node does not refer to any other node, and therefore the reference component of the node, 5 has a Null value, i.e., in python it is None. The linked list above is also called a singly linked list to demonstrate its unidirectional type that it can be traversed only in one direction starting from the head (left) of the linked list to the tail (right), i.e., the last node.
