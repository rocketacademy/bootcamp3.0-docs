# A.5.7: Graphs

## A.5.7: Graphs

### Introduction

Graphs are a more generalised version of trees that can have "edges" that point in forward, backward, and both directions. All trees are graphs but not all graphs are trees.

#### Introduction to Graphs & Graph Problems

{% embed url="https://www.youtube.com/watch?v=eQA-m22wjTQ" %}

{% embed url="https://www.youtube.com/watch?v=LFKZLXVO-Dg" %}

### Representing a Graph

As described in the video above, there are many ways to represent a graph. We will be using an _adjacency list_ to represent our graphs.

```python
graph = {
  'a' : ['b','c'],
  'b' : ['d'],
  'c' : ['e'],
  'd' : ['f'],
  'e' : [],
  'f' : []
}
```

## Traversal Algorithms

### Depth First Search

For visiting every node in a graph. This code looks a little bit different from our tree DFS code.

{% embed url="https://www.youtube.com/watch?v=PMMc4VsIacU" %}

{% embed url="https://www.youtube.com/watch?v=7fujbpJ0LB4" %}

```python
graph = {
  'a' : ['b','c'],
  'b' : ['d'],
  'c' : ['e'],
  'd' : ['f'],
  'e' : [],
  'f' : []
}

visited = {}

def dfs(at):
  if at in visited: return

  visited[at] = True
  print(f'at: {at}')

  neighbors = graph[at]

  for next_node in neighbors:
    dfs(next_node)

dfs('a')
```

### Breadth First Search

For visiting every node in a graph. This one visits each node in order of distance. This is equivalent to the level-order tree traversal algorithm we've seen.

{% embed url="https://www.youtube.com/watch?v=oDqjPvD54Ss" %}

{% embed url="https://www.youtube.com/watch?v=xlVX7dXLS64" %}

```python
graph = {
  'a' : ['b','c'],
  'b' : ['d'],
  'c' : ['e'],
  'd' : ['f'],
  'e' : [],
  'f' : []
}
visited = {} # List to keep track of visited nodes.
queue = []     #Initialize a queue

def bfs(visited, graph, node):
  visited[node] = True
  queue.append(node)

  while queue:
    s = queue.pop(0)
    print (s, end = " ")

    for neighbour in graph[s]:
      if neighbour not in visited:
        visited.append(neighbour)
        queue.append(neighbour)

# Driver Code
bfs(visited, graph, 'a')
```

## Graph Problems

### DFS Path Finding (maze)

{% embed url="https://www.youtube.com/watch?v=W9F8fDQj7Ok" %}

### BFS Shortest Path

{% embed url="https://www.youtube.com/watch?v=KiCBXu4P-2Y" %}

### Exercises

#### Part 1

Implement a function that DFS searches a graph for a value and returns a boolean.

Implement a function that BFS searches a graph for a value and returns a boolean.

#### Part 2

Implement path finding DFS that prints out a path in the graph from 'a' to 'e'.

```python
graph = {
  'a' : ['b','c'],
  'b' : ['d'],
  'c' : ['e'],
  'd' : ['f'],
  'e' : [],
  'f' : []
}
```

#### Part 3

Implement shortest path BFS that prints out or returns the shortest path in the graph from 'a' to 'e':

```python
graph = {
  'a' : ['b','c'],
  'b' : ['d'],
  'c' : ['e'],
  'd' : ['f'],
  'e' : [],
  'f' : []
}
```

#### Part 4

1. [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)
2. [https://leetcode.com/problems/shortest-bridge/](a.5.7-graphs.md#a.5.7-graphs)
3. [https://leetcode.com/problems/keys-and-rooms/](https://leetcode.com/problems/keys-and-rooms/) (Medium)
4. [https://leetcode.com/problems/redundant-connection/](https://leetcode.com/problems/redundant-connection/) (Medium)
5. [https://leetcode.com/problems/find-the-town-judge/](https://leetcode.com/problems/find-the-town-judge/)
   1. Hint: What additional data structures might be helpful for us to solve this problem?
   2. RA solution code: [https://pastebin.com/3N4NUz8G](https://pastebin.com/3N4NUz8G)
   3. RA solution video: [https://youtu.be/1xDBSlnUiUE?t=1308](https://youtu.be/1xDBSlnUiUE?t=1308)

-

#### Part 5

1. https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/
2. https://leetcode.com/problems/minesweeper/
3. [https://leetcode.com/problems/all-paths-from-source-to-target/](https://leetcode.com/problems/all-paths-from-source-to-target/) (Medium)
   1. Hint: Would recursion be helpful?
   2. RA solution code: [https://pastebin.com/AtwkRjBf](https://pastebin.com/AtwkRjBf)
   3. RA solution video: [https://www.youtube.com/watch?v=dUhleIGC-D4](https://www.youtube.com/watch?v=dUhleIGC-D4)
4. [https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/) (Medium)

## Further Reading

[https://pythoninwonderland.wordpress.com/2017/03/18/how-to-implement-breadth-first-search-in-python/](https://pythoninwonderland.wordpress.com/2017/03/18/how-to-implement-breadth-first-search-in-python/)

[https://medium.com/tebs-lab/breadth-first-search-and-depth-first-search-4310f3bf8416](https://medium.com/tebs-lab/breadth-first-search-and-depth-first-search-4310f3bf8416)

#### Intro to Graphs

https://www.youtube.com/watch?v=Pdk8U1r7qvk

**Graph Representation**

https://www.youtube.com/watch?v=WQ2Tzlxl\_Xo

**BFS**

https://www.youtube.com/watch?v=ls4cHglfc0g

**DFS**

https://www.youtube.com/watch?v=qH-mHxkoK0Q

**BFS**

https://www.youtube.com/watch?v=T\_m27bhVQQQ

**BFS vs DFS**

https://www.youtube.com/watch?v=62IcXF\_OF3k

**BFS and DFS**

https://www.youtube.com/watch?v=TIbUeeksXcI

**Free Code Camp - Graphs in JavaScript**

https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=143s

https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=430s

https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=1753s

**How many sandwiches are a salad?**

{% embed url="https://www.youtube.com/watch?vz=vJZsH8Dsf8U" %}
