# A.4: Complexity Analysis, Big-O Notation

## Learning Objectives

1. Know what Big-O notation is and how we use it to measure algorithmic time and space complexity
2. Know common Big-O complexities and what kinds of algorithms have each complexity for time and space.

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

## What is a "good" algorithm?

![](../.gitbook/assets/travelling\_salesman\_problem.png)

As defined above, the Big-O of a given function may seem like it's unviable or a "wrong" solution. However, many algorithms in the real-world run in "_bad_" or "_worst_" time complexity. The nature of the problem itself dictates the complexity of the solution, and there is no correct or incorrect solution to a problem.

One of the most classically intractable Computer Science algorithm problems, the [Travelling Salesman Problem](https://en.wikipedia.org/wiki/Travelling\_salesman\_problem) is a kind of problem that has to be solved constantly in real life. [There is no perfect work-around](https://shotl.com/news/the-travelling-salesman-problem-in-the-modern-era) for the fact that it runs in a minimum of exponential time.

## Big-O Common Functions

### Constant Time: `O(1)`

#### Description

Also known as constant time, **O(1)** time complexity means that regardless of how big the input of an algorithm is, the algorithm will still be able to complete in a fixed number of iterations.

**O(1)** space complexity means regardless of input size, the algorithm can complete using a fixed amount of additional space, e.g. a fixed number of variables or data structure size excluding the input data.

#### Example: Find the median element in a sorted array

Given a sorted input array of length _**n**_, find the median element of the array. Median refers to the element that is ranked _**n**_**/2 in the sorting order. One might be tempted to do a for loop over the array and return when the index is \_n**_**/2**, but this would be an **O(**_**n**\_**)** algorithm because the number of iterations is linear based on _**n**_. Instead, since the array is sorted, we can access the middle element directly with `arr[len(arr)/2]`. This operation does not depend on the size of _**n**_, since the array length is readily available and accessing elements in an array by index is a single operation. This algorithm that immediately retrieves the middle element by index runs in **O(1)** time.

The above algorithm also runs in **O(1)** space complexity because it does not require additional variables other than the input array.

### Log Time: `O(logn)`

#### Description

Also known as logarithmic or logn ("log n") time, **O(**_**logn**_**)** complexity means that the algorithm will need to perform a number of operations proportional to the log of the size of the input. Without getting into too much math, **log(**_**n**_**)** represents the exponent necessary to raise a constant number (typically 2 or 10, the exact number doesn't matter in Big-O) to the value of _**n**_. For example, assuming a log of base 2, _**log**_**(2) would be 1, and \_log**_**(1024)** would be 10. Notice how even though the value of `n` increased by 1000+ between the 2 examples, the value of **log(**_**n**_**)** only increased by roughly 10. Thus **log(**_**n**\_**)** is significantly less than _**n**_ at large numbers.

#### Example: Find the element with value `x` in a sorted array

Given a sorted input array of length _**n**_, find the position of an element with value **x**. A naïve solution would be to iterate over every element in the array until we find **x**, but this would run in **O(**_**n**_**) or linear time because we would need to search through n elements at most, in the event that x were at the end of the array. A more optimal solution would be to perform binary search over the array, which runs in O(log\_n**_\*\*) \*\*time. Binary search works by splitting a sorted array into halves recursively until it finds the relevant element. This would require us to compare at most on the order of **log(**_**n**_**) elements. For example, if my input array were numbers from 1 to 1000, e.g. \[1, 2, ..., 1000], to perform binary search on this array, I would first look for the middle element at index \_n**_**/2,** and compare it with **x**. If `x == arr[n/2]`, return `n/2` as the index of x. If `x > arr[n/2]`, repeat the same process on the right half of arr. If `x < arr[n/2]`, repeat the same process on the left half of `arr`. Read more about binary search [here](https://www.geeksforgeeks.org/binary-search/).

The above algorithm runs in **O(1)** space because it does not require additional variables beyond the input elements.

### Linear Time: _`O(n)`_

#### Description

Known as linear time, **O(**_**n**_**)** complexity means that the algorithm needs to inspect at most each element of the input a constant number of times.

#### Example: Find the largest number in an unsorted array

Given an unsorted input array of numbers of length n, find the position of the largest number. We cannot perform binary search on this array because it is unsorted and we do not know the value of the largest number. If the array were sorted, we could extract the last element of the array which would be the largest number in **O(1)** time. The fastest sorting algorithms take **O(**_**nl**_**og**_**n**_**)** time complexity. Thus the best method we have is to iterate over each element of the array linearly (i.e. a for loop) until we reach the end of the array and confirm the largest number, which would take **O(**_**n**_\*\*) \*\*time complexity.

The above algorithm runs in **O(1)** space because it does not require additional variables beyond the input elements.

### Loglinear Time: `O(nlogn)`

#### Description

**O(**_**n**_**log**_**n**_**)** complexity typically involves performing a binary-search-like operation for every element in the input.

#### Example: Sort an unsorted array of numbers

It's rare to invent a sorting algorithm from scratch. Computer scientists have been working on efficient sorting algorithms since the start of the field, and so far they have concluded that [Merge Sort](https://en.wikipedia.org/wiki/Merge\_sort) is the fastest sorting algorithm (in the worst case) that exists today, and it runs in **O(**_**n**_**log**_**n**_**)** time. Thus whenever we are given a problem to sort an unordered list, our first instinct should be to think that this could run in **O(**_**n**_**log**_**n**_**)** time.

Companies rarely ask candidates to implement sorting algorithms such as merge sort in interviews because it's the kind of answer that can be memorised. It doesn't hurt to memorise how common sorting algorithms such as merge sort work, but there's no need to spend too much time on them other than to understand how they work.

The above Merge Sort algorithm runs in **O(**_**n**_**)** space because at any given time it requires temporary storage space on the order of n elements in addition to the input data.

### **Quadratic Time:** `O(n²)`

#### Description

_**O(n²)**_ complexity typically involves nested loops over an input collection.

#### Example: Find all pairs of numbers in an array

Given an array of numbers, find all unordered pairs of those numbers. This problem requires us to loop through each element of the array, and for each element of the array, loop through each other element of the array. This is a classic _**O(n²)**_ -complexity algorithm.

The above algorithm requires **O(**_**n**_**)** space during calculation, but its output will require space proportional to the size of the output, roughly _**n**_**C2** or "_**n**_ choose 2".

### Exponential Time: `O(2ⁿ)`

#### Description

Also known as exponential complexity, **`O(2ⁿ)`** complexity (and any **`O(Cⁿ)`** complexity where **C** is a constant) is the highest order of complexity (without combining it with itself or others above) and typically bad. If you find that your algorithm runs in exponential complexity in a DS\&A interview, there is probably a more efficient algorithm to solve the problem.

#### Example: Calculate the n-th Fibonacci Number

The Fibonacci sequence is defined as **Fib(**_**n**_**) = Fib(**_**n**_**-1) + Fib(**_**n**_**-2)**, where\*\* Fib(0) == 1\*\* and **Fib(1) == 1**. The naïve way to solve Fibonacci is to write a recursive algorithm that calculates **Fib(**_**n**_**)** by calling **Fib(**_**n**_**-1)** and **Fib(**_**n**_**-2)**. However, this results in 2 operations per Fib operation, and because each Fib operation runs recursively, we end up with **2ⁿ** operations because it would take n levels of Fib operations to reach the base cases of **Fib(0) and Fib(1). Interestingly, this problem can be solved in O(\_n**\_\*\*) \*\*time complexity. See [here](https://stackoverflow.com/questions/18172257/efficient-calculation-of-fibonacci-series) for solution.

The **O(2ⁿ) time complexity algorithm above also requires O(2ⁿ) space complexity because at any given time, there will be up to O(2ⁿ) simultaneous function calls, thus O(2ⁿ) intermediate Fib calculations in memory. However, the optimal O(n) time complexity solution only requires O(1) space complexity because it only uses a finite number of variables to calculate Fib(n), regardless of \_n**\_.

### Factorial Time: `O(n!)`

A naive solution to finding all permutations of an array:

```
permutations([1, 2, 3])
```

where the solution would be:

```
[1, 2, 3]
[1, 3, 2]
[2, 1, 3]
[2, 3, 1]
[3, 1, 2]
[3, 2, 1]
```

is an example of a factorial complexity algorithm.

The Travelling Salesman algorithm referenced above is also an example of a problem that can be written naively as _**n**_**!**.

## Further Reading

{% embed url="https://www.youtube.com/watch?v=D6xkbGLQesk" %}
