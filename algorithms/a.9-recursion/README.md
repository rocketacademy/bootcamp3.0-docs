# A.9: Recursion

### Introduction

For solving certain types of algorithm problems we'll want to repeat an action several times, as in a loop- the syntax keyword `for` in JavaScript and Python. There is another syntax to repeat some code a set number of times called recursion. Recursion is a function that calls itself. Specifically we we need to add some features inside the function so that it stops after _n_ times.

We'll see through some examples where a given concept or code is expressed more elegantly (not necessarily more simply) in the format of a function that calls itself. This may be preferable to writing the code using the `for` keyword to make a loop.

```python
def say_something
    print("hello")
    say_something() # keep repeating this function forever
```

#### New Vocabulary for Loops

When we introduce this new syntax for repeating some code with a function that calls itself, we'll still call that a loop, but make a new distinction between what kind of loop it is.

**Iterative vs. Recursive**

From now on we'll refer to writing "loops" (code that repeats a given number of times) either as _**iteratively**_, that is using something like the `for` keyword or any of the other ways we wrote repeating code before- `while`, `map`, etc. **or** we'll refer to the loop as _**recursive**_- using a function that calls itself.

#### Recursive Vocabulary

There are 2 concepts to remember with recursion.

1. Recurrence relation
   1. When our function calls itself, what do we expect to be returned by that function?
2. Base case
   1. When does our function stop calling itself and return a value that does not depend on the function calling itself again?
   2. In our Fibonacci example, our base cases would be that `Fib(0) == 1` and `Fib(1) == 1`.
   3. Without base cases, our recursive function would recurse infinitely and result in an infinite loop.

{% embed url="https://youtu.be/lMBVwYrmFZQ" %}

### Background on Recursion

The history of recursion is deeply tied to the invention of Turing's theoretical computer. The word recursion is not just a topic in Computer Science but also a topic in mathematical logic. So the concept of recursion is deeper than simply a function that calls itself. It is any construct or system that is defined in terms of itself. Implementations of the concept of recursion include a [JavaScript interpreter written in JavaScript](./#part-2), or a [quine](<https://en.wikipedia.org/wiki/Quine_(computing)>), a program whose purpose is to print out it's own code. However, the purposes of Rocket's algorithms content we can assume the word recursion to mean a loop.

### Example - Simple Loops

#### Infinite Recursive Loop

Given this infinite iterative loop:

```python
count = 0
while True:
    print(f'count: {count}')
    count += 1
```

Let's implement the same loop in recursion.

```python
def loop_count_times(count: int) -> None
    print(f'count: {count}')
    new_count = count + 1
    loop_count_times(new_count)

loop_count_times(0)   # start the loop at zero, will increase forever
```

**Rules of Recursive Functions so Far**

1. Function must call itself

### Example - Base Cases

The first important property of recursion that must be implemented is the "base case". This simply means the condition for stopping what would otherwise be the infinite recursing loop.

In a function context the base case always has to do with the function returning or not. A base case that satisfies the base condition can return, or exit out of that recursive call.

#### Base Case - How to End the Loop

Given this iterative loop:

```python
count = 5
while count != 0:
    print(f'count: {count}')
    count -= 1
```

Let's implement the same loop in recursion.

```python
def loop_count_times(count: int) -> None
    print(f'count: {count}')
    if count == 0:
        return
    new_count = count - 1
    loop_count_times(new_count)

loop_count_times(5)
```

On line 3 s the Base Case. We need to be able to write code that, in contrast to the infinite example above, knows when to end the loop.

Note that as the function gets called over and over again we can define function calls 3,4 and 5 as dealing with an ever-reducing set of data.

**Rules of Recursive Functions so Far**

1. Function must call itself
2. Must have a base case to say when to stop.
3. Called with a smaller piece of the original data every "iteration".

#### Base Case with Parameters

How can we implement a recursive loop that counts up instead of down?

Given this iterative loop:

```python
count = 0
while count < 5:
    print(f'count: {count}')
    count += 1
```

Let's implement the same loop in recursion.

```python
def loop_count_times(max: int, count: int) -> None
    print(f'count: {count}')
    if count == max:
        return
    new_count = count + 1
    loop_count_times(max, new_count)

loop_count_times(5,0)
```

Also note that it is a convention to have the base case at the top of the function. We actually call the function at the end once just to check the count value and return / end the loop, even though it isn't affecting the counter- it will just end after the check fails.

### Example - Return Values

So far having a base case condition that exits the loop is relatively simple. Now we'll look at functions that return a value. This turns out to make tracking the execution of the recursive function much, much more difficult. When first learning about recursion this tracing of the execution context is one of the main difficulties.

