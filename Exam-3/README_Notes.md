# CSCI 570 - EXAM 3

### Review Session

### Topic:
- NP complete
- Approximization algorithm
- Linear programming

---

## Np complete problems

- Decision vs Optimizations
  - Decision problem : Yes/No
  - Optimization problem : Max/Min
- P/NP problems
  - P problem: Decision problems that is **solvable** in polynomial time
  - NP: Decision problems that is **verifiable** in polynomial time
- NP hard
- NP complete

- Relations

<img src="./src/P_np_np-complete_np-hard.svg.png" width = 70%>

## Prove NP complete

- Prove that problem $X\in NP$
  - Certificate and verifier
- Choose a known problem $Y$ in NP complete
- Prove $Y \leq _p X$
  - Construct an instance of X out of an instance of Y
  - Forward assumptions: Prove that x is satisfiable for X -> y is satisfiable for Y
  - Backwards assumptions: Prove that y is satisfiable for Y -> x is satisfiable for X



### Some theoreums

- Any NP problem can be reduced to NP-complete problem
- NP-complete problems can be reduced to each other
- Always check if it is in NP
- Optimization problems are not in NP
- All NP-complete problems are not proved sovlable in P-time and not prove unsolvable in P-time

### Known NPC problem instances

- 3-SAT

Given a set of clauses $C1, . . . , Ck$, each of length 3, over a set of variables $X = \lbrace x_1, . . . , x_n\rbrace $, does there exist a satisfying truth assignment?

- Independent set

Independent set: not two edge is connected by an edge

Problem statement: : Given a graph $G(V,E)$ and an integer k, is the graph contains an independent set of vertices of size $\geq k$

- Vertex cover

Vertext cover: For each edge in the graph, at least one of its vertex is in the set, then this set is called a vertex set

Problem statement: Given a graph $G(V,E)$ and an integer k, is the graph contains a vertex cover of size $\leq k$


- Set cover

Given a universe U of n elements, a collection of subsets of U say $S = {S_1, S_2…,S_m}$ where every subset $S_i$ has an associated cost. Find a minimum cost $c_i$ subcollection of S that covers all elements of U.

- Set packing

Given a universe union U and a group of subsets S, and an integer k. Is there a subset of S that each subset in it does not intersect and the size is $\geq k$

- Hamilton cycle / Hamilton path

Problems of determining whether a Hamiltonian path (a path in an undirected or directed graph that visits each vertex exactly once) or a Hamiltonian cycle exists in a given graph (whether directed or undirected)

- TSP

Given a set of distance on n cities and a bound D, is there a tour of length/cost $\leq D$

- 01 knapsack problem

Given n items with size $s_1, s_2,...s_n$ value $v_1, v_2, ... v_n$, capacity B and value V, is there a subset $s \subseteq [1,2,...,n]$ such that $\sum _{i\in S} s_i \leq B$ and $\sum _{i\in S} v_i \geq V$

- Subset sum problem

Given a set of non-negative integers, and a value sum, determine if there is a subset of the given set with sum equal to given sum. 

#### Tricks of reduction

- First, we think about the instance of the known problem, and we try to construct a similar instance of the unknown problem based on this known instance
- Then, we prove that, if we can solve the knwon

---

## Linear Programming

### Classification

- Linear Programming -- Continuous variables
- Integer Programming -- Discrete variables
- Mixed Integer Prgramming -- Both Cont. and Dis.
- Non-Linear Programming -- Non Linear Constraints or Objective function


### Representation

- LP variables
- Objective function
- Objective constraints

#### Tricks

- If the given objective function cannot be expressed, we can choose an auxilary variable and put the relations of the auxilary variable to the constaints
- For integer lp problem, use TF table to find the inequation of the different variables
- 
