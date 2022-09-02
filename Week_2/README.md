# CSCI-570

### Week 02 - Aug. 31<sup>st</sup> 2022

---

## Review: Asymptotic Notations

- When we talk about asymptotic notations, we care about situations when n is very large but not small
- When we analyze algorithms, we care about the worst case complexity more, which makes the big O notation more meaningful, while the big Θ results for each algorithms can vary a lot actually.
- ##### Big **O** notation ---> Upper bound
  
  - Some claims:
    - Any quadradic functions is O(n<sup>2</sup>) -----> Tight bound
    - Any linear function is O(n<sup>2</sup>) ----> **Upper bound** but not tight
- ##### Big **Ω** notation ---> Lower bound
  
  - Some claims:
    - Any quadradic function is Ω(n<sup>2</sup>)
    - Any linear function is Ω(n<sup>2</sup>) ----> False!!!!
    - Any cubic function is Ω(n<sup>2</sup>) -----> True! lower bound!!
- ##### Big **Θ** notation ---> tight bound
  
  - Any quadradic function is Θ(n<sup>2</sup>) ----> True!
  - Any linear function is Θ(n<sup>2</sup>) ----> False!!!!
  - Any cubic function is Θ(n<sup>2</sup>) -----> False!!!!
- ##### Examples:

| Algorithms     | Worst cases|	Best case|
| ----------- | ----------- |-------|
| Linear Search      | O(n), Ω(n),  Θ(n)  |O(1), Ω(1),  Θ(1)| 
| Binary Search   | O(logn), Ω(logn),  Θ(logn)  | O(1), Ω(1),  Θ(1)  |
|Insertion sort|	O(n2), Ω(n2), Θ(n2) |O(n), Ω(n),  Θ(n)|
|Merge sort|	O(nlogn), Ω(nlogn), Θ(nlogn) |O(nlogn), Ω(nlogn), Θ(nlogn) |
|...| | |𝝝

- ##### Performance Analysis
  
  - Alg' A: O(4<sup>n</sup> n<sup>3</sup> logn)
  - Alg' B: O(3<sup>n</sup> n<sup>8</sup> logn<sup>2</sup>)
  - Breaking into components:
    - Exponential component: **Growing faster**
    - Polynomial component: ⬆️
    - logarithmic component: **Growing slower**
  - We care about the **Growing-faster** components ONLY
- ##### Hybrid Solutions senarios
  
  - When the runtuime complexity of two algorithms have a break-point, we can choose the two algorithms hybridly.

---

## Review: BFS and DFS

- ### What are we searching for in a graph?
  
  - A path from A to B
  - All nodes that can be reached from a certain node.
- ### BFS
  
  - Can find the **shortest** distances
  - BFS tree structure
    
    - Nodes on the same level have same distance from the root
    - The path should be **unweighted!!**
  - Runtime complexity
    
    - num of nodes: n; num of edges: m
    - Find a node from a node: O(m+n)
- ### DFS
  
  - DFS tree
    - Non shortest distances
  - Also O(m+n)
- ### Examples
  
  - ##### Determine if a graph is bipartite:
    
    - Define. All nodes in a graph can be partitioned into two sub sets U & Y, where every edge in the graph is between one node from U and one node from Y.
    - Another defi. All the cicles in the graph have only **even** num of nodes.
    - Use BFS to iterate all nodes and label them as BLUE and RED depending on if they are in a odd level or a even level.
    - Go through all the edges in the graph and check they all have a RED end a BLUE end. If do, the graph is bipartite.
- ### Types of graphs
  
  - **Strongly connected:** A directed graph is strongly connected if there is a path from any node to any other node.
    
    - To detect strong connectivity, run BFS/DFS starting from any node
    - O(n<sup>2</sup> + nm)
- ### Transpose of a directed graph
  
  - Change the direction of every edge
  - A graph is strongly connected <----> A graph has a transpose
  - Steps:
    - detect if the graph is strongly connected
    - Change directions of edges

---

## Discussion sessions

- ##### If f(n) = O(g(n)), can we say
- ##### 
- ##### If we can have a path to go through all the nodes in a graph, there can be only one topological sorting order existing in this graph

---

## Greedy algorithms
