# CSCI 570 - Homework 11

- **Name:** Boyang Xiao
- **Due Date:** Nov. 23<sup>rd</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>

---

### Problem #1

- Prove NP:
  - Efficient certificate: THe solution should be a spanning tree of the graph, which contains polynomial size of nodes
  - Efficient certifier: To certificste the solution, we have to first go over all the nodes to determine if it is a spanning tree. And we should go over all the nodes to count their degrees to see if they are all $\leq k$. And this is of polynomial complexity.

- Choose a known np-complete problem: **Hamiltonian path problem**

- Prove that: Hamiltonian Cycle problem $\leq _p$ k bounded spanning tree problem

First of all, Hamiltonian cycle problem can be treated as a spanning tree problem with constraint $k = 2$. That is, every Hamiltonian path is a spanning tree where every node is of degree 2.

If we can find a hamiltonian path in the graph, we connect $k-2$ nodes to every node in the original graph and every spanning tree should've contained k-2 edges. Then we could definitely find a spanning tree of degree k if we can find a spanning tree of degree 2. Therefore: Hamiltonian Cycle problem $\leq _p$ k bounded spanning tree problem.

Therefore: The stated k bounded spanning tree problem is NP-complete.

---

### Problem #2

- Prove NP:
  - Efficient certificate: The solution should be a cycle (a specific order of nodes) which is of polynomial size.
  - Efficient certifier: To certificate the solution, we have to:
    - Go over the cycle to count the total weights and see if it equals to 0
    - Find if there is an edge between the first node and the last node

- Choose a know NP-complete problem: **Subset sum problem**

- Prove that: Subset sum problem $\leq _p$ 0-weighted-cycle problem:

In the subset sum problem, we are given a set of numbers and we have to determine if there exists a subset of the numbers that adds up to 0. 

If we can find such an subset, we can contruct a graph based on this subset. For each number $w_i$ in the subset, we assign two nodes to this number: $u_i$ and $v_i$. There is an edge connecting $u_i$ and $v_i$, whose weight is $w_i$. For $u_i$, there is only one outgoing edge connecting $v_i$, and for $v_i$, it connects to the next $u_j$ with a 0-weighted edge. Also, we should connect the first number and the last number with a 0-weighted edge like this to form a closed cycle. In this way, if we can find a 0-sum-subset out of the subset sum problem, we can find a zero-weight-cycle in this way. Therefore, Subset sum problem $\leq _p$ 0-weighted-cycle problem. $Q.E.D$

Therefore, the 0-weighted-cycle problem is NP-complete.

---

### Problem #3

- Prove NP:
  - Efficient certificate: K clubs
  - Efficient certification: To certificate the solution, we have to go over all the K clubs' lists of members and check if all the people are counted at least once.

- Choose a known NP-complete problem: **Set cover problem**
- Prove that: Set cover problem $\leq _p$ Redundant club problem

In the set cover problem, we have to find a minimum number $K'$ subsets of nodes to cover all the nodes. We can change the input of the set cover problem to the input of the redundant club problem. That is: each node represents a member and each subset is a club. Say the original number of clubs is $C$, then $K = C - K'$ where $K$ is the constraint in Redundant club problem and $K'$ is the constrain in the Redundant club problem. This can be done in polynomian time.

And if we can find a set cover of K' subsets which cover all the nodes at least once, we can say that these K' clubs can cover all the members at least once, too. And $C-K'$ should be the clubs we want to disband. THerefore, we can reduce the set cover problem to the redundant club problem.

Therefore, the redundant club problem is in NP-complete. $Q.E.D$

---

### Problem #4

- Prove NP:
  - Efficient certificate: The solution should be a subset of vertices of $|V|/2$ size.
  - Efficient certifier: To verifiy the solution, we have to first count the number of vertices in the subset and check if it equals to $|V|/2$. And we should also go over all the edges to check that not both of its ends are in this subset.

- Choose a known NP-complete problem: **Independant set problem**
- Prove that: IS problem $\leq _p$ HALF IS problem:

Let's say: In a IS problem, we have n nodes and the size of the found independant set is k. And we assume here that n is a even number. We can construct a new graph G' out of the graph in IS problem to satisfy the requirements of HALF IS problem.

- If $k > n/2$:

We add $2k - n$ nodes which are connected to at least one node in the known independant set of vertices, so that all these $2k-n$ nodes cannot be counted into the independant set. Now the whole number of vertices is $2k$ and there are $|V|/2 = k$ vertices are in the independant set.

- If $k = n/2$:

The solution of IS problem is exactly the solution of HALF IS problem. No modifications needed.

- If $k < n/2$:

We add $n -2k$ nodes which are mutually independant and also independant from the vertices in the known independant set, so that all these vertices can be counted into the independant set. And now the whole number of vertices is $2n - 2k$ and the independant set size is $k + n-2k = n-k$, which is exactly $|V|/2$.

In this way, we can reduce an IS problem to an HALF IS problem in polynomial time.

THerefore, the HALF IS problem is in NP-complete.

---

### Problem #5

- Prove NP:
  - Efficient certificate: The solution of this problem should be a series of courses, which is of polynomial size.
  - Efficient certifier: To verify the results, we should go over all 24 hours in a day and check if there is no two courses going on at the same hour.

- Choose a known NP complete problem: (Clearly the problem statement has already chosen for us (LOL) ) **Independant set problem**

- Prove that: IS problem $\leq _p$ Course choosing problem.

We can treat every time interval as a edge in the Independant Set, say, $[e_1, e_2, ... e_n]$ and $e_i$ represents the time interval $[i, i+1]$. The two ends of each edge should be two end points of this interval (two specific hours).  And according to the nature of an independant set, ther should be no overlapping of each two time intervals. The chosen courses can be generated from all these intervals in the independant set problem. 

THerefore, the Course choosing problem is of NP-complete.




