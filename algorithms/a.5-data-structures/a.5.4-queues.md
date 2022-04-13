# A.5.4: Queues

![](../../.gitbook/assets/1_axag3gn3s-xjn3dvqw6afw.png)

## Learning Objectives

By the end of this lesson, you should:

- be familiar with queue functionality time and space complexity
- understand the difference between LIFO and FIFO
- understand the python queue class example

## Introduction

Queues are similar to stacks except instead of removing elements from the end of a list, we can only remove elements from the front of a list. Instead of push and pop operations, queues have "enqueue" and "dequeue" operations respectively. Enqueue adds an element to the back of a queue, and dequeue removes an element from the front of a queue. Queues are FIFO- First In First Out.

#### Big-O of Queues

If we think of a list or, even worse, a stack, operations that affect the beginning of the data would run in at least O(n). Remember that in an array, removing something from the front is **O(n)**. We can think of a queue as a doubly linked list so that taking things off the front or the back is always **O(1)**.

## Helpful Resources

1. [This](https://www.youtube.com/watch?v=9Obx8TTQnaY) video is a concise introduction for the motivation and usage of queues.
2. [This](https://www.youtube.com/watch?v=Y7wZO2tMjnY) video is a more detailed introduction to queues and how to use them in Python.
3. Read pages 109-110 in the [Cracking the Coding Interview PDF](../a.0-algorithms-overview.md#resources).

## Queue Class

Notice we Python's built-in `deque` data structure because it supports more efficient popping (dequeuing) of the left-most element than Python Lists.

```python
# We use the built-in Python deque data structure for queues.
# Deque is implemented using linked lists and more efficient
# than Python lists for popping the left-most element.
from collections import deque

class Queue:
  '''
  Define a Queue class that supports the methods
  1) .enqueue(element): Add element to back of queue
  2) .dequeue():        Return element from front of queue
  3) .size():           Return number of elements in queue
  '''
  # self is a reference to the instance that was just created
  def __init__(self):
    self.data = deque()

  # Return optional representation of class in string format
  def __repr__(self):
    return str(self.data)

  def enqueue(self, element):
    print(f"{element} joins the queue")
    self.data.append(element)

  def dequeue(self):
    element = self.data.popleft()
    print(f"{element} leaves the queue")
    return element

  def size(self):
    print(f"Queue contains {len(self.data)} elements")
    return len(self.data)
```

## Linked List Queue Class

From [here](https://www.geeksforgeeks.org/queue-linked-list-implementation/).

```python
class Node:

    def __init__(self, data):
        self.data = data
        self.next = None

# A class to represent a queue

# The queue, front stores the front node
# of LL and rear stores the last node of LL
class Queue:

    def __init__(self):
        self.front = self.rear = None

    def isEmpty(self):
        return self.front == None

    # Method to add an item to the queue
    def EnQueue(self, item):
        temp = Node(item)

        if self.rear == None:
            self.front = self.rear = temp
            return
        self.rear.next = temp
        self.rear = temp

    # Method to remove an item from queue
    def DeQueue(self):

        if self.isEmpty():
            return
        temp = self.front
        self.front = temp.next

        if(self.front == None):
            self.rear = None

# Driver Code
if __name__== '__main__':
    q = Queue()
    q.EnQueue(10)
    q.EnQueue(20)
    q.DeQueue()
    q.DeQueue()
    q.EnQueue(30)
    q.EnQueue(40)
    q.EnQueue(50)
    q.DeQueue()
    print("Queue Front " + str(q.front.data))
    print("Queue Rear " + str(q.rear.data))
```

## Exercises

Please use Python's `deque` data structure to represent queues.

Please fork starter code Repls and attempt solutions there. Feel free to compare with reference solutions after attempting each problem. Have fun!

### Pre-Class

1. [https://replit.com/@neokaiyuan/queues#main.py](https://replit.com/@neokaiyuan/queues#main.py)
   1. Solutions: [https://repl.it/@neokaiyuan/queuessoln#main.py](https://repl.it/@neokaiyuan/queuessoln#main.py)

### Comfortable

1. [https://leetcode.com/problems/task-scheduler/](https://leetcode.com/problems/task-scheduler/)
   1. Hint: This may be solved more efficiently without queues, but see how we can implement it with queues first.
