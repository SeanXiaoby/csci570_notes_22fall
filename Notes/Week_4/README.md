# CSCI 570 - Week 04

**Lecture date:** Sep. 14<sup>th</sup>, 2022

---
## Amortized Cost analysis

- Amortized cost for operations of data structures


- ### Amortized cost analysis applied to 3 types of trees
|Ops|Binary heap|Binomial tree|Fibonacci tree|
|---|---|---|---|
|FInd-min| $O(1)$| $O(logn)$| $O(1)$|
|Insert| $O(logn)$| $O(logn)$| $O(1)$|
|Extract min| $O(logn)$| $O(logn)$| $O(logn)$|
|Delete| $O(logn)$| $O(logn)$| $O(logn)$|
|Decrease key| $O(logn)$| $O(logn)$| $O(1)$|
|⚠️Merge| $O(n)$| $O(logn)$| $O(1)$|
|Construct|$O(n)$| $O(n)$| $O(n)$| 

---

## Shortest path w/ weights

### Problem Statement

Given graph G(V,E), where weights of each edge $\omega(u,v) > 0$ for each edge between u and v. Find a shortest path starting from S to every other node.

### Minimum network building problem:
Find a minimum cost network that covers all the nodes in a Graph.

- #### Spanning tree def.
  - Any tree that covers all the nodes in a graph is called a **spanning tree**.
  - A spanning tree with minimum total edge costs is called a **minimum spanning tree(MST)**

### Algorithm

- ##### Sol1: Kruskal's algorthm
    - Sort all edges in increasing orders
    - Add edges into set T in this order as long as this edge **does not make a cycle** with the other edges in set T
    - If does, discard the edge and move on


- ##### Sol2: Modified Dijkastra (Prim's)
  - 

- ##### Sol3: Reverse Delete algorithm
    - Delete the largest edge from the graph one by one
    - Make sure it's a connected graph if we delete the edge
    - If not, move to the next edge

### Proof of fact

### Implementations

### Runtime complexity analysis

---

## Discussion Session

### Problem 1

- Perform dijakstra twice: From home to work and from work to home
- Change undirected graph to a directed one: 
  - From home to work: low to high
  - From work to home: **also low to high**
- Find the intersection between these two shortest path
- If no intersection, no this kind of shortest path

### Problem 2

- We can run Dijakstra only once
- We add a entry point, and the distances between this virtual entry point to all the real entry points are all 0
- Start dijkstra from this virtual point

### Problem 3

- Watch recordings
- **Difference between amortized and averaged**

### Problem 4

