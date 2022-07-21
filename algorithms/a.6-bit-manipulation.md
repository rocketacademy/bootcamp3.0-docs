# A.6: Bit Manipulation

## Learning Objectives

1. Understand that computers store values in code as sequences of bits (data type with value 0 or 1). Computers represent numbers with bits in [binary format](https://en.wikipedia.org/wiki/Binary\_number).
2. Bit manipulation refers to manipulation of the bits that form a value using bitwise operators
3. Know the 6 most common bitwise operators (`&`, `|`, `~`, `^`, `<<`, and `>>`) and what they do

## Introduction

Computers store all data as sequences of 0s and 1s in a data type called a "bit". Programming languages like JavaScript automatically translate JavaScript to bits for us, thus we rarely need to think of bits while building apps. However, there are [several algorithm problems](https://stackoverflow.com/a/2097062) occasionally tested in interviews that can be solved more efficiently by manipulating bits with bitwise operators instead of usual JavaScript commands, thus we learn bit manipulation.

Bit manipulation refers to changing bits in a value using bitwise operators. In the algorithm interview context, this typically involves manipulating bits that represent numbers.&#x20;

There are 6 most common bitwise operators: `&`, `|`, `~`, `^`, `<<`, and `>>`. Let us examine them in a table.

| Operator | Name                                              | Example  | Description                                                                                                                                                                       |
| -------- | ------------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `&`      | Bitwise And                                       | `a & b`  | Compare bits of values `a` and `b` and produce a result based on the comparison. In the result, bits in each position that were both 1 in `a` and `b` stay 1, otherwise become 0. |
| `\|`     | Bitwise Or                                        | `a \| b` | Compare bits of values `a` and `b` and produce a result based on the comparison. In each bit of the result, if either `a` or `b` had a 1 bit in that position, that bit is now 1. |
| `~`      | Bitwise Not                                       | `~a`     | Produce a result where all bits in `a` are reversed. If any bit in `a` was 0, the same bit in the result is 1 and vice versa.                                                     |
| `^`      | Bitwise Xor (pronounced "x-or" or "exclusive or") | `a ^ b`  | Same as Bitwise Or, except if the same bit in both values is 1, that bit is 0 in the result.                                                                                      |
| `<<`     | Bitwise Left Shift                                | `a << 1` | Shift all bits in `a` to the left by the number to the right of the operator, inserting a 0 bit to the right of the original number for every shift.                              |
| `>>`     | Bitwise Right Shift                               | `a >> 1` | Shift all bits in `a` to the right by the number to the right of the operator, deleting the right-most bit of the original number with every shift.                               |

Before trying bitwise operators on your own in a Node console, read the following article with diagrams on how each operator works, and watch the following illustrative videos.

{% embed url="https://code.tutsplus.com/articles/understanding-bitwise-operators--active-11301" %}
Understanding Bitwise Operators
{% endembed %}

{% embed url="https://www.youtube.com/watch?v=mesu75PTDC8" %}
Introduction to basic bitwise operators and how they can be used in practice
{% endembed %}

{% embed url="https://www.youtube.com/watch?v=NLKQEOgBAnw" %}
Deeper introduction to binary numbers and how to manipulate those numbers using bitwise operators
{% endembed %}

{% embed url="https://www.youtube.com/watch?v=qq64FrA2UXQ" %}
Example of how to add 2 numbers using only bitwise operators
{% endembed %}

## Exercises

### Pre-Class

1. Decode XORed Array ([LeetCode](https://leetcode.com/problems/decode-xored-array/))
   1. Hint: If `A XOR B == C`, then `C XOR A == B` and `C XOR B == A`.
   2. [Rocket Academy solution code](https://pastebin.com/BVmPd2kE) (Python)
   3. [Rocket Academy solution video](https://youtu.be/88-cUrvsZ5Q?t=3202) (Python)

### Part 1

Hint: For JavaScript, consider using the built-in [`toString(2)`](https://stackoverflow.com/a/9939785) method on numbers to convert integers (aka decimal numbers) to binary numbers, and `toString(10)` to convert binary numbers to integers. For Python, consider using the equivalent built-in functions `bin` and `int`.

1. XOR Operation in an Array ([LeetCode](https://leetcode.com/problems/xor-operation-in-an-array/))
2. Hamming Distance ([LeetCode](https://leetcode.com/problems/hamming-distance/))
3. Sort Integers by the Number of 1 Bits ([LeetCode](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/))
4. Binary Number with Alternating Bits ([LeetCode](https://leetcode.com/problems/binary-number-with-alternating-bits/))

### Part 2

1. Power of Two ([LeetCode](https://leetcode.com/problems/power-of-two/))
2. Power of Four ([LeetCode](https://leetcode.com/problems/power-of-four/))
3. Number Complement ([LeetCode](https://leetcode.com/problems/number-complement/))
   1. Hint: We cannot just use the `~` operator because JavaScript and Python integers are signed by default, and the problem assumes unsigned integers. [Solution here](https://leetcode.com/problems/number-complement/discuss/1870920/Python-easy-solution-for-beginners).
4. Convert Binary Number in a Linked List to Integer ([LeetCode](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/))

### More Comfortable

1. Maximizing Xor ([HackerRank](https://www.hackerrank.com/challenges/maximizing-xor/problem?isFullScreen=true))
2. Sum vs Xor ([HackerRank](https://www.hackerrank.com/challenges/sum-vs-xor/problem?isFullScreen=true))
3. Reverse Bits ([HackerRank](https://www.hackerrank.com/challenges/flipping-bits/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/reverse-bits/))
   1. Hint: Unsigned integer means the number is always positive and has no signed bit
4. Single Number ([HackerRank](https://www.hackerrank.com/challenges/lonely-integer/problem?isFullScreen=true), [LeetCode](https://leetcode.com/problems/single-number/))
   1. Hint: Requires trick to understand what happens when we XOR a number with 0, and when we XOR a number with itself
