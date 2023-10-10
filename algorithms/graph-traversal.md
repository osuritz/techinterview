# Algorithms › Graph Traversal

## Single-Source Shortest Path (SSSP)

| Situation                            | Algorithm     | Time |
| ------------------------------------ | ------------- | --- |
| Unweighted / equal weight `(w = 1)`  | [breadth-first search (BFS)](./graph-bfs.md)  | O(𝑉 + 𝐸)  |
| Non-negative edge weights `(w ≥ 0)`  | [Dijkstra](./graph-dijkstra)  | O(𝑛²) or O(𝐸 + (𝑉 × log 𝑉))* |
| General                              | [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman–Ford_algorithm)  | O(𝑉 × 𝐸) |
| Acyclic graphs (DAGs)                | [Topological sort](./graph-dfs.md#solution-topological-sort) + 1 round of [B-F](https://en.wikipedia.org/wiki/Bellman–Ford_algorithm) | O(𝑉 + 𝐸) |

\* with a Fibonacci heap.
