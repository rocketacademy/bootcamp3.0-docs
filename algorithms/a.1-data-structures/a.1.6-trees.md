# A.1.6: Trees

## Learning Objectives

1. Trees are collections of nodes connected by uni-directional edges without cycles
2. Trees store hierarchical data and are commonly used for applications such as file systems, nested UI representation, search and language processing
3. Binary trees and binary search trees are the most common trees in algorithm problems
4. There are 2 common tree traversal algorithms: depth-first search (DFS) and breadth-first search (BFS)
5. Within DFS there are 3 orders of traversing nodes: pre-order, in-order and post-order

## Introduction

{% embed url="https://youtu.be/qH6yxkw0u78" %}
Simple whiteboard introduction to trees
{% endembed %}

![Sample computer science tree. The node outlined in red is the root node. Source: Wikipedia](<../../.gitbook/assets/A.1.6 - Trees.png>)

Trees are collections of nodes connected by uni-directional edges with no cycles. They are typically drawn from top to bottom as in the image above. For any 2 connected nodes, the source node is called the "parent" and the target node is called the "child". Nodes with no children are called "leaf" nodes. Each node typically has a payload, which is often a number in algorithm problems but can be anything in practical problems, such as folder names or React components.

Trees store hierarchical data and are commonly used for application such as file systems (think the folder structure in terminal), nested UI representation (think React component hierarchy), search (think dictionary or encyclopaedia search), and language processing (imagine a tree representing common word orders). They are not uncommon algorithm problems, which is why we are learning them now.&#x20;

## Tree Types and Initialisation Code

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

![Sample binary search tree. Source: Wikipedia](<../../.gitbook/assets/A.1.6 - Trees - BST.png>)

Binary search trees (BSTs) are binary trees where every node has the following properties:

