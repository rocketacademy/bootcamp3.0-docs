# A.5.1: Arrays

![array meme](../../.gitbook/assets/array-meme.gif)

## Learning Objectives

By the end of this lesson, you should:

* be familiar with array functionality time and space complexity
* understand new python array slice syntax
* understand how the basic syntax of Leetcode problems work

## Introduction

Many of us will be familiar with arrays since we started using them in Coding Basics. This module will focus on Python-specific array syntax and array-specific practice problems.

### Big-O of Common Python List Operations

Given:

```python
arr = [2,1,3,4,5]
```

#### Constant O\(1\)

`append`

```python
arr.append(9) # [2,1,3,4,5,9]
```

Append only adds something onto the end of a list. Python does not have to consider the rest of the list.

`len`

```python
len(arr) # 5
```

Python stores the length of the list inside the list itself as a running counter.

#### Linear O\(_n_\)

`clear`, `max`, `copy`, `index`, `insert`, `remove`, `reverse,` slice operations.

```python
max(arr) # 5
```

Each of these functions must look at every array element in the worst case.

#### Loglinear O\(_n_log_n_\)

```python
sort(arr) # [1,2,3,4,5]
```

Python uses Timsort sorting algorithm to sort lists.

## Tips

### Useful Python List Syntax

#### Basic Python list methods: [https://www.w3schools.com/python/python_arrays.asp](https://www.w3schools.com/python/python_arrays.asp)

#### Python list slice syntax: [https://stackoverflow.com/a/509295](https://stackoverflow.com/a/509295)

```python
a[start:stop]  # items start through stop-1
a[start:]      # items start through the rest of the array
a[:stop]       # items from the beginning through stop-1
a[:]           # a copy of the whole array
# There is also the step value, which can be used with any of the above:

a[start:stop:step] # start through not past stop, by step
# The key point to remember is that the :stop value represents the first value that is not in the selected slice. So, the difference between stop and start is the number of elements selected (if step is 1, the default).

# The other feature is that start or stop may be a negative number, which means it counts from the end of the array instead of the beginning. So:

a[-1]    # last item in the array
a[-2:]   # last two items in the array
a[:-2]   # everything except the last two items
a[::2]   # every other item in the array

# Similarly, step may be a negative number:

a[::-1]    # all items in the array, reversed
a[1::-1]   # the first two items, reversed
a[:-3:-1]  # the last two items, reversed
a[-3::-1]  # everything except the last two items, reversed
```

## Introduction to Leetcode

Leetcode problems are encapsulated in classes. We will learn more about classes in [D.6: Object-Oriented Programming](../a.8-intro-to-object-oriented-programming.md), but without going into too much detail here, the following are what we need to know to solve and submit problems in Leetcode.

- **Every method inside a Python class requires `self` as the 1st parameter in the method definition.** This is so that the method has access to other attributes and methods within the class instance via `self`.

```python
class Solution:
    def say_something(self):
        print("yay")
```

- **To call Python class methods \(i.e. methods inside the class\), we will need to prefix the method name with** `self.`. For example `self.myMethodName()`. There is no need to pass `self` as the 1st parameter to class methods, even though `self` is the 1st param in the method definition.

```python
class Solution:
    def say_something(self):
        print("yay")
    def buildArray(self, nums: List[int]) -> List[int]:
        self.say_something()
```

- **Leetcode problems specify variable types in function parameters to help us understand the inputs and outputs of the function we need to implement.** This optional syntax is part of Python 3, so that function parameters can specify variable types.

```python
class Solution:
    # this function parameter is a List. It is supposed to return a List
    def buildArray(self, nums: List[int]) -> List[int]:
        pass
```

- **There is no need for us to call the function we define.** For example `validMountainArray`. Leetcode will call the function, we just need to implement it.

```python
class Solution:
    def validMountainArray(self, arr: List[int]) -> bool:
```

## Exercises

Once you've attempted each problem, find solutions in either the Solution or Discuss tabs on that problem's page.

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
   1. Strings can be iterated over like lists in Python.
2. [https://leetcode.com/problems/squares-of-a-sorted-array/](https://leetcode.com/problems/squares-of-a-sorted-array/)
3. [https://leetcode.com/problems/relative-sort-array/](https://leetcode.com/problems/relative-sort-array/)
4. [https://leetcode.com/problems/sort-array-by-parity-ii](https://leetcode.com/problems/sort-array-by-parity-ii/)
5. [https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)
