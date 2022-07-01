# A.1.6: Trees

## Learning Objectives

1. Trees are collections of nodes connected by uni-directional edges without cycles
2. Trees store hierarchical data and are commonly used for applications such as file systems, nested UI representation, search and language processing
3. There are 2 common tree traversal algorithms: depth-first search (DFS) and breadth-first search (BFS)
4. Within DFS there are 3 orders of traversing nodes: pre-order, in-order and post-order
5. TODO: Time and space complexity?
6. TODO: Include binary search trees

## Introduction

{% embed url="https://youtu.be/qH6yxkw0u78" %}
Simple whiteboard introduction to trees
{% endembed %}

![Sample computer science tree. The node outlined in red is the root node. Source: Wikipedia](<../../.gitbook/assets/A.1.6 - Trees.png>)

Trees are collections of nodes connected by uni-directional edges with no cycles. They are typically drawn from top to bottom as in the image above. For any 2 connected nodes, the source node is called the "parent" and the target node is called the "child". Nodes with no children are called "leaf" nodes. Each node typically has a payload, which is often a number in algorithm problems but can be anything in practical problems, such as folder names or React components.

Trees store hierarchical data and are commonly used for application such as file systems (think the folder structure in terminal), nested UI representation (think React component hierarchy), search (think dictionary or encyclopaedia search), and language processing (imagine a tree representing common word orders). They are not uncommon algorithm problems, which is why we are learning them now.&#x20;

## Example Tree Initialisation Code

### Binary Tree

The following tree node definition is for binary trees, the most common kind of tree we will encounter in algorithm problems. Binary trees have at at most 2 children per parent, and we generally refer to the children as left and right nodes.

```javascript
// Binary tree node definition
class Node {
  constructor(val) {
    // The node value is stored in an attribute called val
    this.val = val;
    // Initialise left and right child nodes to null
    this.left = null;
    this.right = null;
  }
}

// Initialise a binary tree and populate its nodes
const root = new Node(3);
root.left = new Node(1);
root.right = new Node(2);
root.left.left = new Node(3);
root.left.right = new Node(4);
root.right.left = new Node(5);
root.right.right = new Node(3);

// The resulting tree should look like the following
//      3
//    /   \
//   1     2
//  / \   / \
// 3   4 5   3
```

### Binary Search Tree

TODO: Update BST introduction

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

### Generic Tree

The following tree node definition is for a generic tree with no limit to the number of child nodes per parent. These are less common but occasionally seen in algorithm problems.

```javascript
// Generic tree node definition
class Node {
  constructor(val) {
    // The node value is stored in an attribute called val
    this.val = val;
    // Store children in array, starting with empty array when no children
    this.children = [];
  }
}
```

## Tree Traversal

Most tree algorithm problems involve traversing (i.e. going through) the nodes in a tree and calculating a result, for example summing the value of nodes, finding a specific value in the tree, or determining if a tree is balanced (equal nodes on left and right).

There are 2 common forms of tree traversal: depth-first search (DFS) and breadth-first search (BFS). DFS means traversing down every path until we reach a leaf node before exploring other paths. BFS means traversing all nodes at each level of depth (distance from root node) before proceeding to the next level of depth. DFS is simpler and more common. BFS is more specialised for certain kinds of problems such as finding the shortest path in a tree.

{% embed url="https://youtu.be/9RHO6jU--GU" %}
Overview of BFS, DFS and the 3 permutations of DFS
{% endembed %}

## Depth-First Search (DFS)

DFS is the default form of tree traversal and we typically implement DFS with recursion.

![Illustration of DFS. Source: Viva Differences](<../../.gitbook/assets/A.1.6 - Trees - DFS.png>)

### Example: Find `x` in tree

The following code uses DFS to find value `x` in a tree. The algorithm returns `true` if `x` exists in the tree and `false` if not.

```javascript
// The initial call to findXInTree passes in the root node
const findXInTree = (node, x) => {
  // If recursion reaches child of leaf node, x was not found
  if (!node) {
    return false;
  }
  // If current node has value x, x is found
  if (node.val === x) {
    return true;
  }
  // Return true if x is in the left or right subtrees of node, false otherwise
  return findXInTree(node.left, x) || findXInTree(node.right, x); 
}
```

Notice the algorithm looks like many of the recursive algorithms we have written before, with base cases and recurrence relations. DFS algorithms typically examine the current node in the base cases and pass child nodes to the recursive functions in recurrence relations.

The above algorithm has a time complexity of `O(n)`, where `n` is the number of nodes in the tree. This is because the algorithm will need to visit at most all nodes in the tree to find `x`. This algorithm has a space complexity of `O(1)` because it does not allocate any additional memory beyond what is provided.

### Pre-Order, In-Order and Post-Order Traversal

Certain DFS problems are better solved if we can manipulate the order in which we traverse nodes. The following 3 traversals are variants of DFS that determine the order in which we traverse left child, parent, and right child nodes. All 3 traversals assume we are traversing a binary tree.

