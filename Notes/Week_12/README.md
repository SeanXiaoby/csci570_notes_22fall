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

