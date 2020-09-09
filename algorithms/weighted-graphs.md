# Weighted Graphs
In weighted graphs (graphs where the **edges** between vertices have weights), [breadth-first search (BFS)](./graph-bfs.md)
and [depth-first search (DFS)](./graph-dfs.md) do not work for computing shortest paths.

For weighted graphs, the two options for single-source shortest paths are: 
* [**Dijkstra**](./graph-dijkstra.md) (preferred because of its running time) for graph with non-negative weights.
* [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) for graphs with negative weights.