#### **Pre-Order Traversal**

Pre-Order Traversal implies visiting nodes in the following order. This is helpful in situations such as searching a binary search tree, because we will need to inspect the parent first to determine whether the value we are looking for is in the left or right subtree.

1. Parent
2. Left Child
3. Right Child

```javascript
const preOrderTraversal = (node) => {
  // 1) Check parent
  if (node.val) {
    // Return something
    return;
  }

  // 2) Check left child
  preOrderTraversal(node.left);

  // 3) Check right child
  preOrderTraversal(node.right);
}
```

#### In-Order Traversal

In-Order Traversal implies visiting nodes in the following order. This is helpful in situations such as printing the values in a binary search tree in ascending order.

1. Left Child
2. Parent
3. Right Child

```javascript
const inOrderTraversal = (node) => {
  // 1) Check left child
  inOrderTraversal(node.left);

  // 2) Check parent
  if (node.val) {
    // Return something
    return;
  }

  // 3) Check right child
  inOrderTraversal(node.right);
}
```

#### Post-Order Traversal

Post-Order Traversal implies visiting nodes in the following order. This is helpful in situations where we might want to operate on all leaf nodes before their parents, for example when deleting nodes in a tree.

1. Left Child
2. Right Child
3. Parent

```javascript
const postOrderTraversal = (node) => {
  // 1) Check left child
  postOrderTraversal(node.left);

  // 2) Check right child
  postOrderTraversal(node.right);

  // 3) Check parent
  if (node.val) {
    // Return something
    return;
  }
}
```

## Breadth-First Search (BFS)

![Illustration of DFS. Source: Viva Differences](<../../.gitbook/assets/A.1.6 - Trees - BFS.png>)

### Example: Return tree values in level order

TODO: Clean up explanation and change code example to JS

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

## Additional Resources

1. Read pages 111-114 (book pages 100-103) in the [Cracking the Coding Interview PDF](https://drive.google.com/file/d/1M3uvavrprW\_xmbSFHAe3Q4RgfgFwEfwy/view?usp=sharing)
2. [FTBC3's class video](https://youtu.be/3Dw3spVIk1w?t=297) when we introduced trees

## Exercises

TODO: Review all exercises, update Repl exercises to JS, include HackerRank exercises, update exercise listing format to match prev algos submodules

Note: The following exercises are sorted in increasing order of difficulty, and organised in groups to help us keep track of milestones. Please do as many as you can during Bootcamp and feel free to complete the rest at a later time.

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

Tree (and Linked List) problems will often say that the tree is passed as a parameter to our function. What they mean by this is that the root or head node of the tree or linked list respectively is passed to the function. The tree is represented by the root node, which can be used to access all other nodes in the tree.

### Pre-Class

1. [https://repl.it/@rocketkai/treeintro#main.py](https://repl.it/@rocketkai/treeintro#main.py)
   1. [https://repl.it/@rocketkai/treeintrosoln#main.py](https://repl.it/@rocketkai/treeintrosoln#main.py)
   2. [FTBC3 class video ](https://youtu.be/3Dw3spVIk1w?t=3001)where we solved the 1st 2 problems together.

### Part 1

1. [https://repl.it/@rocketkai/treetraversals#main.py](https://repl.it/@rocketkai/treetraversals#main.py)
   1. Hint: Level-order traversal requires BFS techniques that are not recursive.
   2. [https://repl.it/@rocketkai/treetraversals-soln#main.py](https://repl.it/@rocketkai/treetraversals-soln#main.py)

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

See [Pre-Order, In-Order, and Post-Order section](a.1.6-trees.md#pre-order-in-order-and-post-order-traversal) above for a recap on the various traversal orderings. For non-binary trees that can have more than 2 children, when we iterate through an array of children we are typically iterating from left to right children.

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
   2. Kai also explained binary numbers in a [prior FTBC3 class here](https://youtu.be/qewAXA\_vkpE?t=2372).
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
   2. [Solution video](https://youtu.be/AMpseCEX6\_A?t=2147) from FTBC3's class
8. [https://leetcode.com/problems/cousins-in-binary-tree/](https://leetcode.com/problems/cousins-in-binary-tree/)
   1. Rocket Academy solution code: [https://pastebin.com/wWYXg309](https://pastebin.com/wWYXg309)
   2. Rocket Academy video solution: [https://youtu.be/SeNfZBAU\_f4?t=4088](https://youtu.be/SeNfZBAU\_f4?t=4088)
9. [https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)
10. [https://leetcode.com/problems/binary-tree-right-side-view/](https://leetcode.com/problems/binary-tree-right-side-view/) (Medium)
11. [https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) (Medium)

## Binary Search Tree Exercises

See pre-order and in-order tree traversal.

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Pre-Class

1. [https://repl.it/@rocketkai/treebst#main.py](https://repl.it/@rocketkai/treebst#main.py)
   1. [https://repl.it/@rocketkai/treebstsoln#main.py](https://repl.it/@rocketkai/treebstsoln#main.py)

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
