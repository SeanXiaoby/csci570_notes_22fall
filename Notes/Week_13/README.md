# CSCI 570 - Week 13

## Approximation algorithms

**Lecture date:** Nov. 16<sup>th</sup>, 2022

---

## TSP problem and Hamiltonian Cycle

### TSP problem statement

- Given n cities and distances between every pair of cities (fully connected graph)
- Order the cities the salesman travels with to minimize the trip distance

#### Decision version of TSP problem

Given n cities and a bound D, does there exsit an order of city of length /cost at D?

#### TSP problem is an NP complete problem

To prove that, we can reduce a know NP-complete problem to TSP problem: **Hamiltonian Cycle**

### Hamiltonian cycle problem

- Hamiltonian cycle: a cycle in graph which visits each vertex only once
- Problem statement:

Given a undirected graph G, is there a Hamiltonian cycle existing in the graph

#### Show that Hamiltonian cycle problem is an NP-complete problem

1. Show that HC problem is an NP problem:

Certificate: an order of all the vertex in the graph
Certifier: 

- Every node appears in the cycle
- Nodes only appear once
- Every pair of adjcent nodes have an edge between them
- THere is an edge between the head node and the tail node

2. Choose an NP-complete problem: Vertex cover
3. Show: Vertext cover $\leq _p$ Hamiltonian cycle