# A.5.1: Arrays

## Learning Objectives

1. Understand common array functions and their runtimes
2. Get familiar with solving algorithm problems with arrays

## Common array functions and runtimes

Assume we start with the following example array `arr`. Scroll right in the table below to see explanations.

```javascript
const arr = [2, 1, 3];
```

| Function              | Resulting value of \`arr\` | Return value | Runtime    | Explanation                                                                                                                                         |
| --------------------- | -------------------------- | ------------ | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `arr[1]`              | `[2,1,3]`                  | `1`          | `O(1)`     | We can access value at specific index in array in a single operation                                                                                |
| `arr.push(4)`         | `[2,1,3,4]`                | `4`          | `O(1)`     | We can append to end of array in single operation                                                                                                   |
| `arr.length`          | `[2,1,3]`                  | `3`          | `O(1)`     | JS Array data structure stores up-to-date length that we can retrieve in constant time                                                              |
| `Math.max(...arr)`    | `[2,1,3]`                  | `3`          | `O(n)`     | Get max element of unsorted array requires iterating over every element in array                                                                    |
| `arr.unshift(4)`      | `[4,2,1,3]`                | `4`          | `O(n)`     | Adding element to start of array requires shifting every element to the right by 1 index                                                            |
| `arr.splice(1, 0, 4)` | `[2,4,1,3]`                | `[]`         | `O(n)`     | Adding and removing elements from the middle of an array requires shifting every following element by a constant number of indexes                  |
| `arr.sort()`          | `[1,2,3]`                  | `[1,2,3]`    | `O(nlogn)` | The fastest sorting algorithms run in `O(nlogn)` time, different JS runtimes implement different sorting algorithms that all have similar runtimes. |

## Exercises

After attempting each problem, find solutions in either Solution or Discuss tabs on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. [https://leetcode.com/problems/running-sum-of-1d-array/](https://leetcode.com/problems/running-sum-of-1d-array/)
2. [https://leetcode.com/problems/richest-customer-wealth/](https://leetcode.com/problems/richest-customer-wealth/)

### Part 1

1. [https://leetcode.com/problems/valid-mountain-array](https://leetcode.com/problems/valid-mountain-array)
2. [https://leetcode.com/problems/sort-array-by-parity/](https://leetcode.com/problems/sort-array-by-parity/)
3. [https://leetcode.com/problems/shuffle-the-array/](https://leetcode.com/problems/shuffle-the-array/)
4. [https://leetcode.com/problems/intersection-of-two-arrays-ii/](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

### Part 2

1. [https://leetcode.com/problems/count-items-matching-a-rule/](https://leetcode.com/problems/count-items-matching-a-rule/)
2. [https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)
3. [https://leetcode.com/problems/number-of-good-pairs/](https://leetcode.com/problems/number-of-good-pairs/)
4. [https://leetcode.com/problems/string-matching-in-an-array/](https://leetcode.com/problems/string-matching-in-an-array/)

### More Comfortable

1. [https://leetcode.com/problems/jewels-and-stones/](https://leetcode.com/problems/jewels-and-stones/)
2. [https://leetcode.com/problems/squares-of-a-sorted-array/](https://leetcode.com/problems/squares-of-a-sorted-array/)
3. [https://leetcode.com/problems/relative-sort-array/](https://leetcode.com/problems/relative-sort-array/)
4. [https://leetcode.com/problems/sort-array-by-parity-ii](https://leetcode.com/problems/sort-array-by-parity-ii/)
5. [https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)
