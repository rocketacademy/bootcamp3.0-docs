# A.1.1: Arrays

## Learning Objectives

1. Understand common array functions and their use cases
2. Get familiar with solving algorithm problems with arrays

## Common array functions&#x20;

Assume we start with the following example array `arr`. Scroll right in the table below to see explanations.

```javascript
const arr = [2, 1, 3];
```

| Function              | Resulting value of \`arr\` | Return value | Explanation                                                                                                                                         |
| --------------------- | -------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `arr[1]`              | `[2,1,3]`                  | `1`          | We can access value at specific index in array in a single operation                                                                                |
| `arr.push(4)`         | `[2,1,3,4]`                | `4`          | We can append to end of array in single operation                                                                                                   |
| `arr.length`          | `[2,1,3]`                  | `3`          | JS Array data structure stores up-to-date length that we can retrieve in constant time                                                              |
| `Math.max(...arr)`    | `[2,1,3]`                  | `3`          | Get max element of unsorted array requires iterating over every element in array                                                                    |
| `arr.shift()`         | `[1, 3]`                   | `2`          | Removing element from start of array requires shifting every element to the left by 1 index                                                         |
| `arr.unshift(4)`      | `[4,2,1,3]`                | `4`          | Adding element to start of array requires shifting every element to the right by 1 index                                                            |
| `arr.splice(1, 0, 4)` | `[2,4,1,3]`                | `[]`         | Adding and removing elements from the middle of an array requires shifting every following element by a constant number of indexes                  |
| `arr.sort()`          | `[1,2,3]`                  | `[1,2,3]`    | The fastest sorting algorithms run in `O(nlogn)` time, different JS runtimes implement different sorting algorithms that all have similar runtimes. |

## Exercises

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. Running Sum of 1D Array ([LeetCode](https://leetcode.com/problems/running-sum-of-1d-array/))
2. Richest Customer Wealth ([LeetCode](https://leetcode.com/problems/richest-customer-wealth/))

### Part 1

1. Valid Mountain Array ([LeetCode](https://leetcode.com/problems/valid-mountain-array))
2. Sherlock and Array ([HackerRank](https://www.hackerrank.com/challenges/sherlock-and-array/problem?isFullScreen=true))
3. Jewels and Stones ([LeetCode](https://leetcode.com/problems/jewels-and-stones/))
4. Missing Numbers ([HackerRank](https://www.hackerrank.com/challenges/missing-numbers/problem?isFullScreen=true))
5. Sparse Arrays ([HackerRank](https://www.hackerrank.com/challenges/sparse-arrays/problem?isFullScreen=true))

### Part 2

1. Count Items Matching a Rule ([LeetCode](https://leetcode.com/problems/count-items-matching-a-rule/))
2. Kids with the Greatest Number of Candies ([LeetCode](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/))
3. Left Rotation ([HackerRank](https://www.hackerrank.com/challenges/array-left-rotation/problem?isFullScreen=true))
4. Number of Good Pairs ([LeetCode](https://leetcode.com/problems/number-of-good-pairs/))

### Part 3

1. Sort Array by Parity ([LeetCode](https://leetcode.com/problems/sort-array-by-parity/))
2. Shuffle the Array ([LeetCode](https://leetcode.com/problems/shuffle-the-array/))
3. String Matching in an Array ([LeetCode](https://leetcode.com/problems/string-matching-in-an-array/))
   1. Hint: You may find the array `sort` method helpful to sort input array by word length
   2. Hint: You may find nested for loops helpful where the indexes follow the pattern in the below code sample
   3. [Recommended LeetCode solution](https://leetcode.com/problems/string-matching-in-an-array/discuss/930878/Clean-JavaScript-Solution)
4. Ice Cream Parlor ([HackerRank](https://www.hackerrank.com/challenges/icecream-parlor/problem?isFullScreen=true))

Code sample for String Matching in an Array:

```javascript
for (let i = 0; i <= arr; i += 1) {
  for (let j = i+1; j <= arr; j += 1) {
    // Compare arr[i] and arr[j] without duplicate checks
  }
}
```

### More Comfortable

1. Squares of a Sorted Array ([LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/))
2. Sort Array by Parity II ([LeetCode](https://leetcode.com/problems/sort-array-by-parity-ii))
3. Relative Sort Array ([LeetCode](https://leetcode.com/problems/relative-sort-array/))
