# A.2: Complexity Analysis

## Learning Objectives

1. Know what Big-O notation is and how we use it to measure algorithmic time and space complexity
2. Know common Big-O complexities and what kinds of algorithms have each complexity for time.

## Introduction

Big-O notation is the most common way to measure theoretical time and space "complexity" of algorithms to judge their efficiency. Time complexity refers to number of operations in relation to input size `n`. Space complexity refers to amount of additional memory allocated in relation to input size `n`, not including input size.

For example, the following function has time complexity of `O(n)` (pronounced "oh of n", aka "linear" complexity) and space complexity of `O(1)` (pronounced "oh of one", aka "constant" complexity), where `n` refers to the size of the input array `arr`. This means runtime grows "linearly" with the value of `n` (if `n` grows by 1 unit, runtime grows by 1 unit), and space stays constant (if `n` grows or shrinks, space stays the same).

```javascript
const doesArrayHaveOne(arr) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === 1) {
      return true;
    }
  }
  return false;
}
```

Big-O represents the upper bound of complexity, i.e. the "worst-case" time or space required in relation to `n`. For example, there may not be `n` operations in the above function if the first element in `arr` is `1`. But we still consider the function to be `O(n)` because in the "worst case", e.g. when `arr` does not contain `1`, we would need to iterate through the whole array of size `n`.

Big-O only cares about the "highest order" of `n` (we can think of `n` as `n^1` and `1` as `n^0`, where "order" refers to the exponent) because at larger values of `n` when complexity matters, the highest-order term has most effect. For example, we might expect the above function to have runtime `O(n+1)`, because there are up to `n+1` operations if `arr` does not contain `1`. But because `1` is a "lower order" term than `n`, we drop the `1` in Big-O notation and only use `O(n)`.

Big-O also always drops coefficients, because those matter less than the "order" of the highest-order term at large values of `n`. For example, if my algorithm needed `2n^2` operations, I would remove the `2` in `2n^2` and have Big-O complexity of `O(n^2)`.

Common Big-O complexities include `O(1)`, `O(logn)`, `O(n)`, `O(nlogn)`, `O(n^2)`, `O(2^n)`.

![c refers to a constant value. Source: Geeks for Geeks](<../.gitbook/assets/A.4 - Big O.png>)

## Constant: `O(1)`

### Description

`O(1)` ("oh of one") time means the algorithm will complete in a fixed number of operations regardless of input size.

`O(1)` space means the algorithm will complete using a fixed amount of additional space (not including space of the input) regardless of input size.

### Example: Find median element in sorted array

Given a sorted array of length `n`, find the median element of the array. Median refers to the element ranked `n/2` in sorted order.

We might be tempted to loop over the array and stop when `i === n/2`, but that would be an `O(n)` algorithm because the number of iterations would increase linearly with `n`.

Instead, since the array is sorted, we can access the middle element in a single operation with `arr[arr.length/2]`, where `arr` is the sorted input array. This is an `O(1)` algorithm because no matter `n`, the algorithm runs in a constant number of operations (in this case 1).

Referencing an array element runs in `O(1)` space because it does not require additional variables beyond the input elements.

## Log: `O(logn)`

### Description

`O(logn)` ("oh of log n") time means the algorithm will complete in a number of operations proportional to the log of the input size `n`.

