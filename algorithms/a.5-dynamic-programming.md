# A.5: Dynamic Programming

## Learning Objectives

1. Dynamic programming (DP) problems are a subset of recursion problems that involve caching intermediate calculations to avoid repeated calculations
2. DP problems often involve "take or don't take" logic in each recursive call, which results in repeated calculations without caching
3. DP problems are not the most commonly seen interview problems (less common at most SWE jobs), and Rocket recommends being comfortable with prior algorithm topics before spending too much time on DP

## Introduction

Dynamic programming allows us to optimise recursive solutions by "caching" (i.e. storing) intermediate calculations to minimise repeated and redundant recursive calls.

The first 40 minutes of the below video visually explain the premise behind dynamic programming and why it is powerful. The remainder of the video walks through DP solutions to other problems, which we do not need to review right now.

{% embed url="https://www.youtube.com/watch?v=oBt53YbR9Kk" %}
Introduction to dynamic programming
{% endembed %}

## Exercises

### Part 1

Please fork starter code Repl and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Conway and Catalan problems are optional. Have fun!

1. [https://replit.com/@rocketkai/dp#index.js](https://replit.com/@rocketkai/dp#index.js)
   1. [https://replit.com/@rocketkai/dp-soln#index.js](https://replit.com/@rocketkai/dp-soln#index.js)

### Part 2

1. [https://leetcode.com/problems/min-cost-climbing-stairs/](https://leetcode.com/problems/min-cost-climbing-stairs/)
2. [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

### Part 3

1. [https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)
2. [https://leetcode.com/problems/partition-array-for-maximum-sum/](https://leetcode.com/problems/partition-array-for-maximum-sum/)

### Part 4

1. [https://leetcode.com/problems/minimum-cost-for-tickets/](https://leetcode.com/problems/minimum-cost-for-tickets/)
2. [https://leetcode.com/problems/divisor-game/](https://leetcode.com/problems/divisor-game/)
   1. Note: This can be solved with math and not DP, but please implement the DP version for practice.
   2. Rocket Academy solution code: [https://pastebin.com/mywskXkk](https://pastebin.com/mywskXkk)
   3. Rocket Academy solution video: [https://youtu.be/SUGb21Ec5kE?t=2113](https://youtu.be/SUGb21Ec5kE?t=2113) (35:13 until about 1:48:30)

### Leftover from Sliding Windows

1. [https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)
2. [https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)

## Further Reading

1. [Video solution to Longest Common Subsequence](https://youtu.be/ASoaQq66foQ), a DP problem that involves storing intermediate calculations in a table with dimensions `m` by `n`, where `m` is the length of 1 input word and `n` is the length of the other.
