# A.5.6.1: Tree Traversal

## Learning Objectives

By the end of this lesson, you should:

- be familiar with what a tree data structure is
- understand the python implementation of a tree data structure
- be familiar with the different tree traversal algorithms
- be familiar with the time and space complexity of tree traversal algorithms

## Introduction

Now that we understand what a tree is, we need to _use_ it. In the context of the tree data structure that means going through the values in the tree, or **traversal** of the tree. Computer science defines only a few standard ways for an algorithm to move through a tree. The purpose of the algorithm could be a few things: to count the number of items in a tree, to find something in the tree, to look at every item in the tree, etc. In this section we'll detail the different ways we can do these actions.

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

## Helpful Resources

1. [This](https://www.youtube.com/watch?v=qH6yxkw0u78) video is a clear and concise intro to basic concepts regarding trees.
2. Read pages 112-115 in the [Cracking the Coding Interview PDF](../../a.0-algorithms-overview.md#resources).
3. [FTBC3's class video](https://youtu.be/3Dw3spVIk1w?t=297) when we introduced trees.

## Tree Traversals

The 2 most common methods of tree traversal are Depth-First Search (DFS) and Breadth-First Search (BFS). Tree traversal is a crucial technique in using trees to solve problems.

### Depth-First Search (DFS)

![](<../../../.gitbook/assets/image (1).png>)

### Time Complexity: _`O(V+E)`_ where V is all the vertexes in the tree and E are all the edges.

Most vanilla recursion applies DFS. For example, the naive Fibonacci implementation of Fib(n) might solve the entire Fib(n-1) subtree before recursing on Fib(n-2). The following is an example of DFS that returns `True` if the value `x` is within a tree, false if not.

```python
# The initial call to find_x_in_tree passes the root node
def find_x_in_tree(node, x):
  # If recursion reaches child of leaf node, x was not found
  if not node:
    return False
  # If current node has value x, x is found
  if node.val == x:
    return True
  # Return True if x is in the left or right subtrees of node
  return find_x_in_tree(node.left, x) or find_x_in_tree(node.right, x)
```

### Pre-Order, In-Order and Post-Order Traversal

Certain tree problems are better solved if we can manipulate the order in which we traverse nodes. **These 3 traversals are variations on the DFS algorithm** shared above, and determine the order in which we traverse the left child, parent, and right child nodes.

#### **Pre-Order Traversal**

**Pre-Order Traversal** implies visiting nodes in the following order. This is helpful in situations such as searching a binary search tree.

1. Parent
2. Left Child
3. Right Child

```python
def pre_order_traversal(node):
  # 1) Check parent
  if node.val:
    # Return something
    return

  # 2) Check left child
  pre_order_traversal(node.left)

  # 3) Check right child
  pre_order_traversal(node.right)
```

#### In-Order Traversal

**In-Order Traversal** implies visiting nodes in the following order. This is helpful in situations such as printing the values in a binary search tree in ascending order.

1. Left Child
2. Parent
3. Right Child

```python
def in_order_traversal(node):
  # 1) Check left child
  in_order_traversal(node.left)

  # 2) Check parent
  if node.val:
    # Return something
    return

  # 3) Check right child
  in_order_traversal(node.right)
```

#### Post-Order Traversal

**Post-Order Traversal** implies visiting nodes in the following order. This is helpful in situations where we might want to operate on all leaf nodes before their parents, for example when deleting nodes in a tree.

1. Left Child
2. Right Child
3. Parent

```python
def post_order_traversal(node):
  # 1) Check left child
  post_order_traversal(node.left)

  # 2) Check right child
  post_order_traversal(node.right)

  # 3) Check parent
  if node.val:
    # Return something
    return
```

### Breadth-First Search (BFS)

![](../../../.gitbook/assets/image.png)

### Time Complexity: _`O(V+E)`_ where V is all the vertexes in the tree and E are all the edges.

BFS is a fancier form of tree traversal that typically involves queues. As a recap of BFS, consider the following `level_order` traversal solution from Rocket's tree traversal exercises. The following algorithm enables us to access nodes in a tree in level order.

Consider using Python's built-in `deque` data structure [here](https://docs.python.org/3/library/collections.html#collections.deque) for a more efficient queue implementation than `list`. `deque` is implemented with a doubly-linked list, thus dequeue is a O(1) operation. Specifically, see the [`popleft` method](https://docs.python.org/3/library/collections.html#collections.deque.popleft).

```python
from collections import deque

def level_order(root_node):
  ''' Return the list of values level by level (Hint: Consider iteration)'''
  level_order_values = []
  # Store upcoming nodes in a queue
  q = deque([root_node])
  while len(q) > 0:
    # Iteratively dequeue first node in queue until queue is empty
    currnode = q.popleft()
    # Perform operation on current node
    level_order_values.append(currnode.value)
    # Enqueue left child if any
    if currnode.left:
      q.append(currnode.left)
    # Enqueue right child if any
    if currnode.right:
      q.append(currnode.right)
  return level_order_values
```

## Practical Use Cases of Trees

Trees are often used to represent hierarchical data, e.g. HTML elements or React components, and efficient use of trees can help us optimise our applications. Trees can also be used for efficient syntax parsing, for example in programming language compilation.

## General Tips for Tree Problems

1. Tree (and Linked List) problems will often say that the tree is passed as a parameter to our function. What they mean by this is that the root or head node of the tree or linked list respectively is passed to the function. The tree is represented by the root node, which can be used to access all other nodes in the tree.

## Exercises

Note: The following exercises are sorted in increasing order of difficulty, and organised in groups to help us keep track of milestones. Please do as many as you can during Bootcamp and feel free to complete the rest at a later time.

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Pre-Class

1. [https://repl.it/@neokaiyuan/treeintro#main.py](https://repl.it/@neokaiyuan/treeintro#main.py)
   1. [https://repl.it/@neokaiyuan/treeintrosoln#main.py](https://repl.it/@neokaiyuan/treeintrosoln#main.py)
   2. [FTBC3 class video ](https://youtu.be/3Dw3spVIk1w?t=3001)where we solved the 1st 2 problems together.

### Part 1

1. [https://repl.it/@neokaiyuan/treetraversals#main.py](https://repl.it/@neokaiyuan/treetraversals#main.py)
   1. Hint: Level-order traversal requires BFS techniques that are not recursive.
   2. [https://repl.it/@neokaiyuan/treetraversals-soln#main.py](https://repl.it/@neokaiyuan/treetraversals-soln#main.py)

### Part 2

1. [https://leetcode.com/problems/univalued-binary-tree/](https://leetcode.com/problems/univalued-binary-tree/)
2. [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
   1. FTBC3 class video discussion on solution and how to trace code in a recursion problem: [https://youtu.be/uQldubu1LOE?t=2269](https://youtu.be/uQldubu1LOE?t=2269)

### Part 3

1. [https://leetcode.com/problems/maximum-depth-of-n-ary-tree/](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/)
   1. Hint: Review [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) problem before attempting this one.
   2. [FTBC class video discussion](https://youtu.be/L2gtfJBxKzE?t=5329)
2. [https://leetcode.com/problems/minimum-depth-of-binary-tree/](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
3. [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)
   1. FTBC3 class video discussion on solution and runtime: [https://youtu.be/uQldubu1LOE?t=1709](https://youtu.be/uQldubu1LOE?t=1709)

### Part 4

See [Pre-Order, In-Order, and Post-Order section](./#pre-order-in-order-and-post-order-traversal) above for a recap on the various traversal orderings. For non-binary trees that can have more than 2 children, when we iterate through an array of children we are typically iterating from left to right children.

1. [https://leetcode.com/problems/n-ary-tree-postorder-traversal/](https://leetcode.com/problems/n-ary-tree-postorder-traversal/)
2. [https://leetcode.com/problems/n-ary-tree-preorder-traversal/](https://leetcode.com/problems/n-ary-tree-preorder-traversal/)
3. [https://leetcode.com/problems/increasing-order-search-tree/](https://leetcode.com/problems/increasing-order-search-tree/)
   1. Hint: Consider in-order traversal to traverse a binary search tree in increasing order.

### Part 5

1. Hint: Review [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) problem before attempting this one.
2. [FTBC3 In-Class Discussion Part 1](https://youtu.be/L2gtfJBxKzE?t=4412)
3. [FTBC3 In-Class Discussion Part 2](https://youtu.be/L2gtfJBxKzE?t=6278)
4. [https://leetcode.com/problems/find-mode-in-binary-search-tree/](https://leetcode.com/problems/find-mode-in-binary-search-tree/)
5. [https://leetcode.com/problems/path-sum/](https://leetcode.com/problems/path-sum/)
   1. Rocket solution code: [https://pastebin.com/wu9Xn6b3](https://pastebin.com/wu9Xn6b3)
   2. FTBC class video solution: [https://youtu.be/DUxsg2iDtuE?t=1226](https://youtu.be/DUxsg2iDtuE?t=1226)

### Part 6

1. [https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)
   1. Here's an [intuitive explanation of binary numbers](https://www.mathsisfun.com/binary-number-system.html).
   2. Kai also explained binary numbers in a [prior FTBC3 class here](https://youtu.be/qewAXA_vkpE?t=2372).
2. [https://leetcode.com/problems/two-sum-iv-input-is-a-bst/](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)
3. [https://leetcode.com/problems/range-sum-of-bst/](https://leetcode.com/problems/range-sum-of-bst/)
   1. Rocket solution code (naive solution without pruning): [https://pastebin.com/5eGrpPSq](https://pastebin.com/5eGrpPSq)
   2. [Solution video](https://youtu.be/3Dw3spVIk1w?t=4579) from FTBC3's class

### Part 7

1. [https://leetcode.com/problems/merge-two-binary-trees/](https://leetcode.com/problems/merge-two-binary-trees/)
2. [https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)
3. [https://leetcode.com/problems/leaf-similar-trees/](https://leetcode.com/problems/leaf-similar-trees/)

### More Comfortable

1. [https://leetcode.com/problems/sum-of-left-leaves/](https://leetcode.com/problems/sum-of-left-leaves/)
2. [https://leetcode.com/problems/subtree-of-another-tree/](https://leetcode.com/problems/subtree-of-another-tree/)
3. [https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)
   1. Hint: Consider starting in the middle of the array and using recursion.
4. [https://leetcode.com/problems/binary-tree-paths/](https://leetcode.com/problems/binary-tree-paths/)
   1. Hints
      1. Each time we reach a leaf node, we've explored a valid path.
      2. How can we keep track of the path up to each leaf node such that when we reach a leaf node in our recursion, we can add that path to the list of valid paths? Do we need an additional input parameter to our recursive function, i.e. a recursive helper function for this?
      3. Where can we store our list of valid paths? Should it be inside or outside of our recursive helper function?
   2. [FTBC3 class video discussion on algorithm](https://youtu.be/uQldubu1LOE?t=5355) and how to write helper function for recursion problems to pass additional parameter to recursive children.
   3. [Leetcode reference solution](https://leetcode.com/problems/binary-tree-paths/discuss/1357824/Python-3-DFS-With-Backtracking) from Leetcode Discuss tab
5. [https://leetcode.com/problems/average-of-levels-in-binary-tree/](https://leetcode.com/problems/average-of-levels-in-binary-tree/)
   1. Hint: BFS
6. [https://leetcode.com/problems/minimum-absolute-difference-in-bst/](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)
   1. Hint: The minimum absolute distance in a tree with root node `root` is the minimum of the following 4 values.
      1. `minAbsDist(root.left)`
      2. `minAbsDist(root.right)`
      3. `abs(root.val - maxValInLeftSubtree)`
      4. `abs(root.val - minValInRightSubtree))`
7. [https://leetcode.com/problems/symmetric-tree/](https://leetcode.com/problems/symmetric-tree/)
   1. Rocket solution code: [https://pastebin.com/a2buQJxv](https://pastebin.com/a2buQJxv)
   2. [Solution video](https://youtu.be/AMpseCEX6_A?t=2147) from FTBC3's class
8. [https://leetcode.com/problems/cousins-in-binary-tree/](https://leetcode.com/problems/cousins-in-binary-tree/)
   1. Rocket Academy solution code: [https://pastebin.com/wWYXg309](https://pastebin.com/wWYXg309)
   2. Rocket Academy video solution: [https://youtu.be/SeNfZBAU_f4?t=4088](https://youtu.be/SeNfZBAU_f4?t=4088)
9. [https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)
10. [https://leetcode.com/problems/binary-tree-right-side-view/](https://leetcode.com/problems/binary-tree-right-side-view/) (Medium)
11. [https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) (Medium)
