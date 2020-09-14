# Weighted Graphs
In weighted graphs (graphs where the **edges** between vertices have weights), [breadth-first search (BFS)](./graph-bfs.md)
and [depth-first search (DFS)](./graph-dfs.md) do not work for computing shortest paths.

For weighted graphs, the two options for single-source shortest paths are: 
* [**Dijkstra**](./graph-dijkstra.md) (preferred because of its running time) for graph with non-negative weights.
* [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) for graphs with negative weights.

|          | Single-source shortest paths in DAGs | Dijkstra   | Bellman-Ford  |
|----------|---------------------------------------|------------|---------------|
| Supports cycles.          |   | ✓ |  ✓ |
| Supports negative weights | ✓ | | ✓ |
| Runtime complexity.       | O(V+E)  |  O(n²) or O(E+V log V)* | O(V*E)
| Key supporting data structure |   | [Priority queue](../abstract-data-types/priority-queue.md)  |  — |

\* when using the right data structure such as a Fibonacci heap

## Single-Source Shortest Paths in DAG
We can compute shortest paths from a single source in Θ(V+E) time for a weighted directed acyclic graph (DAG).

Start with a topological sort of the DAG to impose a linear ordering of the vertices. (If the DAG conains a path from
vertex 𝑢 to 𝑣, then 𝑢 precedes 𝑣 in the topological sort). This is a barely modified [DFS](./graph-dfs.md).

The shortest path can be obtained by making just one pass over the vertices in the topologically sorted order.

### Pseudocode
```
dag-shortest-path(G, 𝑤, 𝑠)
1 topologically sort the vertices of G
2 INITIALIZE-SINGLE SOURCE(G, 𝑠)
3 for each vertex 𝑢, taken in topologically sorted order
4     for each vertex 𝑣 ∈ G.Adj[𝑢]
5         Relax(𝑢, 𝑣, 𝑤)
```


### Sample implementation
```
// TODO
```
