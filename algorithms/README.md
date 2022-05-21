# 🧮 Algorithms

## Learning Objectives

1. We study algorithms at Rocket to pass interviews (but they can also be helpful for optimising our code)
2. Know the general format of algorithm interview problems
3. Understand how to solve basic algorithm problems
4. Be familiar with LeetCode and HackerRank problem interfaces
5. Understand strategies to succeed at algorithm interviews
6. Know about other SWE interview types and what to expect for each

## Introduction

Algorithm interviews are the most common interview type for software engineering jobs, and typically require solving an algorithm problem in 30-45 minutes in a coding language of our choice. They will be similar to questions on popular interview prep platforms such as [HackerRank](https://www.hackerrank.com/) and [LeetCode](https://leetcode.com/), or in well-known interview prep material such as [Cracking the Coding Interview](https://drive.google.com/file/d/1M3uvavrprW_xmbSFHAe3Q4RgfgFwEfwy/view?usp=sharing). With enough practice we can master algorithms and pass algorithm interviews from any company.

Algorithm problems require us to code an algorithm (series of steps) to transform specific inputs to specific outputs according to the rules of the problem. One of the most canonical basic algorithm problems is "Fizz Buzz", a problem that asks us to output all numbers from 1 to an input `n` where multiples of 3 are replaced with Fizz, multiples of 5 are replaced with Buzz, and multiples of both 3 and 5 are replaced with Fizz Buzz.

Algorithm interviews typically test for 3 things:

1. Have we worked hard enough to get good at algos
2. Can we logically deduce a solution
3. Can we communicate our thought processes clearly

Understanding the problem is half the battle, and we encourage asking our interviewer as many questions we need to understand the problem.

Below are basic algorithm problems to understand their format and what to expect.

## Warmup Exercises

Solve each exercise by writing a function that satisfies the requirements. You will need to create HackerRank and LeetCode accounts if you have not already.

{% hint style="info" %}
**Recommended learning strategy**

For a given problem, if you cannot think of a way to solve the problem after 15 minutes, check the solutions or submissions to understand how others solved the problem. Come back to the problem after a few days and attempt the problem again. This will save us time and help us learn faster, because many problems follow the same patterns.
{% endhint %}

1. Solve Me First ([HackerRank](https://www.hackerrank.com/challenges/solve-me-first/problem?isFullScreen=true))
2. Simple Array Sum ([HackerRank](https://www.hackerrank.com/challenges/simple-array-sum/problem?isFullScreen=true))
3. Fizz Buzz ([LeetCode](https://leetcode.com/problems/fizz-buzz/)) (Fizz Buzz is a common coding screening test)
4. Mini Max Sum ([HackerRank](https://www.hackerrank.com/challenges/mini-max-sum/problem?isFullScreen=true))
5. Time Conversion ([HackerRank](https://www.hackerrank.com/challenges/time-conversion/problem?isFullScreen=true))

## Tips for Succeeding at Algorithm Interviews

### Introduction

The following strategies will greatly increase our chances of success.

1. Clarify Problem
2. Think Out Loud
3. Naive Solution
4. Pseudocode First
5. Think of Test Cases
6. Can We Do Better?

### Clarify Problem

Always clarify the interview problem before starting; Understanding the problem is half the battle. This shows initiative, communication skills, and an outcome-driven mindset.&#x20;

Clarifications often include:

1. Sample inputs and outputs
2. Constraints on solutions, e.g. run time, data structures
3. Any other ambiguities

### Think Out Loud

Think out loud when solving the problem. Thinking out loud greatly increases our chances of success because it demonstrates communication skills, earns partial credit and helps the interviewer help us. Algorithms interviews test problem-solving ability, not memorisation, and thinking out loud shows how we solve problems.

### Naive Solution

Start with the naive solution so you have something to fall back on if you are unable to create a more efficient solution. The naive solution is typically a brute-force method that may not pass time limits but at least works.

### Pseudocode First

Write pseudocode before code to clarify our algorithm without worrying about syntax, which will save us debugging time later. Where possible, optimise our algorithm in pseudocode before writing code.&#x20;

### Think of Test Cases

Test code on inputs that might break it. More often that not, algorithm problems do not provide comprehensive test cases. This is a strong signal for problem solving independence and thoroughness.&#x20;

### Can We Do Better?

Is there a solution with less time and space complexity? The most impressive candidates develop multiple solutions, each with time and space tradeoffs, and communicate those tradeoffs clearly. They can then decide with the interviewer which solution to implement.

## Other Software Engineering Interview Types

Below are other common coding interview formats that Rocket graduates have encountered.

### Take-Home Assignment

Common initial interview. Typically takes 2-3 days and involves building a simple app related to the company's business in a language of our choice.

Companies typically assess take-home assignments on both completion and code quality. Completion is simpler: does the app meet requirements. Code quality is more subjective, but typically refers to clarity in naming, commenting and decomposition.

Companies often follow-up with an on-site or Zoom interview to verify the candidate knows what they were doing and can communicate decisions clearly. Be sure to revise your code and decisions before meeting them!

### System Design Interview

Less common in entry-level interviews. Typically consists of designing and explaining software architecture, e.g. drawing a diagram of frontend and backend components in an app and explaining how components work together. More common in mid and senior-level interviews because senior engineers spend more time designing architecture. Impressive if entry-level engineer can do systems design.

### Language-Specific Trivia

Less common interview type, mostly asked by teams dependent on more niche languages such as Java (banks, consultancies that work with banks) or Solidity and Rust (Web3). Rocket has also seen software agencies test for SQL knowledge.

### Culture Fit Interview

Standard "get to know you" interviews. Be yourself and show you care by asking your interviewer questions about their job and company.
