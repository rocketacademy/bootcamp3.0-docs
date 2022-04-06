# A.5.6: Trees

![](../../../.gitbook/assets/trees.jpeg)

## Introduction

Trees are a common data structure used to represent hierarchical data, often seen in DS\&A problems. Trees are essentially linked lists where nodes are oriented from top to bottom instead of left to right, and each node can have more than 1 subsequent node, called **"child nodes"** in trees. Each child node can only have 1 **"parent node"**, and nodes with no child nodes are called **"leaf nodes"**. Nodes in trees generally contain a data payload (e.g. a number), and pointers to each respective child node.

## Tree Example

```
class Node:
  def __init__(self, value):
    self.value = value
    self.left = None
    self.right = None

# Creating a binary tree
root0 = Node(3)
root0.left = Node(1)
root0.right = Node(2)
root0.left.left = Node(3)
root0.left.right = Node(4)
root0.right.left = Node(5)
root0.right.right = Node(3)
#      3
#    /   \
#   1     2
#  / \   / \
# 3   4 5   3

print(root0)
```
