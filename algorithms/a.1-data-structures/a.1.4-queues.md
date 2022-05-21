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

## Exercises

Please use JavaScript arrays to perform queue operations.

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

Please fork starter code Repl and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

1. [https://replit.com/@neokaiyuan/queues-js#index.js](https://replit.com/@neokaiyuan/queues-js#index.js)
   1. Solution: [https://replit.com/@neokaiyuan/queues-js-solution#index.js](https://replit.com/@neokaiyuan/queues-js-solution#index.js)

### Part 1

1. [https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/)
2. [https://leetcode.com/problems/reveal-cards-in-increasing-order/](https://leetcode.com/problems/reveal-cards-in-increasing-order/)

## Additional Resources

1. [This video](https://youtu.be/Y7wZO2tMjnY) is a more hands-on introduction to queues than the video above. It introduces queues in Python and Python's built-in `deque` data structure that we can use to perform dequeues in `O(1)` time complexity.
