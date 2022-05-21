# A.1.5: Linked Lists

## Learning Objectives

1. Linked lists store ordered data using nodes that each contain a payload and a pointer to the next node
2. A pointer is a memory address, called "pointer" for illustration purposes
3. When to use linked lists vs arrays
4. How to execute common linked list operations such as inserting and deleting nodes

## Introduction

{% embed url="https://www.youtube.com/watch?v=R9PTBwOzceo" %}
Brief introduction to the linked list data structure. Source: Neso Academy
{% endembed %}

Linked lists store ordered lists of data where elements (aka "nodes") may not be stored in contiguous blocks of memory. Each node contains a payload (numbers in above illustration) and a pointer to the next node (arrows in above illustration).

The benefit of non-contiguous data is that inserting or deleting a node from anywhere in a linked list is an `O(1)` operation because only adjacent nodes need updating, instead of all subsequent elements in an array. The drawback of this is that accessing an element in the middle of a linked list requires `O(n)` traversal, instead of `O(1)` access with an array.

Below is a comparison of runtimes for common array and linked list operations.

| Operation                        | Runtime (Arrays) | Runtime (Linked Lists)                                                  |
| -------------------------------- | ---------------- | ----------------------------------------------------------------------- |
| Insertion/Deletion (start)       | `O(n)`           | `O(1)`                                                                  |
| Insertion/Deletion (middle)      | `O(n)`           | `O(n)` (`O(1)` if we have pointer to the node to be deleted)            |
| Insertion/Deletion (end)         | `O(1)`           | `O(n)` (`O(1)` if we have pointer to tail node with doubly-linked list) |
| Access element at specific index | `O(1)`           | `O(n)`                                                                  |

We typically use linked lists when we need efficient deletion of the first element in a list, for example to implement queues. We also use linked lists when we may not have sufficient contiguous storage space, for example in file systems on our hard drives.

## Common Linked List Operations

### Linked list node definition

The following linked list node definition is the definition LeetCode uses for linked list problems. Each node will have 2 properties `val` and `next` that can be accessed with dot notation like with any other class instance, e.g. `node.val` and `node.next`, where `node` is a `ListNode` instance.

```javascript
function ListNode(val, next) {
  this.val = val === undefined ? 0 : val;
  this.next = next === undefined ? null : next;
}
```

### Linked list traversal

Given a linked list head node `node`, we can traverse the linked list with a while loop and calling `node = node.next` at the end of the loop, where `next` is a property of the linked list node that points to the next node.

```javascript
while (node) {
  // TODO: Do something with current node
  node = node.next; // Iterate to next node
}
```

### Insert and delete node in linked list

![Steps to insert a node in a linked list. Source: University of San Francisco](<../../.gitbook/assets/A.1.5 Linked List Add Node.png>)

To insert a node in a linked list we need to:

1. Point the "next" pointer in the new node to the node ahead of it in the list
2. Point the "next" pointer of the node behind the new node to the new node

To delete a node in a linked list we need to:

1. Point the "next" pointer of the previous node to the node after the current node, effectively removing the current node from the chain of nodes in the linked list

## Exercises

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

For problems with both HackerRank and LeetCode, implement a solution on the platform you are least comfortable with; feel free to submit on both.

### Pre-Class

1. Print the elements of a linked list ([HackerRank](https://www.hackerrank.com/challenges/print-the-elements-of-a-linked-list/problem?isFullScreen=true))
2. Insert a node at the tail of a linked list ([HackerRank](https://www.hackerrank.com/challenges/insert-a-node-at-the-tail-of-a-linked-list/problem?isFullScreen=true))

### Part 1

1. Insert a node at the head of a linked list ([HackerRank](https://www.hackerrank.com/challenges/insert-a-node-at-the-head-of-a-linked-list/problem?isFullScreen=true))
2. Insert a node at a specific position in a linked list ([HackerRank](https://www.hackerrank.com/challenges/insert-a-node-at-a-specific-position-in-a-linked-list/problem?isFullScreen=true))
3. Delete a node from a linked list ([HackerRank](https://www.hackerrank.com/challenges/delete-a-node-from-a-linked-list/problem?isFullScreen=true))
4. Remove linked list elements ([LeetCode](https://leetcode.com/problems/remove-linked-list-elements/))

### Part 2

1. Palindrome linked list ([LeetCode](https://leetcode.com/problems/palindrome-linked-list/))
2. Middle of the linked list ([LeetCode](https://leetcode.com/problems/middle-of-the-linked-list/))
3. Print the elements of a linked list in reverse ([HackerRank](https://www.hackerrank.com/challenges/print-the-elements-of-a-linked-list-in-reverse/problem?isFullScreen=true))
4. Compare two linked lists ([HackerRank](https://www.hackerrank.com/challenges/compare-two-linked-lists/problem?isFullScreen=true))

### Part 3

1. Get the value of the node at a specific position from the tail ([HackerRank](https://www.hackerrank.com/challenges/get-the-value-of-the-node-at-a-specific-position-from-the-tail/problem?isFullScreen=true))
2. Delete duplicate value nodes from a sorted linked list ([HackerRank](https://www.hackerrank.com/challenges/delete-duplicate-value-nodes-from-a-sorted-linked-list/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-list/))
   1. Hint: Keep track of prev node and next node. When we encounter duplicate, update prev node's next value to next node
3. Merge two sorted linked lists ([HackerRank](https://www.hackerrank.com/challenges/merge-two-sorted-linked-lists/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/merge-two-sorted-lists/))
4. Reverse a linked list ([HackerRank](https://www.hackerrank.com/challenges/reverse-a-linked-list/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/reverse-linked-list/))
   1. Hint: For given node, keep track of old next node and new next node
   2. Hint: Inside while loop:
      1. Old next node is `node.next`
      2. Assign `node.next` to new next node (the node we just visited)
      3. Assign new next node variable to `node`
      4. Assign `node` to old next node

### More Comfortable

1. Find the merge point of two joined linked lists ([HackerRank](https://www.hackerrank.com/challenges/find-the-merge-point-of-two-joined-linked-lists/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/))
2. Insert a node into a sorted doubly linked list ([HackerRank](https://www.hackerrank.com/challenges/insert-a-node-into-a-sorted-doubly-linked-list/problem?isFullScreen=true))
3. Reverse a doubly linked list ([HackerRank](https://www.hackerrank.com/challenges/reverse-a-doubly-linked-list/problem?isFullScreen=true))
4. Detect whether a linked list contains a cycle ([HackerRank](https://www.hackerrank.com/challenges/detect-whether-a-linked-list-contains-a-cycle/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/linked-list-cycle/))
