# A.5.6.2: Binary Search Trees

## Learning Objectives

By the end of this lesson, you should:

* be familiar with what a binary search tree data structure is

## Introduction

Binary search trees are commonly used for indexing and lookup- binary search trees are the data structure used in database indexes to speed up the querying of data.

Binary Search Trees or BSTs are a special kind of tree where each node has the following properties.

1. All nodes in the left subtree (subtree that extends from the parent node's left child) have values smaller than the parent node.
2. All nodes in the right subtree (subtree that extends from the parent node's right child) have values larger than the parent node.

These properties are especially useful for search algorithms, because given relatively "balanced" BSTs we will be able to search for elements in BSTs in `O(log(n))` time. [Read more about BSTs here](https://www.geeksforgeeks.org/binary-search-tree-data-structure/).

```
class Node:
  def __init__(self, val):
    self.value = val
    self.left = None
    self.right = None
  def __repr__(self):
    return str(self.value)

# Creating a BST
root = Node(5)
root.left = Node(3)
root.right = Node(8)
root.right.left = Node(7)
#   5
#  / \
# 3   8
#    /
#   7
```

## Traversal

See pre-order and in-order tree traversal.

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Pre-Class

1. [https://repl.it/@kaiyuanneo/treebst#main.py](https://repl.it/@kaiyuanneo/treebst#main.py)
   1. [https://repl.it/@kaiyuanneo/treebstsoln#main.py](https://repl.it/@kaiyuanneo/treebstsoln#main.py)

### Part 1

1. [https://leetcode.com/problems/univalued-binary-tree/](https://leetcode.com/problems/univalued-binary-tree/)
2. [https://leetcode.com/problems/search-in-a-binary-search-tree/](https://leetcode.com/problems/search-in-a-binary-search-tree/)
3. [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
   1. FTBC3 class video discussion on solution and how to trace code in a recursion problem: [https://youtu.be/uQldubu1LOE?t=2269](https://youtu.be/uQldubu1LOE?t=2269)

### Part 2

1. [https://leetcode.com/problems/maximum-depth-of-n-ary-tree/](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)
   1. Hint: Review [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) problem before attempting this one.
   2. [FTBC class video discussion](https://youtu.be/L2gtfJBxKzE?t=5329)

### Part 3

1. [https://leetcode.com/problems/minimum-depth-of-binary-tree/](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
2. [https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)
3. [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