This exposes the other major behaviour of a recursive function that returns a value: each step of the function deals with a smaller and smaller piece of the data. The return value of the function builds that data back up piece by piece.

**Reverse a String - Iterative**

How do we write recursive functions that returns values?

![Demonstration of recursive string reverse from here: https://towardsdatascience.com/finding-a-recursive-solution-184784b0aea0](../../.gitbook/assets/recurse_string.gif)

Given this iterative loop:

```python
def reverse_iter(word: str) -> str:
    result = ''
    for char in word:
        result = char + result
    return result

result = reverse_iter('hello') # olleh
```

**Reverse a String - Recursive**

Let's implement the same loop in recursion.

```python
def reverse_recurse(word: str) -> str:

  if len(word) == 0:
    return ''

  last_letter = word[-1] # letter at the end of the word
  rest = word[:-1] # the rest of the string except the last letter

  # get the result of reversing every other letter before the current one
  recurse_result = reverse(rest)

  new_string = last_letter + recurse_result # arrange the last letter in front

  return new_string

result = reverse_recurse('hello') # olleh
```

**Full Commentary Version**

Run this version and follow the call stack to see where each part of the function branches off to recurse and comes back.

```python
def reverse_recurse(string: str) -> str:
    print(f'current word: {string}')

    if len(string) == 0:
        print('========== reached the base case')
        return ''

    last_letter = string[-1] # letter at the end of the string
    rest = string[:-1] # the rest of the string except the last letter

    print(f'^^^ about to recurse. this is rest: {rest}')
    # get the result of reversing every other letter before the current one
    recurse_result = reverse_recurse(rest)

    print(f"### we're back. this was string function param: {string}")

    new_string = last_letter + recurse_result # arrange the last letter in front

    print(f'recurse result: >> {recurse_result} <<')
    print(f'putting last letter on first: {last_letter}')

    return new_string

result = reverse_recurse('hello') # olleh
print(f'reverse result: {result}')
```

**Compact Refactor**

The common style of recursive functions is to write all of the intermediate values inline with the return.

```python
def reverse_recurse_compact(word: str) -> str:
    if len(word) == 0:
        return ''
    else:
        return word[-1] + reverse_recurse_compact(word[:-1])

result = reverse_recurse_compact('hello')
```

**Gather Values**

The key to understanding the control flow of this function is to understand that the values are gathering back up and the function returns back to what will become `result`. Our final goal is to have the accumulated total value inside of `result` - each time we get a new return value we get to put together another piece of the answer.

**Rules of Recursive Functions so Far**

1. Function must call itself
2. Must have a base case to say when to stop.
3. Called with a smaller piece of the original data.
4. Function return values accumulate previously gathered values, our recursive function must compile these values.

### Examples - Linked List

A nice way to see how recursion applies to code we might write is to look at converting some code that we had previously written as iterative. One ongoing challenge will be to understand what makes a given problem appropriate for a recursive solution or not. Many propblems ca be written either way. In these ideal conversions between iterative and recursive try to see how the paradigm of "repeat the sme action (function) over and over again for a constantly reducing set of data" applies to these linked list examples.

#### Print Out Values

**Iterative Linked List**

We can write certain linked list methods as recursive insterad of iterative.

Given a normal linked list class:

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.nextnode = None
```

We can put values inside the list:

```python
head = Node(1)
head.nextnode = Node(2)
head.nextnode.nextnode = Node(3)
head.nextnode.nextnode.nextnode = Node(4)
head.nextnode.nextnode.nextnode.nextnode = Node(5)
head.nextnode.nextnode.nextnode.nextnode.nextnode = Node(3)
head.nextnode.nextnode.nextnode.nextnode.nextnode.nextnode = Node(3)
```

**Recursive Printing of LL**

```python
def display_ll(node):
    while node:
        print(node.value, end=" --> ")
        node = node.nextnode
    print(None)

display_ll(head) # 1 --> 2 --> 3 --> 4 --> 5 --> 3 --> 3 --> None
```

We can write the same LL algorithm recursively:

```python
def display_ll_recursive(node):

    if node == None:
      return

    print(node.value, end=" --> ")
    display_ll_recursive(node.nextnode)

display_ll_recursive(head) # 1 --> 2 --> 3 --> 4 --> 5 --> 3 --> 3 --> None
```

This code gives a hint that some kinds of algorithms are more elegantly expressed in terms of recursion.

#### Recursive Find Length

**Iterative Find Length**

This slight modification on the above would find the length of the list:

```python
def length(node):
    length=0
    while node:
        length += 1
        node = node.nextnode

result = length(head)
print(result)
```

**Recursive Find Length**

Now we can modify the above recursive function to return the list length:

```python
def length_recursive(node):

    if node == None:
      return 0

    return length_recursive(node.nextnode) + 1

result = length_recursive(head)
print(result)
```

**Full Commentary Recursive Length**

Follow the comments to see where the return values recurse down and back up, so that a value can be returned

```python
def length_recursive(node):

    if node == None:
      print(f"### we're going back. this is None")
      return 0

    print(f'recursing down. node value is: {node.value}')
    accumulated_length = length_recursive(node.nextnode)
    print(f'we got a return value. current length is: {current_length}')

    current_node_count = 1
    current_total = current_node_count + accumulated_length

    print(f"we got a return value. current total is: {current_total}")

    return current_total

result = length_recursive(head)
print(result)
```

#### Adding to End

**Iterative Adding to End**

Given this iterative way to find the end of the list and add a node:

```python
def add(node, newnode):
    ''' Adds a new node object at the end of the ll '''
    # Go to the end of the existing LL
    while node:
      # Keep track of the last node with prevnode
      prevnode = node
      node = node.nextnode
    # Attach newnode to the final prevnode
    prevnode.nextnode = newnode

add(head, Node(3))
display_ll(head)
```

**Recursive Adding to End**

This can also be implemented using recursion:

```python
def addRecursive(node, newnode):
    ''' Adds a new node object at the end of the ll '''
    if (node == None):
        return newnode
    else:
        node.next = addRecursive(node.nextnode, newnode)
    return node

addRecursive(head, Node(3))
display_ll(head)
```

### Exercises

#### Instructions

We will be working through these exercises over multiple days. Please see your batch schedule for which exercises to do on which days.

We will complete the Learn Python Recursion Repl. Please start with [this empty starter repl](https://repl.it/@kaiyuanneo/Recursion#main.py). RA created this repl by copying the @Learnpython Recursion Repl and removing answers.

1. Pressing the Play button (`Ctrl+Enter` on Windows, `Cmd+Enter` on Mac) in Repl to run `main.py` will execute all problems against the provided test cases.
2. To limit the problems that Repl executes at any given time, see instructions in the Repl document to edit the `problems` array in the `main` function.
3. See [here](https://docs.repl.it/repls/editor) for useful keyboard shortcuts in Repl.

#### Reference Solutions

Please attempt to solve each problem on your own before reviewing each problem's answer. If you find yourself stuck and unable to proceed, feel free to learn from sample answers for each problem in the [@Learnpython Recursion Repl](https://repl.it/@Learnpython/Recursion). Note there are multiple ways to solve each problem and the sample answers represent only 1 way.

#### Part 1

1. Factorial
2. Bunny Ears
3. Fibonacci
4. Bunny Ears 2
5. Triangle
6. Sum Digits
7. Count 7
8. Count 8
9. Power N
10. Count X
11. Count Hi

#### Part 2

1. Change XY
2. Change Pi
3. No X
4. Array 6
5. Array 11
6. Array 220
7. All Star
8. Pair Star
9. End X
10. Count Pairs

#### Part 3

1. Count ABC
2. Count 11
3. String Clean
4. Count Hi 2
5. Paren Bit
6. Nest Paren
7. Str Count
8. Str Copies
9. Str Dist
   1. [RA Solution Code](https://pastebin.com/xVFqzPrj)
   2. [FTBC3 Solution Video](https://youtu.be/CnKOLqJ2THc?t=3092)

### Optional Reading

1. Fast Exponentiation. What would be the time complexity of an algorithm to calculate the value of `2^n`, where `n` is an input value? A naïve solution would be to write a for loop to multiply 2 by itself `n` times, which would run in `O(n)` time complexity. However, if we take the notion that `2^2^2 == 2^4` , and `2^4^2 == 2^8`, we can see that we can calculate `2^n` in many fewer operations than `n`, on the order of `log(n)`, with time complexity of `O(logn)`. Fast exponentiation can be implemented relatively easily with recursion. Programming languages typically implement exponent operators using fast exponentiation.
   1. [https://en.wikipedia.org/wiki/Exponentiation_by_squaring#Basic_method](https://en.wikipedia.org/wiki/Exponentiation_by_squaring#Basic_method)

## Further Reading

https://towardsdatascience.com/finding-a-recursive-solution-184784b0aea0

FreeCodeCamp's Intro to Recursion: [https://www.freecodecamp.org/news/quick-intro-to-recursion/](https://www.freecodecamp.org/news/quick-intro-to-recursion/)

https://www.youtube.com/watch?v=AfBqVVKg4GE

https://www.youtube.com/watch?v=mz6tAJMVmfM

Stanford's Intro to Recursion: [https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1206/lectures/intro-to-recursion/](https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1206/lectures/intro-to-recursion/)
