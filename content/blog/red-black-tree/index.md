---
title: Red-Black Tree
description: On how to implement a red-black tree in C.
authors:
- name: Tyler
tags:
- dsm
categories:
- comp sci
date: 2024-03-27T23:15:44+08:00
draft: false
readingTime: true
toc: true
---
{{< callout type="info" >}}
If you think this article is a bit empty... It's because it is. I'm still writing and adding more details to it!
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

To insert a node onto the red-black tree, we will first perform a standard BST insertion, and color the inserted node in red.

As we mentioned before, the red-black tree has self-balancing features that corrects the flaw of a binary search tree. The self-balancing feature is called **fixup**. A balanced red-black tree should satisfy [all five properties of red-black tree](#properties-of-red-black-tree). Especially **rule 3: "The children of a red node are black"** and **rule 4: "Every path from a node to any of its children has the same number of black nodes."** To restore all five properties of it, we'll introduce something called **rotation** and **recoloration**, which will help maintain the balance of the tree.

To balance a tree, we should try recoloring the nodes first before performing rotations. Here is how we insert and recolor:

{{% steps %}}

### BST Insertion
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

### Fixup

```c {filename = "rbt.c"}
void insert_fixup(Node *root, Node *issue) {
	Node *daddy_issue = NULL;
	Node *grandpa_issue = NULL;

	while(issue != root && issue->color != 0 && issue->parent->color == 1) {
		daddy_issue = issue->parent;
		grandpa_issue = issue->parent->parent;

		if(daddy_issue == grandpa_issue->left) {
			Node *uncle_issue = grandpa_issue->right;

			if(uncle_issue != NULL && uncle_issue->color == 1) {
				grandpa_issue->color = 1;
				daddy_issue->color = 0;
				uncle_issue->color = 0;
				issue = grandpa_issue;
			}
			else {
				if(issue == daddy_issue->right) {
					left_rotate(daddy_issue);
					issue = daddy_issue;
					daddy_issue = issue->parent;
				}

				right_rotate(grandpa_issue);
				int tmp = daddy_issue->color;
				grandpa_issue->color = tmp;
				issue = daddy_issue;
			}
		}
		else {
			Node *uncle_issue = grandpa_issue->left;

			if(uncle_issue != NULL && uncle_issue->color == 1) {
				grandpa_issue->color = 1;
				daddy_issue->color = 0;
				uncle_issue->color = 0;
				issue = grandpa_issue;
			}
			else {
				if(issue == daddy_issue->left) {
					right_rotate(daddy_issue);
					issue = daddy_issue;
					daddy_issue = issue->parent;
				}

				left_rotate(grandpa_issue);
				int tmp = daddy_issue->color;
				daddy_issue->color = grandpa_issue->color;
				grandpa_issue->color = tmp;
				issue = daddy_issue;
			}
		}
	}
}
```

### Rotation

```c {filename = "rbt.c"}
void right_rotate(Node *temp) {
	Node *left = temp->left;
	temp->left = left->right;
	if(temp->left) {
		temp->left->parent = temp;
	}
	left->parent = temp->parent;
	if(!temp->parent) {
		root = left;
	}
	else if(temp == temp->parent->left) {
		temp->parent->left = left;
	}
	else {
		temp->parent->right = left;
	}
	left->right = temp;
	temp->parent = left;
}
```

```c {filename = "rbt.c"}
void left_rotate(Node *temp) {
	Node *right = temp->right;
	temp->right = right->left;
	if(temp->right) {
		temp->right->parent = temp;
	}
	right->parent = temp->parent;
	if(!temp->parent) {
		root = right;
	}
	else if(temp == temp->parent->left) {
		temp->parent->left = right;
	}
	else {
		temp->parent->right = right;
	}
	right->left = temp;
	temp->parent = right;
}
```

{{% /steps %}}

> I'm still updating this article, but you can find the sample code on my GitHub Gist [here](https://gist.github.com/nottyl/9cce62fcbc9253b69bcbf25e9448b52c).

## Leave a Comment!

{{< chat red-black-tree >}}
