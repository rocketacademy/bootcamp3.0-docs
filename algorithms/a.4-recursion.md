# A.4: Recursion

## Learning Objectives

1. Recursion is a function calling itself
2. All recursive problems can be solve iteratively and vice versa, but certain problems are more easily solved with either recursion or iteration
3. All recursive functions have 1 or more recurrence relations and 1 or more base cases
4. We can use call stack diagrams to visualise recursive function calls
5. Recursive backtracking is a technique used to explore problem spaces
6. Our recursive functions either return values that "add up" to a final result, or store results in a variable outside the recursive function call

## Introduction

{% embed url="https://youtu.be/lMBVwYrmFZQ" %}
Concise introduction to recursion. Source: Colt Steele
{% endembed %}

Recursion means a function calling itself. Certain classes of algorithm problems, especially those involving trees, graphs and dynamic programming are easier solved with recursion than with iteration (i.e. loops).

Take the [Fibonacci problem](https://leetcode.com/problems/fibonacci-number/) for example, where our goal is to find `fib(n)` where `fib(n)` is defined as `fib(n-1) + fib(n-2)`. This is much more easily modelled with recursion than iteration. To model this problem with iteration we would have to calculate how many of each Fib number between 0 and `n` to add together, which can be challenging.

```javascript
const fib = (n) => {
  // Every recursive function has "base case" to stop recursion from going forever
  if (n === 1 || n === 0) {
    return n;
  }
  return fib(n-1) + fib(n-2);
}
```

All problems that can be solved with recursion can also be solved with iteration and vice versa. Sometimes recursive and iterative solutions are equally accessible; sometimes one is much simpler than the other. As we do more recursion problems we will gain intuition for when to use recursion vs iteration.

## Key Concepts

Every recursive function has 2 key components: 1 or more recurrence relations and 1 or more base cases. We can use the function call stack and sometimes even trees (covered in later submodule) to visualise our recursive algorithm.

### Recurrence Relation

Recurrence relations define what we expect our functions to do in relation to themselves, usually passing a subset of data to child functions. For example, the recurrence relation in our Fibonacci example above is the return value `fib(n-1) + fib(n-2)`. Without worrying what `fib(n-1)` and `fib(n-2)` do internally, we expect `fib(n)` to return `fib(n-1) + fib(n-2)`, and if `fib(n)` does that we have solved our problem.

### Base Case

Base cases exist to stop our recursion once they have reached their natural stopping point, for example 0 or the end of a list. Without base cases our recursive functions would recurse infinitely, exhausting the memory and crashing the programs that run them.

In our above Fibonacci example, the base case is when `n === 1` or `n === 0`, because the Fibonacci sequence explicitly defines `fib(1)` as 1 and `fib(0)` as 0. This prevents our function from recursing infinitely.

### Call Stack

In Colt Steele's video above you may hear him talking about "call stacks" from 10:20 onward, which are an important tool to visualise recursive functions (and program execution in general). Call stacks are like the stacks we learn at Rocket, except for function calls. Every time JavaScript calls a function, JavaScript pushes that function to its global call stack. When a function calls a nested child function, JavaScript pushes the child function to the call stack. JavaScript pops functions from the call stack when they and their children have finished execution.

Call stacks help us solve recursion problems because they help us visualise the state of our algorithm at any point of execution. Whenever we are stuck on a recursion problem we can always trace our algorithm by drawing a call stack to systematically find our bug.

### Backtracking

Recursive backtracking is a concept in more advanced recursion problems to explore permutations. Backtracking involves making a move, recursively making more moves, then un-making our original move to try a different move if needed. This 3-step process typically happens inside a loop where we loop through possible moves. Backtracking problems include finding string permutations, maze-solving, sudoku puzzles, and simulating chess.

The following video explains how we can use backtracking to find permutations of a string.

{% embed url="https://www.youtube.com/watch?v=GCm7m5671Ps" %}
Visual explanation of recursive backtracking to find string permutations
{% endembed %}

## Examples

The following examples explore using recursion with common data types seen in recursion problems. Recursion is also often used with trees, but we will explore that in the trees submodule.

### Numbers: Power of Two

#### Problem

[https://leetcode.com/problems/power-of-two/](https://leetcode.com/problems/power-of-two/)

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`. An integer `n` is a power of two, if there exists an integer `x` such that `n === 2^x`.

#### Strategy

At each function call:

1. If `n` is less than 1, return `false`. This is an edge case that LeetCode throws at us.
2. If `n` is 1 or 2, return `true`. This is our base case. If we continuously divide a number that is a power of 2 by 2, we will eventually get 2. At this point we know we have a power of 2.
3. If `n/2` is an odd number, the original `n` is not a power of 2. Return `false`.
4. If `n/2` is even, return `isPowerOfTwo(n/2)`. The recurrence relation will determine if the "rest" of the number is a power of 2.

```javascript
const isPowerOfTwo = (n) => {
  // Base case: If n is less than 1, n is not a power of 2
  if (n < 1) {
    return false;
  }
  
  // Base case: If n is 1 or 2, the original n was a power of 2
  if (n === 1 || n === 2) {
    return true;
  }
  
  // If n/2 is an odd number, return false
  if (n/2 % 2 !== 0) {
    return false;
  }
  
  // Recurrence relation: If n/2 is even, let the recursion decide
  return isPowerOfTwo(n/2);
}
```

### Strings/Arrays: Letter Tile Possibilities

#### Problem

[https://leetcode.com/problems/letter-tile-possibilities/](https://leetcode.com/problems/letter-tile-possibilities/)

You have `n`  `tiles`, where each tile has one letter `tiles[i]` printed on it. Return _the number of possible non-empty sequences of letters_ you can make using the letters printed on those `tiles`.

#### Strategy

To eliminate duplicates, we store our results in a [set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Set) (like hash table with only keys) `sequences` outside of our recursive function calls, and define a helper function `findPossibilities` inside the given function as our recursive function. `findPossibilities` recursively finds all possible sequences and adds them to `sequences`, and in the end we return the number of sequences in `sequences`.

`findPossibilities` has the following logic.

1. If the current sequence is non-empty, add it to `sequences`, in case we have not seen it before
2. Base case: If there are no letters remaining to add to the current sequence, return
   1. Note because we store results in a variable outside `findPossibilities`, `findPossibilities` does not need to return anything
3. For each of the remaining tiles
   1. Add that tile to the current sequence
   2. Recursively find all remaining possibilities after adding that tile.&#x20;
   3. Remove that tile. This is the backtracking step.

`findPossibilities` systematically explores all options and once it finishes we can return our result.

```javascript
/**
 * @param {string} tiles
 * @return {number}
 */
var numTilePossibilities = function(tiles) {
  // Store the possible sequences in a set to ensure no duplicates
  // A set is like a hash table but with only keys
  sequences = new Set();

  // Define helper function to assist with recursion
  // current is an array of tiles chosen so far
  // remaining is an array of remaining tiles
  const findPossibilities = (current, remaining) => {
    // If current is non-empty, it is a valid sequence.
    // Convert it to string and add to sequences.
    if (current.length > 0) {
      sequences.add(current.join(''));
    }

    // Base case: If there are no letters remaining, we have exhausted all possible
    // sequences in this subtree and can return.
    if (remaining === "") {
      return;
    }

    // For each letter in remaining, add it to current and find
    // possibilities that start with letters in the new current.
    for (let i = 0; i < remaining.length; i += 1) {
      current.push(remaining[i]);
      findPossibilities(current, remaining.slice(0, i) + remaining.slice(i + 1));
      // After finding possibilities for new current, reset current
      // by popping the last-added letter, before appending the next
      // letter in remaining. This is the backtracking step.
      current.pop();
    }
  }
    
  // Kick off our search by providing an empty array for current and
  // the original tiles string containing possible letters.
  findPossibilities([], tiles);

  // Return the number of unique sequences that we found from our search.
  return sequences.size;
};
```

## Exercises

Problems through Part 1 use relatively vanilla recursion. Problems from Part 2 onward involve recursive backtracking.

After attempting each problem, find solutions in the Leaderboard tab (HackerRank, may be on left side of page) or Solution or Discuss tabs (LeetCode) on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. Power of Two ([LeetCode](https://leetcode.com/problems/power-of-two/))

### Part 1

1. Power of Three ([LeetCode](https://leetcode.com/problems/power-of-three/))
2. Power of Four ([LeetCode](https://leetcode.com/problems/power-of-four/))
3. Recursive Digit Sum ([HackerRank](https://www.hackerrank.com/challenges/recursive-digit-sum/problem?isFullScreen=true))

### Part 2

1. Letter Tile Possibilities ([LeetCode](https://leetcode.com/problems/letter-tile-possibilities/))
2. Generate Parentheses ([LeetCode](https://leetcode.com/problems/generate-parentheses/))
   1. Hint: Consider [this slide](https://docs.google.com/presentation/d/1rpY5NnOvN7MKVLSI5NoU7LYySGVNRTC9Yptl9mtaXRY/edit#slide=id.g81c439b50b\_0\_93) on how we can prune invalid subtrees.
   2. [Rocket solution code](https://pastebin.com/HMxZjpM7) (Python)
   3. [Rocket solution video](https://youtu.be/MTqylosJ1ow?t=2022) (Python, until 57:25)
3. Combination Sum ([LeetCode](https://leetcode.com/problems/combination-sum/))

### Part 3

1. Combinations ([LeetCode](https://leetcode.com/problems/combinations/))
   1. Hint: Can we use a for loop to generate the first of `k` numbers, use a recursive function to generate the remaining `k-1` numbers, and combine the first and `k-1` numbers after the recursive call?
2. Subsets ([LeetCode](https://leetcode.com/problems/subsets/))
   1. Hint: Same strategy as Combinations

### Part 4

1. Letter Combinations of a Phone Number ([LeetCode](https://leetcode.com/problems/letter-combinations-of-a-phone-number/))
   1. Hint: Same strategy as Combinations
2. Subsets II ([LeetCode](https://leetcode.com/problems/subsets-ii/))
   1. Hint: Consider using a hash table or [JavaScript set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Set) to remove duplicates

### Part 5

1. Permutations ([LeetCode](https://leetcode.com/problems/permutations/))
2. Letter Case Permutation ([LeetCode](https://leetcode.com/problems/letter-case-permutation/))