Without getting into too much math, `log(n)` represents the exponent necessary to raise a constant number (typically 2 or 10, the exact number doesn't matter in Big-O) to the value of `n`. For example, assuming a log of "base" 2, `log(2)` equals 1, and `log(1024)` equals 10. Even though the value of `n` increased by over 1000 between the 2 examples, the value of `log(n)` only increased by 10. Thus `log(n)` is significantly smaller than `n` for large values of `n`.

### Example: Find element with value `x` in sorted array

Given a sorted array of length `n`, find the position of an element with value `x`.

A naive solution would be to iterate over every element in the array until we find `x`, but this would run in `O(n)` time because we would need to search through up to `n` elements.

A more optimal solution would be to perform binary search over the array, which runs in `O(logn)` time. Binary search works by splitting a sorted array into half, finding which half contains `x`, and repeating on that half until it finds `x`. This would require checking at most on the order of `log(n)` elements.

For example, if my input array were numbers from 1 to 1000, e.g. `[1, 2, ..., 1000]`, I would first find the middle element at index `n/2` and compare it with `x`. If `x === arr[n/2]`, return `n/2` as the index of `x`. If `x > arr[n/2]`, repeat the same process on the right half of `arr`. If `x < arr[n/2]`, repeat the same process on the left half of `arr`. We will learn about and practise binary search in detail later in the course.

Binary search runs in `O(1)` space because it does not require additional variables beyond the input elements.

## Linear: `O(n)`

### Description

`O(n)` ("oh of n") time means the algorithm will complete in a number of operations proportional to the input size `n`.

### Example: Find largest number in unsorted array

Given an unsorted array of numbers where the array has length `n`, find the position of the largest number.

We cannot perform binary search on this array because it is unsorted and we do not know the value of the largest number. If the array were sorted, we could extract the last element of the array that would be the largest number in `O(1)` time. The fastest sorting algorithms take `O(nlogn)` time. Thus the best method is to iterate over each element of the array linearly (i.e. for loop) until we reach the end of the array and confirm the largest number, which would take `O(n)` time.

Linear search runs in `O(1)` space because it does not require additional variables beyond the input elements.

## Loglinear: `O(nlogn)`

### Description

`O(nlogn)` ("oh of n log n") time means the algorithm will complete in a number of operations proportional to the input size `n` times `log(n)`. This typically involves performing a binary-search-like operation for every element in the input.

### Example: Sort an unsorted array of numbers

Given an unsorted array of numbers, return an array of the same elements in sorted order.

The fastest sorting algorithms run in `O(nlogn)` time, and we can assume `O(nlogn)` runtime for any algorithms that require sorting, where `n` is the size of the input. We do not need to understand why yet; we will explore sorting algorithms later in the course. We can use JavaScript's built-in array `sort` method to implement sorting in code.

Companies rarely ask candidates to implement sorting algorithms in interviews because they are the kind of answer that can be memorised. There is no need to memorise sorting algorithm implementations, but it would be good to understand how they work.

The most common sorting algorithm Merge Sort runs in `O(n)` space because at any given time it requires up to `n` elements of temporary storage in addition to the input data.

## **Quadratic:** `O(n²)`

### Description

`O(n^2)` ("oh of n squared") time means the algorithm will complete in a number of operations proportional to the square of the input size `n`. This typically involves nested loops over an input collection.

### Example: Find all unordered pairs of numbers in an array

Given an array of numbers, find all unordered pairs of those numbers.

This problem requires us to loop through each element of the array, and for each element of the array, loop through each other element of the array. This is a classic `O(n^2)`-time algorithm.

The above algorithm runs in `O(n^2)` space because we would need to return an array containing all unordered pairs of numbers in the original array. There is no need to understand why in detail for now, but if you are curious the explanation is below.

Mathematically there are `n * (n-1)/2` unordered pairs in an input array of size `n`. For example, in an input array `[1, 2, 3]`, there are 2 pairs that start with the 1st element `1` and 1 pair that starts with the 2nd element `2`. If we extrapolate this to an input array `[1, 2, ..., n]`, where `...` represents all numbers between `2` and `n`, there will be `n-1` pairs that start with `1`, `n-2` pairs that start with `2`, so on and so forth until we reach 1 pair that starts with `n-1`. This means we have `1 + 2 + ... + n-1` unique unordered pairs.&#x20;

A clever way to sum `1 + 2 + ... + n-1` is to add consecutive pairs at the beginning and end of the list. For example, `1 + n-1 = n`, `2 + n-2 = n`, etc. There are roughly `(n-1)/2` pairs that sum to `n`, meaning the total number of unordered pairs is `n * (n-1)/2`, which simplifies to `O(n^2)` in Big-O notation.

## Exponential: `O(2ⁿ)`

### Description

`O(2^n)` ("oh of two to the n") time means the algorithm will complete in a number of operations proportional to the number 2 raised to the power of the input size `n`. `O(2^n)` (and any `O(C^n)` complexity where `C` is a constant) is the highest order of complexity and typically bad. If you find your algorithm runs in exponential complexity in an algorithms interview, there is probably a more efficient way to solve the problem.

### Example: Calculate the n-th Fibonacci number

The naive solution to calculating the n-th Fibonacci number runs in `O(2^n)` time. The Fibonacci sequence is defined as `Fib(n) = Fib(n-1) + Fib(n-2)`, where `Fib(0) = 1` and `Fib(1) = 1`. The naive solution recursively calculates `Fib(n)` by calling `Fib(n-1)` and `Fib(n-2)`. This results in 2 operations per `Fib` operation, and because each `Fib` operation runs recursively, we end up with `2^n` operations because it would take `n` levels of `Fib` operations to reach the base cases of `Fib(0)` and `Fib(1)`. Interestingly, this problem can be solved in linear time complexity with dynamic programming. We will learn about dynamic programming later in the course.

The naive Fibonacci solution also runs in `O(2^n)` space because at any given time, there will be up to `O(2^n)` simultaneous function calls, thus `O(2^n)` intermediate `Fib` calculations in memory. The optimal `O(n)` time solution only requires `O(1)` space because it only uses a finite number of variables to calculate `Fib(n)`, regardless of `n`.

## Additional Resources

The following video provides additional explanation of time complexity and Big-O notation.

{% embed url="https://www.youtube.com/watch?v=D6xkbGLQesk" %}
