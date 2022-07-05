# A.1.7: Graphs

## Learning Objectives

1. Graphs are generalised versions of trees, where edges can be directed or undirected, edges can have weights and there can be cycles
2. Graphs are used to model a wide variety of real-world problems, such as transport networks, social networks, disease networks, communication networks, website networks, e-commerce networks and more.

## Introduction

The following video showcases the types of problems we can model and solve with graphs. We hope this excites you about the potential of graphs!

{% embed url="https://www.youtube.com/watch?v=LFKZLXVO-Dg" %}
Introduction to graphs and the problems we can solve with graphs
{% endembed %}

Graphs are generalised versions of trees, where edges can be directed or undirected, edges can have weights and there can be cycles. All trees are graphs but not all graphs are trees.

Directed edges are like the edges in trees, where they only point in 1 direction. These can be used to represent directed relationships such as follow requests on Instagram or Twitter.&#x20;

Undirected edges are edges that connect nodes regardless of direction. These can be used to represent undirected relationships such as Facebook friendships or 2-way road networks.

Weighted edges are edges with a number associated with them. These can be used to represent metadata about connections between nodes, such as friendship scores between Facebook friends or road distances.

Graph cycles are loops within graphs. Trees have no cycles by definition, and are part of a common subset of graphs called "directed acyclic graphs", meaning graphs with directed edges and no loops.

The following video introduces the above concepts and 3 common ways of representing graphs in code: adjacency matrix, adjacency list and edge list.

{% embed url="https://www.youtube.com/watch?v=eQA-m22wjTQ" %}
Introduction to graphs and how we can represent graphs in code
{% endembed %}

## Representing a Graph

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

## Additional Resources

1. ****[https://pythoninwonderland.wordpress.com/2017/03/18/how-to-implement-breadth-first-search-in-python/](https://pythoninwonderland.wordpress.com/2017/03/18/how-to-implement-breadth-first-search-in-python/)
2. [https://medium.com/tebs-lab/breadth-first-search-and-depth-first-search-4310f3bf8416](https://medium.com/tebs-lab/breadth-first-search-and-depth-first-search-4310f3bf8416)
3. [Intro to Graphs](https://www.youtube.com/watch?v=Pdk8U1r7qvk)****
4. [Graph Representation](https://www.youtube.com/watch?v=WQ2Tzlxl\_Xo)****
5. [BFS](https://www.youtube.com/watch?v=ls4cHglfc0g)****
6. [DFS](https://www.youtube.com/watch?v=qH-mHxkoK0Q)
7. [BFS](https://www.youtube.com/watch?v=T\_m27bhVQQQ)****
8. [BFS vs DFS](https://www.youtube.com/watch?v=62IcXF\_OF3k)****
9. ****[BFS and DFS](https://www.youtube.com/watch?v=TIbUeeksXcI)****
10. **Free Code Camp - Graphs in JavaScript**
    1. [https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=143s](https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=143s)
    2. [https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=430s](https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=430s)
    3. [https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=1753s](https://www.youtube.com/watch?v=tWVWeAqZ0WU\&t=1753s)****
11. How many sandwiches are a salad?

## Exercises

### Part 1

Implement a function that DFS searches a graph for a value and returns a boolean.

Implement a function that BFS searches a graph for a value and returns a boolean.

### Part 2

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

### Part 3

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

### Part 4

1. [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)
2. [https://leetcode.com/problems/shortest-bridge/](https://leetcode.com/problems/shortest-bridge/)
3. [https://leetcode.com/problems/keys-and-rooms/](https://leetcode.com/problems/keys-and-rooms/) (Medium)
4. [https://leetcode.com/problems/redundant-connection/](https://leetcode.com/problems/redundant-connection/) (Medium)
5. [https://leetcode.com/problems/find-the-town-judge/](https://leetcode.com/problems/find-the-town-judge/)
   1. Hint: What additional data structures might be helpful for us to solve this problem?
   2. Rocket solution code: [https://pastebin.com/3N4NUz8G](https://pastebin.com/3N4NUz8G)
   3. Rocket solution video: [https://youtu.be/1xDBSlnUiUE?t=1308](https://youtu.be/1xDBSlnUiUE?t=1308)

### Part 5

1. https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/
2. https://leetcode.com/problems/minesweeper/
3. [https://leetcode.com/problems/all-paths-from-source-to-target/](https://leetcode.com/problems/all-paths-from-source-to-target/) (Medium)
   1. Hint: Would recursion be helpful?
   2. Rocket solution code: [https://pastebin.com/AtwkRjBf](https://pastebin.com/AtwkRjBf)
   3. Rocket solution video: [https://www.youtube.com/watch?v=dUhleIGC-D4](https://www.youtube.com/watch?v=dUhleIGC-D4)
4. [https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/) (Medium)
