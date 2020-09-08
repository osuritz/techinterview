# Algorithms > Graph Traversal: Breadth-First Search
Unlike [Depth-First Search](./graph-dfs.md) which uses a stack for traversal, the Breadth-First-Search algorithm uses a *queue* to store
intermediate results as it traverses the graph.
It has the **extremely useful property that**, if all of the edges in a graph are either unweighted or all the same weight,
then the first time a node is visited **is the shortest path from the source node to that node**.

Note: when applying BFS on a tree, there is no need to mark "vertices" (aka nodes) as visited because there are no cycles in a tree.

## When to Use
* When looking for the shortest path in a graph.
* Beginning state & ending state and how fast to get there (e.g. solving a Rubik's Cube)
  - How deep?
  - How many levels?
  - How many transformations?
  
## Applications
* Web crawling
* Social networking (e.g. friends nearest to you, friends of friends)
* Network broadcast (packet is exploring the graph)
* Garbage collection
* Model checking: draw a graph of all the possible states a chip/circuit or program could reach or have, start from an initial
state so you visit all the vertices reachable from a particular place.
* Checking mathematical conjectures
* Solving puzzles & games


## Sample Implementation
```
//TODO
```

## Example Problems
### Invert/mirror a Binary Tree (Easy)
https://leetcode.com/problems/invert-binary-tree/

The canonical example of Breadth-First Search is to invert/mirror a binary tree

Input:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

Output:
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

#### Java
```java
public TreeNode invertTree(TreeNode root) {
    if (root == null) return null;
    Queue<TreeNode> queue = new LinkedList<TreeNode>();
    queue.add(root);
    while (!queue.isEmpty()) {
        TreeNode current = queue.poll();
        TreeNode temp = current.left;
        current.left = current.right;
        current.right = temp;
        if (current.left != null) queue.add(current.left);
        if (current.right != null) queue.add(current.right);
    }
    return root;
}
```

### Print a Binary Tree in level order (Easy)
Printing a binary tree in level order is a variant of BFS and uses two queues: one to store the current level items and a second queue to store
the children of the current level items.
Once the first queue is empty, we swap the current- and next-level queues and keep going.
https://leetcode.com/problems/binary-tree-level-order-traversal/

### Word Ladder (Medium)
A series of transformations from *beginWord* to *endWord* via a list of words (dictionary).

https://leetcode.com/problems/word-ladder/
