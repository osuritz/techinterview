# Algorithms — Tree Traversal: Breadth-First Search
Unlike [Depth-First Search](tree-dfs) which uses a stack for traversal, the Breadth-First-Search algorithm uses a *queue* to store
intermediate results as it traverses the graph.
It has the **extremely useful property that**, if all of the edges in a graph are either unweighted or all the same weight,
then the first time a node is visited **is the shortest path from the source node to that node**.

## When to Use
* When looking for the shortest path in a graph.
* Beginning state & ending state and how fast to get there
  - How deep?
  - How many levels?
  - How many transformations?


## Sample Implementation
```
//TODO
```


## Example Problems
### Print a Binary Tree in level order (Easy)
Printing a binary tree in level order is a variant of BFS and uses two queues: one to store the current level items and a second queue to store
the children of the current level items.
Once the first queue is empty, we swap the current- and next-level queues and keep going.
http://leetcode.com/2010/09/printing-binary-tree-in-level-order.html

### Word Ladder (Medium)
A series of transformations from *beginWord* to *endWord* via a list of words (dictionary).

https://leetcode.com/problems/word-ladder/
