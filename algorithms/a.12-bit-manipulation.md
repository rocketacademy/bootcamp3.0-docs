# A.12: Bit Manipulation

## Introduction

Bit manipulation is commonly taught in core computer science courses to help students understand how numbers are represented and manipulated by computers. Some companies use bit manipulation in their interview processes.

Please read about the 6 main bitwise operators `&`, `|`, `~`, `^`, `<<`, and `>>` [here](https://code.tutsplus.com/articles/understanding-bitwise-operators--active-11301). These operators can be used in Python to perform bitwise operations.

{% embed url="https://www.youtube.com/watch?v=qq64FrA2UXQ" %}

{% embed url="https://www.youtube.com/watch?v=mesu75PTDC8" %}

{% embed url="https://www.youtube.com/watch?v=NLKQEOgBAnw" %}

## Use Case: Hamming Codes

A Hamming Code is an error-correction algorithm that uses bit manipulation to check if a set of data has errors (specifically binary data) in O(logn) space and time. These videos give a good intuition of the usefulness of bit manipulation as it relates to binary data.

{% embed url="https://www.youtube.com/watch?v=X8jsijhllIA" %}

{% embed url="https://www.youtube.com/watch?v=b3NxrZOu_CE" %}

Hamming codes have a Hamming distance of 3: The algorithm can detect up to three errors per block.

## Exercises

### Pre-Class

1. [https://leetcode.com/problems/decode-xored-array/](https://leetcode.com/problems/decode-xored-array/)
   1. Hint: If `A XOR B == C`, then `C XOR A == B` and `C XOR B == A`.
   2. Rocket Academy solution code: [https://pastebin.com/BVmPd2kE](https://pastebin.com/BVmPd2kE)
   3. Rocket Academy solution video: [https://youtu.be/88-cUrvsZ5Q?t=3202](https://youtu.be/88-cUrvsZ5Q?t=3202)

### Part 1

1. [https://leetcode.com/problems/xor-operation-in-an-array/](https://leetcode.com/problems/xor-operation-in-an-array/)
2. [https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)
3. [https://leetcode.com/problems/hamming-distance/](https://leetcode.com/problems/hamming-distance/)
4. [https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/)
   1. Consider using Python's built-in decimal to binary converter function `bin()`

### More Comfortable

1. [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)
   1. Requires trick to understand what happens when we XOR a number with 0, and when we XOR a number with itself
2. [https://leetcode.com/problems/number-complement/](https://leetcode.com/problems/number-complement/)
3. [https://leetcode.com/problems/binary-number-with-alternating-bits/](https://leetcode.com/problems/binary-number-with-alternating-bits/)
4. [https://leetcode.com/problems/power-of-two/](https://leetcode.com/problems/power-of-two/)
5. [https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)
6. [https://leetcode.com/problems/power-of-four/](https://leetcode.com/problems/power-of-four/)

## Further Reading

Two's complement

{% embed url="https://www.youtube.com/watch?v=4qH4unVtJkE" %}
