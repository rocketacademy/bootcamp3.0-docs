# A.1.7: Graphs

## Learning Objectives

1. Graphs are used to model a wide variety of real-world problems, such as transport networks, social networks, disease networks, communication networks, website networks, e-commerce networks and more
2. Graphs are generalised versions of trees, where edges can be directed or undirected, edges can have weights and there can be cycles
3. DFS and BFS are the most common graph traversal algorithms, where we typically track visited nodes to avoid infinite loops

## Introduction

Graphs are used to model a wide variety of real-world problems, such as transport networks, social networks, disease networks, communication networks, website networks, e-commerce networks and more. Graph theory can get complex and is the subject of entire university courses; in this submodule we will introduce the basics that are relevant for algorithm interviews.

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

## DFS and BFS for Graphs

DFS and BFS are the most common graph traversal algorithms. Unlike trees, which are a type of graph with no cycles (called "acyclic" graphs), for graphs with cycles we will need to track visited nodes to avoid infinite loops.&#x20;

Not all graph problems require DFS or BFS-like traversal algorithms, although many will. Some simpler graph problems can be solved by analysing edges without DFS or BFS.

DFS is generally a "simpler" algorithm because it involves recursion with no additional data structures beyond our graph. BFS requires the use of a queue to visit nodes in increasing distance order from the source node.

We would typically use DFS when we need to visit all nodes in the graph, and BFS when we wish to find the shortest path between nodes in the most efficient manner.

### DFS

The following video explains the logic for DFS in graphs. Notice the use of a hash table to track which nodes have been visited to avoid cycles.

{% embed url="https://www.youtube.com/watch?v=PMMc4VsIacU" %}
Walkthrough of DFS logic for graphs
{% endembed %}

The following is DFS code for graphs in JavaScript. Notice it is similar to DFS for trees except we track visited nodes, and we reference a hash table that represents our graph to find neighbours.

```javascript
// Represent graph in hash table with nodes as keys and neighbouring nodes as values
const graph = {
  a: ["b", "c"],
  b: ["d"],
  c: ["e"],
  d: ["f"],
  e: [],
  f: [],
};

// Track nodes we have visited in hash table
const visited = {};

const dfs = (currNode) => {
  // End this path if we reach visited node
  if (visited[currNode]) {
    return;
  }

  // Mark current node visited
  visited[currNode] = true;

  // Perform DFS on each neighbour
  for (const neighbour of graph[currNode]) {
    dfs(neighbour);
  }
};

// Start DFS on source node
dfs("a");
```

### BFS

Visit each node in graph in increasing distance from source node. This is similar to the level-order tree traversal algorithm. Notice the use of a hash table to track which nodes have been visited to avoid cycles.

{% embed url="https://www.youtube.com/watch?v=xlVX7dXLS64" %}
Walkthrough of BFS logic for graphs
{% endembed %}

The following is BFS code for graphs in JavaScript. Notice it is similar to BFS for N-ary trees except we track visited nodes, and we reference a hash table that represents our graph to find neighbours.

```javascript
// Represent graph in hash table with nodes as keys and neighbouring nodes as values
const graph = {
  a: ["b", "c"],
  b: ["d"],
  c: ["e"],
  d: ["f"],
  e: [],
  f: [],
};

// Track nodes we have visited in hash table
const visited = {};
// Track upcoming nodes to visit in a queue (represented by array for simplicity)
const queue = [];

const bfs = (sourceNode) => {
  // Mark source node as visited
  visited[sourceNode] = true;
  // Initialise BFS by adding source node to queue
  queue.push(sourceNode);

  while (queue.length > 0) {
    // Visit next node in queue
    const currNode = queue.shift(0);
    for (const neighbour in graph[currNode]) {
      // Only add neighbour to queue if not visited yet
      if (!visited[neighbour]) {
        // Mark neighbour as visited
        visited[neighbour] = true
        // Add neighbour to queue
        queue.push(neighbour);
      }
    }
  }
};

// Start BFS on source node
bfs("a");
```

## Exercises

### Pre-Class

1. Find Center of Star Graph ([LeetCode](https://leetcode.com/problems/find-center-of-star-graph/))
   1. Hint: This does not require graph traversal

### Part 1

1. Find the Town Judge ([LeetCode](https://leetcode.com/problems/find-the-town-judge/))
   1. Hint: What additional data structures might be helpful for us to solve this problem?
   2. Hint: This does not require graph traversal
   3. [Rocket solution code](https://pastebin.com/3N4NUz8G) (Python)
   4. [Rocket solution video](https://youtu.be/1xDBSlnUiUE?t=1308) (Python)

### Part 2

1. Find if Path Exists in Graph ([LeetCode](https://leetcode.com/problems/find-if-path-exists-in-graph/))
   1. Hint: This requires graph traversal

### Part 3

1. Keys and Rooms ([LeetCode](https://leetcode.com/problems/keys-and-rooms/)) (Medium)

### More Comfortable

1. All Paths from Source to Target ([LeetCode](https://leetcode.com/problems/all-paths-from-source-to-target/)) (Medium)
   1. Hint: Would recursion be helpful?
   2. [Rocket solution code](https://pastebin.com/AtwkRjBf) (Python)
   3. [Rocket solution video](https://www.youtube.com/watch?v=dUhleIGC-D4) (Python)
2. Redundant Connection ([LeetCode](https://leetcode.com/problems/redundant-connection/)) (Medium)
3. Minimum Number of Vertices to Reach All Nodes ([LeetCode](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/)) (Medium)
4. Number of Islands ([LeetCode](https://leetcode.com/problems/number-of-islands/)) (Medium)

## Additional Resources

1. [BFS vs DFS written explanation](https://medium.com/tebs-lab/breadth-first-search-and-depth-first-search-4310f3bf8416) in blog post
2. [Graph Algorithms for Technical Interviews video](https://youtu.be/tWVWeAqZ0WU) by freeCodeCamp
