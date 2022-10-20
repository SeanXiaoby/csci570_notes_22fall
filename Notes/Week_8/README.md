# CSCI 570 - Week 08

## Dynamic programming *Part II*

**Lecture date:** Oct. 12<sup>th</sup>, 2022

---

## DNA sequence alignment problem

- Defi. Similarity is the minimum cost of an alignment between string X and Y

- Sub-problem:

Define $OPT(i,j)$

Recurrence formula:
$$\begin{align}
  OPT(m,n) = min(\alpha_{{x_m}{y_n}} + OPT(m-1, n-1) \\
             \delta+ OPT(m-1, n), \\
             \delta+ OPT(m, n-1)) 
\end{align}$$

Initialize $i == 0$ columns and $j == 0$ rows



---

## Matrix chain multiplication problem

### Problem statement

Multiple matrics multiplication. A1 A2 A3...Ai

For $A_i \cdot A_j$, it takes time $O(R_iC_iC_j)$

### DP solution

Define: $OPT(i,j)$ minimum costs multiplicating matrix i...j

$OPT(i,j) = min(OPT(i,k)+OPT(k+1, j) + R_iC_kC_j)$ for $i\leq k \leq j$



---

## Shortest path w/ dynamic programming

If there is no negative cycle in a graph G, then there is a shortest path from s to t that is simple, hence it has at most n-1 edges.

Define $OPT(i,v)$ to be the min cost of a shortest path from v to t using at most i edges.

**Objective:** find $OPT(n-1, S)$

Recurrence formula:

$$OPT(i,v) = min(OPT(i-1, w) + c_{v,w})$$

where $w\in adj(v)$


|Bellman-ford|Dijkastra|
|---|---|
|O(mn)|O(mlogn)|