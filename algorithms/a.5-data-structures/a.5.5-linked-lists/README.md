# A.5.5: Linked Lists

![](../../../.gitbook/assets/llmeme2.jpeg)

## Learning Objectives

By the end of this lesson, you should:

* be familiar with linked list functionality time and space complexity
* understand what a pointer is within the examples
* understand the mechanics of linking and unlinking a linked list node

## Introduction

Linked lists, like arrays, store ordered lists of data. Unlike arrays, linked lists may not be stored in contiguous blocks of memory in RAM. Consecutive elements in a linked list may be stored in different places in RAM, but linked by a pointer from each element in the linked list to the next and/or previous element. This means 2 things for us.

1. Start and mid-list insertion and deletion operations that were `O(n)` time with arrays become `O(1)` time with LLs because all subsequent elements do not need to be shifted in memory. Only pointers of previous and next elements in the list need to be updated.
2. Accessing a specific index that was `O(1)` time with arrays becomes `O(n)` time with LLs because the only way to access an element in the middle of a LL is to traverse the list until we reach that element.

| Operation                        | Runtime (Arrays) | Runtime (Linked Lists)                                                  |
| -------------------------------- | ---------------- | ----------------------------------------------------------------------- |
| Insertion/Deletion (start)       | `O(n)`           | `O(1)`                                                                  |
| Insertion/Deletion (end)         | `O(1)`           | `O(n)` (`O(1)` if we have pointer to tail node with doubly-linked list) |
| Insertion/Deletion (middle)      | `O(n)`           | `O(n)` (`O(1)` if we have pointer to the node to be deleted)            |
| Access element at specific index | `O(1)`           | `O(n)`                                                                  |

## Helpful Resources

1. [Here](https://www.youtube.com/watch?v=R9PTBwOzceo) is a short and intuitive introduction to linked lists.
2. Read pages 104-106 in the [Cracking the Coding Interview PDF](../../a.0-algorithms-overview.md#resources).
3. [FTBC3's class video](https://youtu.be/qewAXA\_vkpE?t=1596) when we introduced linked lists.
   1. I forgot to record it during class so I re-recorded the key points afterward.

## Use Cases

Linked lists (LLs) are typically used when we want faster insertion or deletion of the first element in a list, for example to implement queues or hash tables (to handle hash collisions). LLs are also used when we may not have sufficient contiguous storage space, for example in file systems on our hard drives.

## Exercises

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Pre-Class

1. [https://repl.it/@kaiyuanneo/singly-linked-list](https://repl.it/@kaiyuanneo/singly-linked-list)
   1. [https://repl.it/@kaiyuanneo/singly-linked-list-soln](https://repl.it/@kaiyuanneo/singly-linked-list-soln)
   2. [FTBC3 class video](https://youtu.be/qewAXA\_vkpE?t=2004) where we covered the 1st 2 problems (re-recorded after class)

### Part 1

1. [https://repl.it/@kaiyuanneo/doubly-linked-list](https://repl.it/@kaiyuanneo/doubly-linked-list)
   1. [https://repl.it/@kaiyuanneo/doubly-linked-list-soln](https://repl.it/@kaiyuanneo/doubly-linked-list-soln)
2. [https://repl.it/@kaiyuanneo/circular-doubly-linked-list](https://repl.it/@kaiyuanneo/circular-doubly-linked-list)
   1. [https://repl.it/@kaiyuanneo/circular-doubly-linked-list-soln](https://repl.it/@kaiyuanneo/circular-doubly-linked-list-soln)
3. [https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)
   1. Here's an [intuitive introduction to binary numbers](https://www.mathsisfun.com/binary-number-system.html).
   2. [FTBC3 class video solution](https://youtu.be/qewAXA\_vkpE?t=2372) (re-recorded after class)
      1. This video also explains binary numbers.

### Part 2

1. [https://leetcode.com/problems/remove-duplicates-from-sorted-list/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
2. [https://leetcode.com/problems/middle-of-the-linked-list/](https://leetcode.com/problems/middle-of-the-linked-list/)
3. [https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)
4. [https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)

### Part 3

1. [https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)
2. [https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)
3. [https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)
4. [https://leetcode.com/problems/intersection-of-two-linked-lists/](https://leetcode.com/problems/intersection-of-two-linked-lists/)