1. All nodes in the left subtree (subtree that extends from the parent node's left child) have values smaller than the parent node
2. All nodes in the right subtree (subtree that extends from the parent node's right child) have values larger than the parent node

These properties are especially useful for search algorithms, because given relatively "balanced" (all subtrees have the same depth) BSTs, we will be able to search for elements in BSTs in `O(log(n))` time. BSTs can be considered a visual representation of binary search.

```javascript
// BST node definition
class Node {
  constructor(val) {
    self.value = val;
    self.left = null;
    self.right = null;
  }
}

// Creating a BST
const root = new Node(5);
root.left = new Node(3);
root.right = new Node(8);
root.right.left = new Node(7);

// The resulting tree should look like the following
//   5
//  / \
// 3   8
//    /
//   7
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

#### Algorithm description

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

#### Time and space complexity

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

#### Algorithm description

The following algorithm returns all values in the tree level by level from top to bottom. This is hard to do with DFS because DFS explores each subtree completely before moving on to the next. BFS traverses nodes in exactly the order we want, making it easy to add their values to a list in level order.

BFS is typically implemented using queues. Since there is no built-in queue data structure in JavaScript, we use arrays instead, with the array `shift` method to dequeue elements from the front of the array. Note that `shift` is a relatively inefficient `O(n)` operation, and when we need more efficient algorithms we would either use linked lists to implement a queue data structure, or use Python and its built-in `deque` data structure (uses linked lists underneath) for queue operations.

The BFS algorithm works by iteratively (no recursion) adding each node's children to a queue, and visiting nodes in the order they appear in the queue. This guarantees all nodes at each level will be visited before nodes at lower levels. See above video for a visual description.

```javascript
// Return list of values in tree in level order from top to bottom
const levelOrder = (root) => {
  const levelOrderValues = [];
  // Store upcoming nodes in a queue
  q = [root];
  while (q.length > 0) {
    // Iteratively dequeue first node in queue until queue is empty
    currNode = q.shift();
    // Perform operation on curr node, in this case add to level order values
    levelOrderValues.push(currNode.val);
    // Enqueue left child if any
    if (currNode.left) {
      q.push(currNode.left);
    }
    // Enqueue right child if any
    if (currNode.right) {
      q.push(currNode.right);
    }
  }
  return levelOrderValues;
};
```

In each loop, we enqueue the left and right child (assuming binary trees) of the current node to our queue, if any. The algorithm starts with only the root node in the queue, and ends when the queue is empty. BFS also works for non-binary trees, where we would enqueue all children and not just left and right children.

#### Time and space complexity

The above algorithm has a time complexity of `O(n)`, where `n` is the number of nodes in the tree. This is because the algorithm will need to visit at most all nodes in the tree to find `x`. This algorithm has a space complexity of `O(n)` because `levelOrderValues` has size `n` when it is returned.

## Additional Resources

1. Read pages 111-114 (book pages 100-103) in the [Cracking the Coding Interview PDF](https://www.dropbox.com/s/uhl4ouzzcz5h6oq/CrackingTheCodingInteview.pdf?dl=0)
2. [FTBC3's class video](https://youtu.be/3Dw3spVIk1w?t=297) when we introduced trees

## Exercises

The following exercises are sorted in increasing order of difficulty, and organised to help us keep track of milestones. Please do as many as you can during Bootcamp and feel free to complete the rest at a later time.

### Pre-Class

These starter problems cover basic tree traversal which will be helpful for the LeetCode and HackerRank exercises to follow.

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

1. [Starter problems in Repl](https://replit.com/@rocketkai/tree-intro-js#index.js)
   1. [Solutions for starter problems](https://replit.com/@rocketkai/tree-intro-js-soln#index.js)
   2. [FTBC3 class video ](https://youtu.be/3Dw3spVIk1w?t=3001)where we solved the 1st 2 problems together (Python)

### Part 1

Binary tree traversal.

1. Univalued Binary Tree ([LeetCode](https://leetcode.com/problems/univalued-binary-tree/))
2. Height / Maximum Depth of a Binary Tree ([HackerRank](https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/maximum-depth-of-binary-tree/))
   1. [FTBC3 class video discussion](https://youtu.be/uQldubu1LOE?t=2269) on solution and how to trace code in a recursion problem
3. Maximum Depth of N-ary Tree ([LeetCode](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/))
   1. Hint: Review [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) problem before attempting this one
   2. [FTBC3 class video discussion](https://youtu.be/L2gtfJBxKzE?t=5329)

### Part 2

Binary Search Trees (BST).

See [Binary Search Tree section](a.1.6-trees.md#binary-search-tree) above for recap on properties of BSTs.

1. Binary Search Tree Insertion ([HackerRank](https://www.hackerrank.com/challenges/binary-search-tree-insertion/problem?isFullScreen=true)) you will need to define a node as well as additional code to insert into the Binary Tree.
2. Search in a Binary Search Tree ([LeetCode](https://leetcode.com/problems/search-in-a-binary-search-tree/))
3. Increasing Order Search Tree ([LeetCode](https://leetcode.com/problems/increasing-order-search-tree/))
   1. Hint: Consider in-order traversal to traverse a binary search tree in increasing order
4. Lowest Common Ancestor of a Binary Search Tree ([HackerRank](https://www.hackerrank.com/challenges/binary-search-tree-lowest-common-ancestor/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/))

### Part 3

DFS pre-order, in-order and post-order traversal.

See [Pre-Order, In-Order, and Post-Order section](a.1.6-trees.md#pre-order-in-order-and-post-order-traversal) above for a recap on the various DFS traversal orderings. For non-binary trees that can have more than 2 children, when we iterate through an array of children we are typically iterating from left to right children.

1. Pre-Order Traversal ([HackerRank](https://www.hackerrank.com/challenges/tree-preorder-traversal/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/n-ary-tree-preorder-traversal/))
2. In-Order Traversal ([HackerRank](https://www.hackerrank.com/challenges/tree-inorder-traversal/problem?isFullScreen=true))
3. Post-Order Traversal ([HackerRank](https://www.hackerrank.com/challenges/tree-postorder-traversal/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/n-ary-tree-postorder-traversal/))

### Part 4

BFS.

1. Level-Order Traversal ([HackerRank](https://www.hackerrank.com/challenges/tree-level-order-traversal/problem?isFullScreen=true))
2. Minimum Depth of Binary Tree ([LeetCode](https://leetcode.com/problems/minimum-depth-of-binary-tree/))
   1. Hint: Consider BFS for efficiency
3. Same Tree ([LeetCode](https://leetcode.com/problems/same-tree/))
   1. Hint: Both DFS and BFS should work, DFS will be simpler
   2. Can you think of both DFS and BFS solutions?
   3. [FTBC3 class video discussion](https://youtu.be/uQldubu1LOE?t=1709) on solution and runtime

### Part 5

Misc tree problems.

1. Path Sum ([LeetCode](https://leetcode.com/problems/path-sum/))
   1. [Rocket solution code](https://pastebin.com/wu9Xn6b3) (Python)
   2. [FTBC3 class video solution](https://youtu.be/DUxsg2iDtuE?t=1226) (Python)
2. Balanced Binary Tree ([LeetCode](https://leetcode.com/problems/balanced-binary-tree/))
   1. [FTBC3 In-Class Discussion Part 1](https://youtu.be/L2gtfJBxKzE?t=4412)
   2. [FTBC3 In-Class Discussion Part 2](https://youtu.be/L2gtfJBxKzE?t=6278)

### Part 6

Misc tree problems.

1. Two Sum IV Input is a BST ([LeetCode](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/))
2. Range Sum of BST ([LeetCode](https://leetcode.com/problems/range-sum-of-bst/))
   1. [Rocket solution code](https://pastebin.com/5eGrpPSq) (Python, naive solution without pruning)
   2. [FTBC3 class video solution](https://youtu.be/3Dw3spVIk1w?t=4579) (Python)

### Part 7

Misc tree problems.

1. Merge Two Binary Trees ([LeetCode](https://leetcode.com/problems/merge-two-binary-trees/))
2. Invert Binary Tree ([LeetCode](https://leetcode.com/problems/invert-binary-tree/))

### More Comfortable

1. Leaf-Similar Trees ([LeetCode](https://leetcode.com/problems/leaf-similar-trees/))
2. Sum of Left Leaves ([LeetCode](https://leetcode.com/problems/sum-of-left-leaves/))
3. Subtree of Another Tree ([LeetCode](https://leetcode.com/problems/subtree-of-another-tree/))
4. Convert Sorted Array to Binary Search Tree ([LeetCode](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/))
   1. Hint: Consider starting in the middle of the array and using recursion.
5. Binary Tree Paths ([LeetCode](https://leetcode.com/problems/binary-tree-paths/))
   1. Hints
      1. Each time we reach a leaf node, we've explored a valid path.
      2. How can we keep track of the path up to each leaf node such that when we reach a leaf node in our recursion, we can add that path to the list of valid paths? Do we need an additional input parameter to our recursive function, i.e. a recursive helper function for this?
      3. Where can we store our list of valid paths? Should it be inside or outside of our recursive helper function?
   2. [FTBC3 class video discussion on algorithm](https://youtu.be/uQldubu1LOE?t=5355) and how to write helper function for recursion problems to pass additional parameter to recursive children
   3. [LeetCode reference solution](https://leetcode.com/problems/binary-tree-paths/discuss/1357824/Python-3-DFS-With-Backtracking) from LeetCode Discuss tab
6. Average of Levels in Binary Tree ([LeetCode](https://leetcode.com/problems/average-of-levels-in-binary-tree/))
   1. Hint: BFS
7. Minimum Absolute Difference in BST ([LeetCode](https://leetcode.com/problems/minimum-absolute-difference-in-bst/))
   1. Hint: The minimum absolute distance in a tree with root node `root` is the minimum of the following 4 values.
      1. `minAbsDist(root.left)`
      2. `minAbsDist(root.right)`
      3. `abs(root.val - maxValInLeftSubtree)`
      4. `abs(root.val - minValInRightSubtree))`
8. Symmetric Tree ([LeetCode](https://leetcode.com/problems/symmetric-tree/))
   1. [Rocket solution code](https://pastebin.com/a2buQJxv) (Python)
   2. [FTBC3 class video solution](https://youtu.be/AMpseCEX6\_A?t=2147) (Python)
9. Cousins in Binary Tree ([LeetCode](https://leetcode.com/problems/cousins-in-binary-tree/))
   1. [Rocket Academy solution code](https://pastebin.com/wWYXg309) (Python)
   2. [Rocket Academy video solution](https://youtu.be/SeNfZBAU\_f4?t=4088) (Python)
10. Diameter of Binary Tree ([LeetCode](https://leetcode.com/problems/diameter-of-binary-tree/))
11. Binary Tree Right Side View ([LeetCode](https://leetcode.com/problems/binary-tree-right-side-view/)) (Medium)
12. Binary Tree Zigzag Level Order Traversal ([LeetCode](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)) (Medium)
