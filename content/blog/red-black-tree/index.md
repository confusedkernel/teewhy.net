---
title: Red-Black Tree
description: On how to implement a red-black tree in C.
authors:
- name: Tyler
tags:
- dsm
categories:
- comp sci
date: 2023-11-20T23:15:44+08:00
draft: false
readingTime: true
toc: true
---
{{< callout type="info" >}}
  I'm writing this to help me understand red-black trees better. Don't hesitate to reach out if there are any mistakes in this article!
{{< /callout >}}

The red-black tree and the binary search tree are both basic data structures. They're both commonly used binary tree structures, except the red-black tree is a tad bit *quirkier* than the binary search tree.

A binary search tree is straightforward. The left subtree of each node contains values smaller than the node, and the right subtree contains values greater than the node, making search operations more efficient. While a binary search tree is easier to implement, its structure may cause the tree to be unbalanced. In extreme cases, binary search trees could degenerate into a linear structure. The red-black tree fixes this flaw by introducing colors to each node and performing a self-balancing act with a specific set of rules to ensure the shape and performance of the tree.

## Properties of Red-Black Tree

There are five rules of red-black tree that cannot be violated:
1. The root is always black
2. Every leaf (NIL) is black
3. The children of a red node are black
4. Every path from a node to any of its children has the same number of black nodes
5. All the leaves have the same black depth

## Time Complexity

   Operation | Time Complexity
-------------|-----------------
    Search   | O(log n)
    Insert   | O(log n)
    Delete   | O(log n)

## Struct Definition
```c {filename = "bst.c"}
typedef struct Node {
	int value;
	int color; // 1 = red, 0 = black
	struct Node *parent;
	struct Node *left;
	struct Node *right;
} Node;
```

## Insertion

Since the red-black tree is derived from the normal binary search tree, we need to do a basic bst insertion as the base operation:

```c {filename = "rbt.c"}
Node *insert(Node *tree, Node *temp) {
	if(tree == NULL) return temp;

	if(temp->value < tree->value) {
		tree->left = insert(tree->left, temp);
		tree->left->parent = tree;
	}
	else if(temp->value > tree->value) {
		tree->right = insert(tree->right, temp);

tree->right->parent = tree;
	}
	insert_fixup(tree, temp);
	return tree;
}
```
As we mentioned before, the red-black tree has self-balancing features that corrects the flaw of a binary search tree. The self-balancing feature is called **fixup**. A balanced red-black tree should satisfy [all five properties of red-black tree](#properties-of-red-black-tree). Especially **rule 3: "The children of a red node are black"** and **rule 4: "Every path from a node to any of its children has the same number of black nodes."** To restore all five properties of it, we'll introduce something called **rotation** and **recoloration**, which will help maintain the balance of the tree.

We try recoloring first, if recoloring doesn’t work, then we go for rotation.

{{% steps %}}

### Step 1

This is the first step

{{% /steps %}}
