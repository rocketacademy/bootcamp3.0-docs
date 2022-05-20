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

Linked lists store ordered lists of data where elements (aka "nodes") may not be stored in contiguous blocks of memory. Each node contains a payload (numbers in above illustration) and a pointer to the next node (arrows in above illustration).&#x20;

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
  this.val = (val === undefined ? 0 : val)
  this.next = (next === undefined ? null : next)
}
```

### Linked list traversal

Given a linked list head node `node`, we can traverse the linked list with a while loop and calling `node = node.next` at the end of the loop, where `next` is a property of the linked list node that points to the next node.

```javascript
while (node) {
  // TODO: Do something with current node
  node = node.next // Iterate to next node
}
```

### Insert and delete node in linked list

![Steps to insert a node in a linked list. Source: University of San Francisco](../../.gitbook/assets/image.png)

To insert a node in a linked list we need to:

1. Point the "next" pointer in the new node to the node ahead of it in the list
2. Point the "next" pointer of the node behind the new node to the new node

To delete a node in a linked list we need to:

1. Point the "next" pointer of the previous node to the node after the current node, effectively removing the current node from the chain of nodes in the linked list

## Exercises

For Repl exercises: Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Pre-Class

1. [https://replit.com/@neokaiyuan/singly-linked-list-js#index.js](https://replit.com/@neokaiyuan/singly-linked-list-js#index.js)
   1. [https://replit.com/@neokaiyuan/singly-linked-list-js-solution#index.js](https://replit.com/@neokaiyuan/singly-linked-list-js-solution#index.js)
   2. [FTBC3 class video](https://youtu.be/qewAXA\_vkpE?t=2004) (Python) where we covered the 1st 2 problems (re-recorded after class)

### Part 1

1. [https://replit.com/@neokaiyuan/doubly-linked-list-js#index.js](https://replit.com/@neokaiyuan/doubly-linked-list-js#index.js)
   1. [https://replit.com/@neokaiyuan/doubly-linked-list-js-solution#index.js](https://replit.com/@neokaiyuan/doubly-linked-list-js-solution#index.js)
2. [https://repl.it/@neokaiyuan/circular-doubly-linked-list](https://repl.it/@neokaiyuan/circular-doubly-linked-list)
   1. [https://repl.it/@neokaiyuan/circular-doubly-linked-list-soln](https://repl.it/@neokaiyuan/circular-doubly-linked-list-soln)
3. [https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)
   1. Here's an [intuitive introduction to binary numbers](https://www.mathsisfun.com/binary-number-system.html).
   2. [FTBC3 class video solution](https://youtu.be/qewAXA\_vkpE?t=2372) (re-recorded after class)
      1. This video also explains binary numbers.

### Part 2

1. [https://leetcode.com/problems/remove-duplicates-from-sorted-list/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
   1. Hint: Keep track of prev node and next node
   2. When we encounter duplicate, update prev node's next value to next node
2. [https://leetcode.com/problems/middle-of-the-linked-list/](https://leetcode.com/problems/middle-of-the-linked-list/)
3. [https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)
4. [https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)
   1. Hint: For given node, keep track of old next node and new next node
   2. Inside while loop:
      1. Old next node is `node.next`
      2. Assign `node.next` to new next node (the node we just visited)
      3. Assign new next node variable to `node`
      4. Assign `node` to old next node

### Part 3

1. [https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)
2. [https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)
3. [https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)
4. [https://leetcode.com/problems/intersection-of-two-linked-lists/](https://leetcode.com/problems/intersection-of-two-linked-lists/)

## Additional Resources

1. Read pages 103-105 (book pages 92-94) in the [Cracking the Coding Interview PDF](https://drive.google.com/file/d/1M3uvavrprW\_xmbSFHAe3Q4RgfgFwEfwy/view?usp=sharing).
2. [FTBC3's class video](https://youtu.be/qewAXA\_vkpE?t=1596) when we introduced linked lists.
