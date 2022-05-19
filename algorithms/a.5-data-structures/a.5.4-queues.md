# A.1.4: Queues

## Learning Objectives

1. Queues are a first-in-first-out data structure, typically implemented with linked lists
2. The queue concept is useful for tracking ordered data that needs to be executed sequentially, like queues in real life

## Introduction

{% embed url="https://youtu.be/XuCbpw6Bj1U" %}
Brief introduction to queue concepts, methods and applications
{% endembed %}

A queue is a list-like data structure that supports adding to the back ("enqueue") and removing from the front ("dequeue"). For now we will use arrays to represent queues, but more efficient queue implementations will use linked lists because removing from the front of an array is `O(n)` (all other elements need to shift), while removing from the front of a linked list is `O(1)` (we will learn about this in the Linked Lists submodule).

The queue concept powers many operations in computing, including:

1. Message queues that replay message sends when offline devices go online
2. Process queues where our computer needs to decide which applications get to access our CPU at any given time
3. Data buffers, e.g. when our internet connection lags and our computers store video/audio segments before playback catches up

## Helpful Resources

1. [This video](https://youtu.be/Y7wZO2tMjnY) is a more hands-on introduction to queues than the video above. It introduces queues in Python and Python's built-in `deque` data structure that we can use to perform dequeues in `O(1)` time complexity.
2. Read pages 109-110 in the [Cracking the Coding Interview PDF](broken-reference/).

## Exercises

Please use JavaScript arrays to perform queue operations. After attempting each problem, find solutions in either Solution or Discuss tabs on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

1. [https://replit.com/@neokaiyuan/queues#main.py](https://replit.com/@neokaiyuan/queues#main.py)
   1. Solutions: [https://repl.it/@neokaiyuan/queuessoln#main.py](https://repl.it/@neokaiyuan/queuessoln#main.py)

### Comfortable

1. [https://leetcode.com/problems/task-scheduler/](https://leetcode.com/problems/task-scheduler/)
   1. Hint: This may be solved more efficiently without queues, but see how we can implement it with queues first.
