# CSCI 570 - Week 12

## Computational Complexity

**Lecture date:** Nov. 9<sup>th</sup>, 2022

---

## Computational tractability

**Plan:**

Explore the space of computationally hard problems to arrive at a mathmetical characterization of a large class of them

**Technique**

Compare relative difficulty

**Loose definition**

X is as least as hard as Y  **-->** If we could solve X, we could solve Y

### Polynomial reducible definition

$Y\leq _p X$ (Y is polynomial time reducible to X)

if Y can be solved using polynomial number of standard computational steps plus a polynomial number of calls to a blackbox that solves X

#### Theoreum

- #1 Suppose $Y\leq _p X$, if X can be solved by polynomial time, Y can be solve by polynomial time
- #2 Suppose $Y\leq _p X$, if Y cannot be solved by polynomial time, X cannot be solve by polynomial time

### Indepandent Set

**Def.**

In a graph $G=(V,E)$, we say taht a set of nodes $S\subseteq V$ is "indepandent" if no two nodes in S are joined by an edge

#### Indepandent set problem

- Find the largest independant set in a graph $G$ -- **Optimization version**

- Given a graph $G$ and a number k, does G contain a indepandent set of size at least k  -- **Decisional version**

### Vertex cover 

- Given a graph $G = (V,E)$, we say that a set of nodes $S\subseteq V$ is a vertex cover if every edge in E has at least one end in S

#### Vertex cover problem

- Finding the smallest vertex cover
- Given a graph G and a number k, does G contain a vertext cover of size at most k

**FACT:** In graph G, $S$ is a vertex cover $\leftrightarrow$ its complement $V-S$ is a vertex cover

#### Claims

- Indepandent set $\leq$ vertex cover
- Vertex cover $\leq$ indep. set


### Set cover problem



---

## Satisfiability Problem (SAT)

- Clause: A disjunction of terms $t_1, t_2...t_l$ where $t_l \in [x_1, x_2...x_n, \bar x_1, \bar x_2... \bar x_n]$
- 

General form of SAT:

- Gvien a set of clauses $c_1, c_2,... c_k$ over a set of variables $X={x_1, x_2,...x_n}$, does there exist a satafying truth assignment?

---
## NP problems


### Efficient certification

To show a problem has efficient certification:

- Polynomial length certificate

a polynomial length solution

- Polynomial time certificate

an polynomial runtime algorithm that can check the certificate is correct

### Class NP

A set of all decision problems for which there exists an efficient certificate

(Non-deterministic polynomial)

Polynomial time problem $\subset$ NP problem

### NP-complete

If problem $x \in NP$ set and for all problems Y, $Y \leq _p X$, then X is the hardest problem in this NP class and the set of these kind of problems are called NP-complete

- NP trasitivity

If $X \leq _p Y$ and $Y \leq _p Z$, then $X \leq _p Z$

### Prove NP complete

- Prove the problem X is a NP problem
- Choose a problem Y that is known to be NP complete
- Prove $Y \leq _p X$

### NP hard problem

The class of problems that are at least as hard as NP-complete problems