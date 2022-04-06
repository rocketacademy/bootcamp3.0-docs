# A.5.3: Stacks

![stack meme](../../.gitbook/assets/stack_meme.jpeg)

## Learning Objectives

By the end of this lesson, you should:

* be familiar with stack functionality time and space complexity
* understand the difference between LIFO and FIFO
* understand the python stack class example

## Introduction

SImilar to hash tables, we are going to be employing the concept of a stack data structure to work with certain kinds of data. A stack is a data structure that supports adding and removing only from the end/top of the stack. They are often referred to as a FILO \(first in last out\) or LIFO \(last in first out\) data structure.

#### History of Stacks

When the first computer was invented on paper by Alan Turing, the first in, last out behaviour of storing data was one of the mechanisms that was theorized to be needed in order to create a computer. Stacks are therefore one of the first and simplest data structures to be discussed in the context of computer science. Data access with LIFO behaviour is something that naturally shows up in many fundamental places in computer science as we'll also see in function call stacks below. In our modern context it may not make sense to strictly define a list-like data structure with less features than an actual Python list, but because the LIFO behaviour is a key concept in computer science we consider a Stack as distinct from an array.

Within this historical context, arrays can do everything a list can do, but stacks cannot do everything an array can do, since they were invented/implemented before arrays.

#### Big-O of Stacks

Even when using a Python `list` we'll limit ourselves to only writing code that uses the stack operations. This means that our stack code will have a constant **O\(1\)** time complexity.

### LIFO

![](../../.gitbook/assets/stack-gif.gif)

We can think of the stack data structure like a stack of pancakes- we can only add and remove pancakes from the top of the stack, but we cannot add or remove from anywhere else in the stack lest we damage the pancakes. You may notice that arrays already provide the functionality of stacks through list `append` and `pop` methods. Indeed the functionality of stacks is a subset of arrays', but the concepts behind why and how we use stacks may be new to us.

### JavaScript Call Stacks

A recurring example of stack data structure usage is inside the Chrome JavaScript debugger tools- the function call stack. In JavaScript function execution is tracked using a stack data structure. Watch this video to see how function calls tie in with a stack's LIFO behaviour.

{% embed url="https://www.youtube.com/watch?v=W8AeMrVtFLY" %}

## Stack Class Example

To be complete this is an implementation of a stack data structure that defines only the stack methods- `push`, `pop`, `peek` and `size`. Note the use of a list on line 10 to store the actual data.

```python
class Stack:
  '''
  Define a Stack class that supports the methods
  1) .push(element): Push element onto stack
  2) .pop():         Pop (remove) and return element from top of stack
  3) .peek():        Return element from top of stack without popping
  4) .size():        Return number of elements in stack
  '''
  def __init__(self):
    self.data = []

  # Return optional representation of class in string format
  def __repr__(self):
    return str(self.data)

  def push(self, element):
    print(f"Pushed {element} onto stack")
    self.data.append(element)

  def pop(self):
    element = self.data.pop()
    print(f"Popped {element} from stack")
    return element

  def peek(self):
    if not self.data:
      print("This stack is empty!")
      return None
    print(f"The top element in the stack is {self.data[-1]}")
    return self.data[-1]

  def size(self):
    print(f"Stack contains {len(self.data)} elements")
    return len(self.data)

# Create empty stack
s = Stack()

# Push elements onto stack
for i in range(10):
  s.push(i) # <-- Pushed {i} onto stack
print(s) # <-- [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Pop element from stack
e = s.pop() # <-- Popped 9 from stack
print(s) # <-- [0, 1, 2, 3, 4, 5, 6, 7, 8]
print(e) # <-- 9

# Peek at top element in stack
e = s.peek() # <-- The top element in the stack is 8
print(e) # <-- 8

# Get the size of the stack
size = s.size() # <-- Stack contains 9 elements
print(size) # <-- 9
```

## Other Examples of Stack LIFO Behaviour

1. Undo and redo features in most text editors.
2. `git stash` functionality in Git to temporarily save changes without committing.
3. Browser history

## Exercises

Feel free to use the Python List to perform Stack operations. Once you've attempted each problem, please review solutions in the Discuss tab on that problem's page.

### Pre-Class

1. [Reverse a string.](https://leetcode.com/problems/reverse-string/)
   1. Only use a list, `push` and `pop`!
2. [https://leetcode.com/problems/crawler-log-folder/](https://leetcode.com/problems/crawler-log-folder/)
   1. RA solution video: [https://youtu.be/y---RCHCdD4?t=2460](https://youtu.be/y---RCHCdD4?t=2460)
3. [https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)
   1. RA strategy video: [https://youtu.be/y---RCHCdD4?t=4613](https://youtu.be/y---RCHCdD4?t=4613)

### Part 1

1. [https://leetcode.com/problems/backspace-string-compare/](https://leetcode.com/problems/backspace-string-compare/)
2. [https://leetcode.com/problems/make-the-string-great/](https://leetcode.com/problems/make-the-string-great/)
   1. RA strategy video: [https://youtu.be/y---RCHCdD4?t=4457](https://youtu.be/y---RCHCdD4?t=4457)

### Part 2

1. [https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
   1. RA solution code: [https://pastebin.com/qGbG1BAN](https://pastebin.com/qGbG1BAN)
2. [https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)

### More Comfortable

1. [https://leetcode.com/problems/design-a-stack-with-increment-operation/](https://leetcode.com/problems/design-a-stack-with-increment-operation/)
2. [https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/)
3. [https://leetcode.com/problems/score-of-parentheses/](https://leetcode.com/problems/score-of-parentheses/)
4. [https://leetcode.com/problems/daily-temperatures/](https://leetcode.com/problems/daily-temperatures/)
5. [https://leetcode.com/problems/validate-stack-sequences/](https://leetcode.com/problems/validate-stack-sequences/)

## Further Reading

1. [This](https://www.youtube.com/watch?v=k1PX5LxFfTo) is a concise, high-level overview of the stack data structure concept, methods, and use cases.
2. [This](https://www.youtube.com/watch?v=F1F2imiOJfk) is a slightly more detailed video covering the same concepts.
3. Read pages 108-109 in the [Cracking the Coding Interview PDF](../a.0-algorithms-overview.md#resources).
4. [FTBC3 class video ](https://youtu.be/y---RCHCdD4?t=559)introducing Stacks.

#### Pushdown Automata

Turing's theoretical computers used stacks as part of it's basic behaviours. See more about them here: [https://en.wikipedia.org/wiki/Pushdown_automaton](https://en.wikipedia.org/wiki/Pushdown_automaton)
