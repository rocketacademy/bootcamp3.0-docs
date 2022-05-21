# A.1.3: Stacks

## Learning Objectives

1. Stacks are a last-in-first-out data structure, typically implemented with arrays
2. The stack concept is useful for tracking ordered data that we may need to reverse, e.g. text edits

## Introduction

{% embed url="https://youtu.be/F1F2imiOJfk" %}
Brief introduction to stack concepts, methods and applications
{% endembed %}

A stack (think stack of plates) is an array-like data structure that supports adding and removing only from the end, aka "top" of the stack. In practice we will use arrays to represent stacks, but what's important is the pattern of only adding and removing from the end of an array to model and solve certain types of problems.

The stack concept powers many features we use daily, including:

1. Undo and redo in text editors (adding new edits to top of stack and removing them on undo)
2. Parentheses-matching in code editors (adding new opening parens to top of stack, removing them on closing paren and highlighting the pair with the same colour)
3. Browser history (new pages get added to a stack, clicking back button pops them off the stack)

Because we only ever add or remove from the end of the stack, all stack operations run in `O(1)` time complexity.

## Exercises

Please use JavaScript arrays to perform stack operations.

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. Remove All Adjacent Duplicates in String ([LeetCode](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/))
   1. [Rocket strategy video](https://youtu.be/y---RCHCdD4?t=4613) (Python)

### Part 1

1. Make The String Great ([LeetCode](https://leetcode.com/problems/make-the-string-great/))
   1. [Rocket strategy video](https://youtu.be/y---RCHCdD4?t=4457) (Python)
2. Backspace String Compare ([LeetCode](https://leetcode.com/problems/backspace-string-compare/))

### Part 2

1. Crawler Log Folder ([LeetCode](https://leetcode.com/problems/crawler-log-folder/))
   1. [Rocket solution video](https://youtu.be/y---RCHCdD4?t=2460) (Python)
2. Maximum Element ([HackerRank](https://www.hackerrank.com/challenges/maximum-element/problem?isFullScreen=true))

### Part 3

1. Valid Parentheses ([LeetCode](https://leetcode.com/problems/valid-parentheses/), [HackerRank](https://www.hackerrank.com/challenges/balanced-brackets/problem?isFullScreen=true))
   1. [Rocket solution code](https://pastebin.com/qGbG1BAN) (Python)
2. Minimum Add To Make Parentheses Valid ([LeetCode](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/))

### Part 4

1. Simple Text Editor ([HackerRank](https://www.hackerrank.com/challenges/simple-text-editor/problem?isFullScreen=true))
2. Validate Stack Sequences ([LeetCode](https://leetcode.com/problems/validate-stack-sequences/))

### More Comfortable

1. Score of Parentheses ([LeetCode](https://leetcode.com/problems/score-of-parentheses/))
   1. Hint: The depth of the stack can be the power of 2
2. Daily Temperatures ([LeetCode](https://leetcode.com/problems/daily-temperatures/))
   1. Hint: Store temperatures and their array indexes in a stack as we iterate through the input array, and pop those temperatures off the stack and populate "num days until warmer temperature" in answer array when we see a warmer temperature.

## Additional Resources

1. [This video](https://www.youtube.com/watch?v=F1F2imiOJfk) is slightly more detailed introduction to stacks than the video above
2. [FTBC3 class video ](https://youtu.be/y---RCHCdD4?t=559)introducing stacks
