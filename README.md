# Tech Interview

## Data Structures
For each of the following structures, you should understand how to implement and use them.
You should also know their time complexity for common operations (add, remove, access).

* [Dynamic array (aka Vector, Array List)](http://en.wikipedia.org/wiki/Dynamic_array)
* [Linked list](http://en.wikipedia.org/wiki/Singly_linked_list)
* [Hash table](http://en.wikipedia.org/wiki/Hash_table)
* [Heap](http://en.wikipedia.org/wiki/Heap_(data_structure)) (just know about min- and max-heap)

### Trees
* [Binary tree](http://en.wikipedia.org/wiki/Binary_tree)
* [Trie (aka Prefix tree)](http://en.wikipedia.org/wiki/Trie). A common application is for autocomplete or predictive text dictionary (think T9).
* [Binary search tree](https://en.wikipedia.org/wiki/Binary_search_tree)
  - **Self-balancing binary search trees:**  [AVL tree](https://en.wikipedia.org/wiki/AVL_tree) / [Red-black tree](http://en.wikipedia.org/wiki/Red%E2%80%93black_tree).
  You typically just need to know about them and their usage rather than know how to implement them.

> **NOTE:**
> Balanced Binary Search Trees are even better than heaps because in addition to `insert`, `delete`, and `min|max` —which is the contract of
> the [Priority Queue](./abstract-data-types/priority-queue.md) [absract data type](./abstract-data-types/)—, they provide `findSuccessor`
> and `findPredecessor` in O (log n) time.
> The main reason you'd prefer eaps is because the latter are in place: they don't use any extra space.

## [Abstract Data Types](./abstract-data-types/)
* [Queue](http://en.wikipedia.org/wiki/Queue_(abstract_data_type))
* [Stack](http://en.wikipedia.org/wiki/Stack_(abstract_data_type))
* [Priority queue](https://en.wikipedia.org/wiki/Priority_queue)

## [Algorithms](./algorithms/)
* [Binary search](./algorithms/binary-search.md) — find the position of an input element within a sorted array.
* [Graph/tree Traversal: Depth First Search (DFS)](./algorithms/graph-dfs.md)
* [Graph/tree Traversal: Breadth First Search (BFS)](./algorithms/graph-bfs.md) — guarantees shortest path.
* [Quicksort](http://en.wikipedia.org/wiki/Quicksort) vs. [Merge sort](http://en.wikipedia.org/wiki/Merge_sort)
* [Random permutation](http://en.wikipedia.org/wiki/Random_permutation)

## Object-Oriented Programming (OOP)
The three pillars of object-oriented programming are: encapsulation, inheritance, and polymorphism.
You should understand, be able to talk about, and apply the following object-oriented principles.
* [Encapsulation](http://en.wikipedia.org/wiki/Encapsulation_(object-oriented_programming))
* [Inheritance](http://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))
* [Polymorphism](http://en.wikipedia.org/wiki/Polymorphism_(computer_science)) (since we're talking about OOP, I’m referring to *inclusion polymorphism*)
* [Composition](http://en.wikipedia.org/wiki/Object_composition) (and why [one might prefer composition over inheritance](http://en.wikipedia.org/wiki/Composition_over_inheritance))

### Design Patterns
These are not sorted in any particular order other than alphabetical.

### Creational Patterns
* [Factory Pattern](http://sourcemaking.com/design_patterns/factory_method)

### Behavioral Patterns
* [Chain of Responsibility](http://sourcemaking.com/design_patterns/chain_of_responsibility)
* [Observer Pattern](http://sourcemaking.com/design_patterns/observer)
* [Strategy Pattern](http://sourcemaking.com/design_patterns/strategy)

### Structural Patterns
* [Adapter Pattern](http://sourcemaking.com/design_patterns/adapter)
* [Decorator Pattern](http://sourcemaking.com/design_patterns/decorator)

### Architectural Patterns
* [Model-View-Controller (MVC)](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) –
  [Model-View-Presenter (MVP)](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter) –
  [Model-View-ViewModel (MVVM)](http://en.wikipedia.org/wiki/Model_View_ViewModel)
* [Pub/Sub](http://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern)

# [Dynamic Programming](./dynamic-programming/)
TBD: currying, memoization
