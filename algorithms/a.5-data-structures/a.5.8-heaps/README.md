# A.5.8: Heaps

![Heap Ledger](../../../.gitbook/assets/heap-ledger.png)

## Introduction

Heap is a data structure that is optimized for keeping track of the minimum or maximum out of a changing collection of elements. A heap that keeps track of the minimum value is called a min-heap. A heap that keeps track of the maximum value is called a max-heap. A heap implements an abstract data type called a priority queue.

## Complexity Properties of Heaps

Accessing the minimum (for min-heap) or maximum value (for max-heap): `O(1)` constant time.

Putting a new value into a heap: `O(logn)` log time.

Using a normal array we would need linear time to keep track of the max or min element.

{% embed url="https://www.youtube.com/watch?v=c1TpLRyQJ4w" %}

{% embed url="https://www.youtube.com/watch?v=ijfPvX2qYOQ" %}

{% embed url="https://www.youtube.com/watch?v=fJORlbOGm9Y" %}

## Summary (What do we need to know?)

In summary, we should remember 3 primary operations of heaps, and how heap sort works.

1. Pop: Heaps provide efficient extraction (`O(logn)`) of min or max elements in a mutable collection
   1. In code, extraction is done with the `heappop` method of the `heapq` data structure provided by Python [here](https://docs.python.org/3/library/heapq.html).
2. Push: Adding an element to a heap is `O(logn)` because it involves 1 "heapify" call to "fix" the order of the heap after adding the element
   1. In code, adding to a heap is done with `heappush` method of `heapq`.
3. Heapify (create heap from array): Creating a heap is `O(n)`
   1. In code, heap creation is done with `heapify` method of `heapq`.
4. Heap sort runs in `O(nlogn)` time, but in practice is slower than Merge Sort

## Max Heap Example

```python
# consider a single parent and two children
# sift larger values up through the tree
def max_heapify(A,k):

    # get the place in the array that should be left of k
    l = left(k)

    # get the place in the array that should be right of k
    r = right(k)

    # if it's not off the array and
    # left val is more than k val
    if l < len(A) and A[l] > A[k]:
        largest = l
    else:
        largest = k

    # if  it's not off the array and
    # right is more than largest
    if r < len(A) and A[r] > A[largest]:
        largest = r

    # if k isn't larger than children
    if largest != k:
        # swap child with parent
        A[k], A[largest] = A[largest], A[k]

        # recurse down the tree, passing in child
        max_heapify(A, largest)

def left(k):
    return 2 * k + 1

def right(k):
    return 2 * k + 2

def build_max_heap(A):

    # find the root of the tree we are building
    n = int((len(A)//2)-1)

    # do max heap for root and children
    for k in range(n, -1, -1):
        max_heapify(A,k)

A = [3,9,2,1,4,5]
build_max_heap(A)
print(A)
```

From: [https://favtutor.com/blogs/heap-in-python](https://favtutor.com/blogs/heap-in-python)

## Max Heap with Comments

```python
# consider a single parent and two children
def max_heapify(A,k):
    print('***************************')

    # get the place in the array that should be left of k
    l = left(k)

    # get the place in the array that should be right of k
    r = right(k)

    # if it's not off the array and
    # left val is more than k val
    if l < len(A) and A[l] > A[k]:
        print(f'largest is l: {A[l]}')
        largest = l
    else:
        print(f'largest is k: {A[k]}')
        largest = k

    # if  it's not off the array and
    # right is more than largest
    if r < len(A) and A[r] > A[largest]:
        print(f'largest is r: {A[r]}')
        largest = r

    # if k isn't larger than children
    if largest != k:
        # swap child with parent
        A[k], A[largest] = A[largest], A[k]
        print(f'swap {A[largest]} with {A[k]}')

        # recurse up the tree, passing in child
        print(f'recurse down to  {largest} with {A[largest]}')
        max_heapify(A, largest)


def left(k):
    return 2 * k + 1

def right(k):
    return 2 * k + 2

def build_max_heap(A):

    # find the root of the tree we are building
    n = int((len(A)//2)-1)

    # do max heap for root and children
    for k in range(n, -1, -1):
        print(f'heapifying: {k}')
        max_heapify(A,k)

A = [3,9,2,1,4,5]
#     3
#    / \
#   9   2
#  /\   /
# 1  4 5


build_max_heap(A)
print(A)
#     9
#    / \
#   4   5
#  /\   /
# 1  3 2
```

## Full Max Heap Class Example

```python
class Heap:
    def __init__(self):
        self.lst = []
        self.is_bigger_than = operator.gt

    def add(self, x):
        self.lst.append(x)
        idx_node = len(self.lst) - 1
        self._siftup(idx_node)

    def pop(self):
        if len(self.lst) == 0:
            print("Error: Heap empty!")
        else:
            lst = self.lst
            lst[0], lst[-1] = lst[-1], lst[0]  # switch first with last element
            res = lst.pop()  # pop last element
            self._siftdown(0)
            return res

    def _siftup(self, inode):
        lst = self.lst
        iparent = self._get_parent(inode)
        if iparent >= 0 and self.is_bigger_than(lst[inode], lst[iparent]):
            lst[inode], lst[iparent] = lst[iparent], lst[inode]
            self._siftup(iparent)

    def _siftdown(self, inode):
        lst = self.lst
        ichildren = self._get_children(inode)
        for ichild in ichildren:  # do I need to sift down
            if ichild < len(lst) and self.is_bigger_than(lst[ichild], lst[inode]):
                lst[ichild], lst[inode] = lst[inode], lst[ichild]
                self._siftdown(ichild)

    def _get_parent(self, idx_child):
        idx_parent = int((idx_child - 1) / 2)  # zero-based array
        return idx_parent

    def _get_children(self, idx_parent):
        idx_children = 2 * idx_parent + 1, 2 * idx_parent + 2
        return idx_children
```

From: [https://codereview.stackexchange.com/a/239294](https://codereview.stackexchange.com/a/239294)

## Exercises

Please use the [Python `heapq` library](https://docs.python.org/3/library/heapq.html) to utilise heaps in code.

## Tips

1. Python's `heapq` data structure is a min heap by default. To use `heapq` as a max heap with numerical values, multiply every number you insert by -1 on push and pop.
2. We may wish to sort elements by certain numerical values in a heap, but store associated payloads along with those numerical values. In these situations we can insert tuples (e.g. `(x, y)`) into our heap, where `x` is the value to sort by and `y` is the associated payload. For example, in the K Closest Points to Origin problem below, we could store `(dist_to_origin, coordinates)` elements in our heap.
3. A common pattern when solving problems asking for the "max K elements" of anything is to use the reverse kind of heap and maintain the heap size as K. For example, if the problem is asking for "max K elements", we can keep a min heap of size K that stores the max K elements seen so far. Keeping a min heap allows us to find the minimum of the max K elements in constant time, saving us from pushing and popping to our heap if the new element is not within the max K elements so far.
   1. We can do `heap[0]` to quickly peek at the min element in a min heap or the max element in a max heap.
   2. Conversely, if the problem asks for "min K elements" we can use a max heap of size K.
4. Heaps are not always necessary. Given a static input list, it may be faster to sort the input list and access the Kth element instead of using a heap. Heaps are most useful when we may not have the full input up front.

### Pre-Class

1. Implement adding an element to the heap by implementing a `sift_up` function for the max heap example above (don't use a heapq). You can use the heap class example above as reference.
2. [https://leetcode.com/problems/last-stone-weight/](https://leetcode.com/problems/last-stone-weight/)
   1. RA Solution code: [https://pastebin.com/JCB78UG0](https://pastebin.com/JCB78UG0)
   2. RA Solution video: [https://youtu.be/Zat3PE0j1bA?t=2092](https://youtu.be/Zat3PE0j1bA?t=2092)

### Part 1

1. [https://leetcode.com/problems/kth-largest-element-in-a-stream/](https://leetcode.com/problems/kth-largest-element-in-a-stream/)
   1. Hint: What's the most efficient way to get the k-th largest element in a heap of size k? Would we use a min-heap or max-heap?
2. [https://leetcode.com/problems/k-closest-points-to-origin/](https://leetcode.com/problems/k-closest-points-to-origin/)
3. [https://leetcode.com/problems/sort-characters-by-frequency/](https://leetcode.com/problems/sort-characters-by-frequency/)

### Part 2

1. [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)
2. [https://leetcode.com/problems/kth-largest-element-in-an-array/](https://leetcode.com/problems/kth-largest-element-in-an-array/)

### Part 3

1. [https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)
2. [https://leetcode.com/problems/top-k-frequent-words/](https://leetcode.com/problems/top-k-frequent-words/)

## Further Reading

1. [https://www.youtube.com/watch?v=WCm3TqScBM8](https://www.youtube.com/watch?v=WCm3TqScBM8)
2. [https://www.youtube.com/watch?v=g9YK6sftDi0](https://www.youtube.com/watch?v=g9YK6sftDi0)
3. https://www.youtube.com/watch?v=BzQGPA_v-vc
4. [https://www.youtube.com/watch?v=Dvq-YKeuO9Y](https://www.youtube.com/watch?v=Dvq-YKeuO9Y)
5. Here is [RA's FTBC3's class video](https://youtu.be/Zat3PE0j1bA?t=701) introducing heaps.
