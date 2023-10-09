# Algorithms › Graph Traversal › Depth-First Search
Depth-first search (DFS) is often used to explore the whole graph, not just the part reachable from a given vertex
— which would typically call for [breadth-first search](./graph-bfs.md).
“Recursively” explore the graph, backtracking as necessary while being careful not to repeat vertices

> NOTE: it might not use **the** stack to do recursive function calls, and instead might just use **a** stack.

## Running Time
`O (V + E)` just like BFS. 

## Applications
* Maze solving
* Edge classification (tree, forward, backward, cross-edge)
* Cycle detection (particularly for a directed graph, so that would be directed cycles) which is done —in linear time— by finding a back edge.
* Topological sort (e.g. job scheduling), “sorting vertices in a (acyclic) graph”.
  * Run DFS and output the reverse of the “finishing times” of vertices. 


## Sample Implementation
```typescript
interface AdjacencyLists {[index: string]: string[]}

/**
 * Performs a depth-first search (DFS) visit of every node reachable from a specific startNode.
 * Running time: O(V + E)
 */
function dfsVisit(graph: AdjacencyLists, startNode: string, parent: Map<string, string> = new Map()) {
  // The parent variable is essentially used to mark a node/vertex as visited.
  // But it can also be used to walk a path back.
  if (!parent.has(startNode)) { parent.set(startNode, '') };
  var dfsVisitImpl = function(node: string) {
    console.log(`Visiting ${node}.`);
    for (let adjacent of graph[node]) {
      if (!parent.has(adjacent)) {
        parent.set(adjacent, node);
        dfsVisitImpl(adjacent);
      }
    }
  }

  dfsVisitImpl(startNode);
}

/**
 * Performs a depth-first search (DFS) visit of *every* node.
 * Running time: O(V + E)
 */
function dfsVisit(graph: AdjacencyLists) {
  const parent = new Map<string, string>();
  for (const node of Object.keys(graph)) {
    if (!parent.has(node)) {
      parent.set(node, '');
      dfsVisit(graph, node, parent);
    }
  }
}
```


## Job Scheduling
Given a directed acyclic graph (DAG), order vertices so that all edges point from lower order to higher order.

![DAG-Jobs](https://github.com/osuritz/techinterview/assets/928328/a9a331f2-2cc2-4e64-9966-6d997f8edebc)

### Solution: Topological Sort
Run DFS and output the reverse of the “finishing times” of vertices. 
