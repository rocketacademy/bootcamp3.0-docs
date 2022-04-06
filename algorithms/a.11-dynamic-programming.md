# A.11: Dynamic Programming

## Introduction

Dynamic programming allows us to optimise recursive solutions by "caching" intermediate calculation results to reduce repeated and redundant calculations.

#### Why is it called Dynamic Programming?

[According to Wikipedia](https://en.wikipedia.org/wiki/Dynamic\_programming#:\~:text=The%20word%20dynamic%20was%20chosen,schedule%20for%20training%20or%20logistics.), "The word _dynamic_ was chosen \[...] to capture the time-varying aspect of the problems, and because it sounded impressive. The word _programming_ referred to the use of the method to find an optimal _program_, in the sense of a military schedule for training or logistics." In other words, the name makes this algorithm topic seem harder and more esoteric than it is.

### Introduction Video

(the first 40 minutes are the basic definition of Dynamic Programming- no need to watch 5 hours!!)

{% embed url="https://www.youtube.com/watch?v=oBt53YbR9Kk" %}

Calculating the _nth_ fibonacci number using dynamic programming.

```
fib_table = {} # table to store previously computed values

def fib(n):
  if n < 2:
    return n
  if n in fib_table:
    # give back a previously calculated result
    return fib_table[n]
    
  result = fib(n-1) + fib(n-2)
  
  # store a result that has been calculated
  fib_table[n] = result
  
  return result
```

## Further Reading

{% embed url="https://www.educative.io/courses/grokking-dynamic-programming-patterns-for-coding-interviews/m2G1pAq0OO0" %}

{% embed url="https://www.youtube.com/watch?v=vYquumk4nWw" %}

Some dynamic programming problems can be expressed in a table.

{% embed url="https://www.youtube.com/watch?v=ASoaQq66foQ" %}

{% embed url="https://www.youtube.com/watch?v=OQ5jsbhAv_M" %}

[https://www.youtube.com/watch?v=vYquumk4nWw\&list=PLBZBJbE\_rGRU5PrgZ9NBHJwcaZsNpf8yD](https://www.youtube.com/watch?v=vYquumk4nWw\&list=PLBZBJbE\_rGRU5PrgZ9NBHJwcaZsNpf8yD)

## Exercises

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Part 1

1. [https://repl.it/@kaiyuanneo/dp1-basics#main.py](https://repl.it/@kaiyuanneo/dp1-basics#main.py)
   1. [https://repl.it/@kaiyuanneo/dp1-basics-soln#main.py](https://repl.it/@kaiyuanneo/dp1-basics-soln#main.py)

### Part 2

1. [https://leetcode.com/problems/min-cost-climbing-stairs/](https://leetcode.com/problems/min-cost-climbing-stairs/)
2. [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

### Part 3

1. [https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)
2. [https://leetcode.com/problems/partition-array-for-maximum-sum/](https://leetcode.com/problems/partition-array-for-maximum-sum/)

### Part 4&#x20;

1. [https://leetcode.com/problems/minimum-cost-for-tickets/](https://leetcode.com/problems/minimum-cost-for-tickets/)
2. [https://leetcode.com/problems/divisor-game/](https://leetcode.com/problems/divisor-game/)
   1. Note: This can be solved with math and not DP, but please implement the DP version for practice.
   2. Rocket Academy solution code: [https://pastebin.com/mywskXkk](https://pastebin.com/mywskXkk)
   3. Rocket Academy solution video: [https://youtu.be/SUGb21Ec5kE?t=2113](https://youtu.be/SUGb21Ec5kE?t=2113) (35:13 until about 1:48:30)
