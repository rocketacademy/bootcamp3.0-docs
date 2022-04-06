# A.9.1: Recursive Backtracking

## Introduction

Backtracking is a way to explore valid possible subtrees or permutations. Problems that use backtracking are such things as: permutations of strings, maze solving, sudoku puzzles, chess move validity.

In certain problems such as [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/), backtracking may mean we can avoid recursively exploring every subtree. In other problems such as [Permutations](https://leetcode.com/problems/permutations/), this may mean we explore every subtree, and "backtrack" when we have exhausted each subtree.

#### Permutations

{% embed url="https://www.youtube.com/watch?v=Nabbpl7y4Lo" %}

#### String Permutations

{% embed url="https://www.youtube.com/watch?v=GCm7m5671Ps" %}

#### Matched Parens

{% embed url="https://www.youtube.com/watch?v=sz1qaKt0KGQ" %}

#### Maze Solving

{% embed url="https://www.youtube.com/watch?v=gBC_Fd8EE8A" %}

#### Sudoku (harder problem)

{% embed url="https://www.youtube.com/watch?v=Zq4upTEaQyM" %}

#### N-Queens (harder problem)

{% embed url="https://www.youtube.com/watch?v=wGbuCyNpxIg" %}

## Find Tile Permutations Example

You have a set of tiles, where each tile has one letter tiles\[i] printed on it. Return the number of possible non-empty sequences of letters you can make.

Input: “AAB”, Output: 8. Explanation: "A", "B", "AA", "AB", "BA", "AAB", "ABA", "BAA".

```python
def numTilePossibilities(self, tiles: str):
    # Store the possible sequences in a set to ensure no duplicates
    sequences = set()
    
    # Perform depth-first search
    # current is an array of tiles chosen so far
    # remaining is an array of remaining tiles
    def find_possibilities(current, remaining):
        # If current is non-empty, it is a valid sequence.
        # Convert it to string and add to sequences.
        if current != []:
            sequences.add("".join(current))
            
        # If there are no letters remaining, we have exhausted all possible
        # sequences in this subtree and can return.
        if remaining == "":
            return
        
        # For each letter in remaining, add it to current and find
        # possibilities that start with letters in the new current.
        for i in range(len(remaining)): 
            current.append(remaining[i])
            find_possibilities(current, remaining[:i] + remaining[i+1:])
            # After finding possibilities for new current, reset current
            # by popping the last-added letter, before appending the next
            # letter in remaining. This is the backtracking step.
            current.pop() 
    
    # Kick off our search by providing an empty array for current and 
    # the original tiles string containing possible letters.
    find_possibilities([], tiles)
    
    # Return the number of unique sequences that we found from our search.
    return len(sequences)
```

## Exercises

### Pre-Class

1. [https://leetcode.com/problems/generate-parentheses/](https://leetcode.com/problems/generate-parentheses/)
   1. Hint: Consider [this slide](https://docs.google.com/presentation/d/1rpY5NnOvN7MKVLSI5NoU7LYySGVNRTC9Yptl9mtaXRY/edit#slide=id.g81c439b50b\_0\_93) on how we can prune invalid subtrees.
   2. Rocket Academy solution code: [https://pastebin.com/HMxZjpM7](https://pastebin.com/HMxZjpM7)
   3. Rocket Academy solution video: [https://youtu.be/MTqylosJ1ow?t=2022](https://youtu.be/MTqylosJ1ow?t=2022) until 57:25

### Part 1

1. [https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)
2. [https://leetcode.com/problems/letter-case-permutation/](https://leetcode.com/problems/letter-case-permutation/)
3. [https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
4. [https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

## Further Reading

[Geeks for Geeks article](https://www.geeksforgeeks.org/backtracking-introduction/#:\~:text=Backtracking%20is%20an%20algorithmic%2Dtechnique,reaching%20any%20level%20of%20the). https://brilliant.org/wiki/recursive-backtracking/ https://www.hackerearth.com/practice/basic-programming/recursion/recursion-and-backtracking/tutorial/
