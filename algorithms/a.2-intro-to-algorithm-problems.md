# A.4.1 Introduction to Algorithm Problems

## Learning Objectives

By the end of this lesson, you should:

- be familiar with the basic format of algorithm problems
- be familiar with the solutions to basic algorithm problems
- understand how algo challenge sites like Leetcode and Hacker Rank work and how to use them

## Introduction

Algorithm questions are a subset of programming in that the question that is asked is usually one-dimensional. It has a right and wrong answer, and a preferable and less preferable way to solve the problem. This constrained problem space is a more "pure" form of programming without any system engineering considerations or users.

In order to have a specific, testable solution algorithm questions must be formulated in a precise math problem-like language. Reading the question and understanding the phrasing may be one of the main challenges.

We'll begin by introducing the concept of algorithm questions and work through some simple examples.

## Exercises

Solve each exercise by writing a function that satisfies the requirements.

## Pre-Class

### Fizz Buzz

Fizz buzz is the classic programmer screening test.

Write a function `fizzbuzz` that takes an integer n as a parameter.

Print out n lines of integers counting up from 1, except:

- If the line number is divisible by 3 print "fizz"
- If the line number is divisible by 5 print "buzz"
- If the line number is divisible by both 3 and 5 print "fizzbuzz"

```python
fizzbuzz(5)
```

Expected output:

```text
1
2
fizz
4
buzz
```

### Reverse a String

Write a function `reverse` that takes a string as a parameter. The function returns the string with it's characters in reverse order.

```python
result = reverse("hello")
```

Expected output in `result`:

```text
"olleh"
```

### Maximum in List

Write a function `maximum` that takes in a array of integers as a parameter and returns the largest number in the list.

```python
result = maximum([1,2,3,999,1])
```

Expected output in `result`:

```text
999
```

### Minimum in List

Write a function `minimum` that takes in a array of integers as a parameter and returns the smallest number in the list.

```python
result = minimum([2,3,9,10,3])
```

Expected output in `result`:

```text
2
```

### Remainder

Write a function `remain` that takes in two integer parameters and, without using the modulus operator, return an integer remainder of dividing two numbers.

```python
result = remain(10,6)
```

Expected output in `result`:

```text
4
```

### Unique Values

Write a function that takes in an array as a parameter and return an array without any duplicate values in it.

```python
result = unique_vals([1,1,1,1,2])
```

Expected output in `result`:

```text
[1,2]
```

## Part 1

#### Hacker Rank

We'll mostly be using leetcode, but to begin we'll solve the most basic questions in Hacker Rank.

[https://www.hackerrank.com/domains/algorithms?filters%5Bsubdomains%5D%5B%5D=warmup](https://www.hackerrank.com/domains/algorithms?filters%5Bsubdomains%5D%5B%5D=warmup)
