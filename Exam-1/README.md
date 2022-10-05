# CSCI 570 - Exam 1 - Notes

### Topics:

- Statble matching
- Big O notations
- BFS DFS
- MST and shortest path
- Heap and amortized costs
- Greedy Algorithm
- Divide and conquer

---

## Statble matching

- ### Definitions

**Perfect matching**: one to one
**Unstatblity**: m - w and m' - w', but w -> m' and w' -> m

### Gale-Shapley algorithm

- Pick man in a loop and match him to the first woman on his preference list
- If the woman has already matched to another man, compare the current man with this matched man.
- If current man is ranked higher than the matched man, match the current man to the woman, and match the other man to his next preference.
- Iterate all the man like this.

#### Runtime complexity: $O(n^2)$

---

## Big O notation

- Ignores constants
- Usually we cares about the tight bound, but if a runtime has a upper bound of $O(n)$, it can only have a upper bound of $O(n^2)$ or $O(2^n)$

#### Runtime complexity math rules

If $f_1 = O(g_1)$ and $f_2 = O(g_2)$, then $f_1 \times f_2 = O(g_1 \times g_2)$

If $f_1 = O(g_1)$ and $f_2 = O(g_2)$, then $O(f_1 + f_2) = O(max(g_1, g_2))$ or $ O(g_1+g_2)$

If $f_1 = O(g_1)$ and $r$ is a constant, then $f_1 \times r = O(g_1)$

---

## BFS and DFS

### Functions of Search algorithms

- Looking at each node in a graph
- Finding things in graphs at a specific node
- Making a path
- Determine if a graph is connected

### BFS

- BFS can find a path between two nodes
- BFS can find the **shortest** path between two nodes if edges are **unweighted**
- BFS is implemented with a queue (FIFO)
- Runtime complexity: $O(|V|+|E|)$

#### BFS tree

- The nodes on the same layer of a BFS tree have the same distance from the root node
- There is a path from s to t only if t appears in some layer in a BFS tree

### DFS

- DFS can find a path between two nodes
- DFS is implmented with a stack (LIFO)
- Runtime complexity: $O(|V|+|E|)$


### DFS vs BFS

|DFS|BFS|
|---|---|
|Don't care about path length| Care about path length / shortest path|
|Easy to backtrack| Cannot backtrack|
|EXplore deepest first|Explore locally first|
|Both can find path|
|Both can find connected nodes number|
|Runtime same|

### Bipartite problem

- Run DFS/BFS from a random node, color each node with another color different from its parent
- If we come to an already-colored child that has the same color as its parent, then this is not a bipartite graph.

---

## Graph and Minimum spanning tree (MST)

### Definitions in a graph

- Strongly connected: Every vertex can be reached from every other node
- Weakly connected: A directed graph is weakly connected if it is strongly connected when the directions are removed
- Unilaterally connected: A directed graph is unilaterally connected if there exists at least one path from s to t or from t to s, for any pair of nodes (s,t) in the graph

### Dijkastra

- Initialize a visited node array V = {s}
- Loop on nodes that are not in V:
  - Pick the node with minimum distance from the source code
  - Push this current node into V
  - Update distances of other nodes with this current node's distance
- If graph is not connected, start over from the other non-connected nodes

**Runtime complexity:** 
- $O(mlogn)$ - With binary heap / binomial heap
- $O(m+nlogn)$ - With Fibonacci heap

### Finding MST algorithms

- ##### Sol1: Kruskal's algorthm
    - Sort all edges in increasing orders
    - Add edges into set T in this order as long as this edge **does not make a cycle** with the other edges in set T
    - If does, discard the edge and move on


- ##### Sol2: Modified Dijkastra (Prim's)
  - Initialize selected vertex array V' and selected edge array E', push a random source node s into V'
  - Every time pick a minimum edge that one end is in V' and one end is not in V'
  - Stop when all nodes are in V'

- ##### Sol3: Reverse Delete algorithm
    - Delete the largest edge from the graph one by one
    - Make sure it's a connected graph if we delete the edge
    - If not, move to the next edge

#### Runtime complexity 

|Kruskal|Prim |Reverse delete|
|---|---|---|---|
|$O(mlogn)$|$O(mlogm)$|$O(m^2)$|

---

## Heap and amortized costs

### Three types of heaps

|Ops|Binary heap|Binomial tree|Fibonacci tree|
|---|---|---|---|
|Find-min| $O(1)$| $O(logn)$| $O(1)$|
|Insert| $O(logn)$| $O(logn)$| $O(1)$|
|Extract min| $O(logn)$| $O(logn)$| $O(logn)$|
|Delete| $O(logn)$| $O(logn)$| $O(logn)$|
|Decrease key| $O(logn)$| $O(logn)$| $O(1)$|
|Merge| $O(n)$| $O(logn)$| $O(1)$|
|Construct|$O(n)$| $O(n)$| $O(n)$| 

### Binomial Heap

#### Properties of binomial tress:

- In a binomial tree of degree k
  - The root has k children
  - The tree has #2^k# elsements
  - the tree has height k
  - the children of rout are binomial trees of degree k-1, k-2 ... 0

**Binomial heap** is a collection of binomial trees, each one is a heap, and at most one tree of each degree

#### Binomial heap properties

If given a binomial heap of n items:

- Largest tree has a degree of $log{_2}{n}$
- There are $\leq log{_2}{n}+1 $ binomial trees

### Amortized costs

#### Aggregate method

- We take a sequence of n operations, and it takes worst-case time $T(n)$ in total
- So in the worst case, the amortized cost per operation will be $T(n)/n$

---

### Greedy

---

### Divide & Conquer

#### Master theorem

**Case 1:** If $f(n) = O(n^{log{_b}{a} - \epsilon})$ for some $\epsilon>0$, then $T(n) = \Theta(n^{log{_b}{a}})$

**Case 2:** If $f(n) = \Theta(n^{log{_b}{a} - \epsilon}log^kn)$ for some $k\geq0$, then $T(n) = \Theta(n^{log{_b}{a}}log^{k+1}n)$

**Case 3:** 

- If $f(n) = \Omega(n^{log{_b}{a} + \epsilon})$ for some $\epsilon>0$
- And if $af(n/b) \leq cf(n)$ for some constant c<1
- Then $T(n) = \Theta(f(n))$