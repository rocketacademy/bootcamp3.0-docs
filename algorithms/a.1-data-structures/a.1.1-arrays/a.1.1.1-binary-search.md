# A.1.1.1: Binary Search

## Learning Objectives

1. Understand conceptually how binary search works
2. Know how to implement binary search in code

## Introduction

Binary search allows us to search a sorted array for a target number in `O(logn)` time. The following videos explain the concept.

{% embed url="https://youtu.be/YzT8zDPihmc" %}
Dramatic illustration of the efficiency of binary search
{% endembed %}

{% embed url="https://www.youtube.com/watch?v=T2sFYY-fT5o" %}
Explanation of the binary search algorithm in code and its runtime
{% endembed %}

## Example Code

Consider the following canonical binary search implementation.

```javascript
const binarySearch = (arr, x) => {
  // Initialise left and right bounds of search to start and end of arr
  let left_index = 0;
  let right_index = arr.length - 1;
  // While left_index and right_index have yet to overlap
  while (left_index <= right_index) {
    // Find the midpoint between left_index and right_index
    let mid_index = Math.floor((left_index + right_index) / 2);

    console.log("middle index", mid_index);
    // If the element at mid_index is x, return mid_index
    // Use Math.floor to ensure that the index position is an integer not a decimal
    if (arr[mid_index] === x) {
      return mid_index;
    }
    // Otherwise, if x is greater than elem at mid_index,
    // update left_index to be 1 above mid_index
    else if (arr[mid_index] < x) {
      left_index = mid_index + 1;
    }
    // Otherwise, if x is less than elem at mid_index,
    // update right_index to be 1 below mid_index
    else {
      right_index = mid_index - 1;
    }
  }
  // If x is not found, return -1
  return -1;
};

const myList = [2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
const result = binarySearch(myList, 6); // 4
console.log(result);
```

## Exercises

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. Binary Search ([LeetCode](https://leetcode.com/problems/binary-search/))
   1. [Rocket solution code](https://pastebin.com/9v2GdhRM) (Python)
   2. [Rocket solution video](https://youtu.be/Z5VjCg2YuPs?t=1147) (Python)

### Part 1

1. First Bad Version ([LeetCode](https://leetcode.com/problems/first-bad-version/))
2. Valid Perfect Square ([LeetCode](https://leetcode.com/problems/valid-perfect-square/))
3. Search Insert Position ([LeetCode](https://leetcode.com/problems/search-insert-position/))
4. Two Sum II Input Array is Sorted ([LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/))
5. Count Negative Numbers in a Sorted Matrix ([LeetCode](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/))
   1. [Rocket solution code](https://pastebin.com/u7xC2K7t) (Python)
   2. [Rocket solution video](https://youtu.be/Z5VjCg2YuPs?t=1598) (Python)
