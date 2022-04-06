# A.6: Binary Search

## Introduction

Binary search allows us to search a sorted array for a target number in O(log(n)) time. This is faster than linear search, which runs in O(n) time. Note that we can only apply binary search on sorted arrays; it does not work on unsorted arrays.

{% embed url="https://www.youtube.com/watch?v=T2sFYY-fT5o" %}

{% embed url="https://www.youtube.com/watch?v=6ysjqCUv3K4" %}

## Example Code

Consider the following canonical binary search implementation.

```python
def binarySearch(arr, x):
  # Initialise left and right bounds of search to start and end of arr
  left_index, right_index = 0, len(x) - 1
  # While left_index and right_index have yet to overlap
  while left_index <= right_index:
    # Find the midpoint between left_index and right_index
    mid_index = (left_index + right_index) // 2
    # If the element at mid_index is x, return mid_index
    if arr[mid_index] == x:
      return mid_index
    # Otherwise, if x is greater than elem at mid_index,
    # update left_index to be 1 above mid_index
    elif arr[mid_index] < x:
      left_index = mid_index + 1
    # Otherwise, if x is less than elem at mid_index,
    # update right_index to be 1 below mid_index
    else:
      right_index = mid_index - 1
  # If x is not found, return -1
  return -1
  
mylist = [2,3,4,5,6,7,8,9,10,11,12]  
result = binarySearch(my_list, 6)  # 4
```

## Exercises

### Pre-Class

1. [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)
   1. Rocket Academy solution code: [https://pastebin.com/9v2GdhRM](https://pastebin.com/9v2GdhRM)
   2. Rocket Academy solution video: [https://youtu.be/Z5VjCg2YuPs?t=1147](https://youtu.be/Z5VjCg2YuPs?t=1147)

### Part 1

1. [https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/)
   1. Rocket Academy solution code: [https://pastebin.com/u7xC2K7t](https://pastebin.com/u7xC2K7t)
   2. Rocket Academy solution video: [https://youtu.be/Z5VjCg2YuPs?t=1598](https://youtu.be/Z5VjCg2YuPs?t=1598)
2. [https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
3. [https://leetcode.com/problems/search-insert-position/](https://leetcode.com/problems/search-insert-position/)
4. [https://leetcode.com/problems/first-bad-version/](https://leetcode.com/problems/first-bad-version/)

### More Comfortable

1. [https://leetcode.com/problems/valid-perfect-square/](https://leetcode.com/problems/valid-perfect-square/)
   1. Hint: Can we use binary search to find the factor of this number if it were a perfect square?
2. \[Requires Heaps] [https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)
   1. Hint: Heaps may be helpful. Consider the solution to this heaps problem that we may have solved in [D.5.8: Heaps](a.5-data-structures/a.5.8-heaps/#part-3): [https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

## Further Reading

{% embed url="https://yongdanielliang.github.io/animation/web/BinarySearchNew.html" %}

{% embed url="https://www.youtube.com/watch?v=iP897Z5Nerk" %}

{% embed url="https://www.youtube.com/watch?v=NfUTAymEfvQ" %}
