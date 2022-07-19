# A.1.8: Heaps

## Learning Objectives

1. Heaps are a data structure that enables us to efficiently track the minimum or maximum in a collection of elements, even as that collection changes.
2. Heaps are commonly used to implement priority queues for use cases such as hospital queues, bank queues and process queues in operating systems.
3. JavaScript does not have a built-in heap implementation and building heaps from scratch using arrays is relatively complex. Because heaps are less commonly seen in interviews, Rocket recommends we master other data structures before focusing on heaps, and use Python and its built-in `heapq` library when we are ready to solve heap problems.

## Introduction

Heaps are a data structure that enables us to efficiently track the minimum ("min heap") or maximum ("max heap") in a collection of elements, even as that collection changes. Heaps are commonly used to implement "priority queues" for use cases such as hospital queues, bank queues and process queues in operating systems. In these scenarios, heaps enable us to determine which person/element should be at the front of the queue based on factors in addition to insertion order such as severity or importance.

The beauty of heaps is that they enable us to extract the minimum (in a min heap) or maximum (in a max heap) value in `O(1)` time, while inserting new values into a heap takes `O(logn)` time. This is more efficient than adding a new element in sorted order to a sorted array, which would take `O(n)` time. Heaps are able to do this by utilising properties of trees, where heap elements are only partially sorted and not completely sorted like they would be in a sorted array.

## How Heaps Work

The following video explains what heaps look like in theory and the fundamental properties of heaps that enable heaps to maintain `O(1)` access to the min or a max element efficiently. The video uses a max heap as an example, but the same properties apply to min heaps except with the order reversed (smaller numbers on top).

{% embed url="https://www.youtube.com/watch?v=c1TpLRyQJ4w" %}
Introduction to heaps and how heaps maintain `O(1)` access to min or max element when new element added
{% endembed %}

The following video explains how heaps maintain `O(1)` access to the min or max element when the previous min or max element is removed. Again the video uses a max heap as an example but the same theory applies to min heaps, except with order reversed.

{% embed url="https://www.youtube.com/watch?v=ijfPvX2qYOQ" %}
How heaps maintain `O(1)` access to min or max element after removal of previous min or max element
{% endembed %}

The above videos may not have mentioned, but notice the time complexity of adding or removing an element from the heap is `O(logn)` because we only perform element swaps down a single path of the heap tree, through `O(logn)` levels, where `n` is the number of elements in the heap.

Now that we've learnt the theory, you may be wondering how to implement heaps in practice. The following video explains how to efficiently represent the heap data structure in code using an array.

{% embed url="https://www.youtube.com/watch?v=fJORlbOGm9Y" %}
How to represent and use heaps in code with arrays
{% endembed %}

JavaScript does not have a built-in heap data type, and implementing heaps from scratch is relatively complex. [Here is sample code](https://blog.bitsrc.io/implementing-heaps-in-javascript-c3fbf1cb2e65) for a JavaScript implementation of heaps.

Rocket recommends we focus on mastering other data structures and algorithms first before attempting heap problems. When ready to solve heap problems, Rocket recommends we use Python and its built-in [`heapq`](https://docs.python.org/3/library/heapq.html) library, where `heappush` and `heappop` (equivalent to `insert` and `remove` respectively in JS code example above) are implemented for us.

Please review Rocket's Python submodule before working on heap algorithm exercises with `heapq`.

## Exercises

Please use Python3 and the [Python `heapq` library](https://docs.python.org/3/library/heapq.html) to use heaps in code.

### Tips

1. Python's `heapq` data structure is a min heap by default. To use `heapq` as a max heap with numerical values, multiply every number you insert by -1 on push and pop.
2. We may wish to sort elements by certain numerical values in a heap, but store associated payloads along with those numerical values. In these situations we can insert tuples (e.g. `(x, y)`) into our heap, where `x` is the value to sort by and `y` is the associated payload. For example, in the K Closest Points to Origin problem below, we could store `(dist_to_origin, coordinates)` elements in our heap.
3. A common pattern when solving problems asking for the "max K elements" of anything is to use the reverse kind of heap and maintain the heap size as K. For example, if the problem is asking for "max K elements", we can keep a min heap of size K that stores the max K elements seen so far. Keeping a min heap allows us to find the minimum of the max K elements in constant time, saving us from pushing and popping to our heap if the new element is not within the max K elements so far.
   1. We can do `heap[0]` to quickly peek at the min element in a min heap or the max element in a max heap.
   2. Conversely, if the problem asks for "min K elements" we can use a max heap of size K.
4. Heaps are not always necessary. Given a static input list, it may be faster to sort the input list and access the Kth element instead of using a heap. Heaps are most useful when we may not have the full input up front.

### Pre-Class

1. Last Stone Weight ([LeetCode](https://leetcode.com/problems/last-stone-weight/))
   1. [Rocket Solution code](https://pastebin.com/JCB78UG0) (Python)
   2. [Rocket Solution video](https://youtu.be/Zat3PE0j1bA?t=2092) (Python)

### Part 1

1. Kth Largest Element in Array ([LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/))
   1. Hint: What's the most efficient way to get the Kth largest element in a heap of size K? Would we use a min-heap or max-heap? Review tips above before starting.

### Part 2

1. K Closest Points to Origin ([LeetCode](https://leetcode.com/problems/k-closest-points-to-origin/))

### Part 3

1. The K Weakest Rows in a Matrix ([LeetCode](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/))

### More Comfortable

1. Top K Frequent Words ([LeetCode](https://leetcode.com/problems/top-k-frequent-words/))
   1. Hint: Creating a heap of `n` elements is an [`O(n)` operation](https://stackoverflow.com/questions/9755721/how-can-building-a-heap-be-on-time-complexity). Hence building and maintaining a heap of frequencies and associated words of size K is more efficient (`O(n)`) than sorting all frequencies of up to `n` distinct words (`O(nlogn)`).

## Additional Resources

1. [Alternative video explanation of heaps by Back to Back SWE](https://www.youtube.com/watch?v=g9YK6sftDi0) (same concepts as above)
2. [Rocket's FTBC3's class video](https://youtu.be/Zat3PE0j1bA?t=701) introducing heaps
