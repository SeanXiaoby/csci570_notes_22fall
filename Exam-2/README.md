# CSCI 570 - Exam 2 - Notes

### Topics:

- Dynamic Prgramming
- 0-1 Knapsack problem
- Network Flow
- Circulation network problem

---

## Dynamic Prgramming

Pre questions we have to consider:

- Sub problem is?
- How many dimensions do we need for the problem?
- Reccursion relations for OPT
- Initialization values
- Iteration or Recurrsion?

<!-- ### Sub problem

**Define $OPT[i,j,...]$**

Let $OPT[i,j]$ be the number of xxx when we have $i$ of xxx and $j$ of xxx.

### Recur -->

---

## 0-1 knapsack

- Sub-problem: 
  
$OPT[i][j]$: The most values we can get if put item $[0,1,...i]$ into the knapsack with capacity of $j$

- Reccursion:

$OPT[i][j] = max(OPT[i-1][j], w[i]+ OPT[i-1][j-c[i]])$

- Initializations:
  - $OPT[i][0] = 0$
  - $OPT[0][j] = 0$ if $j<c[0]$ and $OPT[0][j] = w[0]$ if $j>=c[0]$
  
- Psuedo codes:

```python
for j = 1:c
    for i = 1:n
        OPT[i][j] = max(OPT[i-1][j], w[i]+ OPT[i-1][j-c[i]])
    end for
end for

return OPT[n][c]
```

- Time complexity: $O(cn)$

## 0-1 完全背包

$OPT[i][j] = max(OPT[i-1][j], w[i]+ OPT[i][j-c[i]])$

---

## Network flow

- Max flow min cut
- Ford fulkerson algo.
- Scaled Ford fulkerson algo.
- Runtime complexity

### Max flow min cut

- **cuts:** $C(S,T)$ is a partition of vertexes with Source node in one half and the sink node in the other
- **cut set:** $X_c$ is the set of edges that connect every node in one part and every node in another part
- **Capacity of a cut:** $c(S,T) = f^{out}(S) - f^{in}(S)$
- **Minimum cut:** Cuts that have minimized capacity

👉 Max value of a flow = minimum capacity of all cuts

- Every edge from u to v has a flow of its capacity

### Ford fulkerson algo.

- Residual graph
- Find path

### Scaled fulkerson Algo.

- Residual graph
- Initialized $\Delta$ = $2^n$ that not greater than the max capacity out of S
- Every loop for $\Delta$, pich path that has bottleneck no less that $\Delta$
- Loop while $\Delta \geq 1$

### Runtime complexity

|Algorithms| Complexity|Type|
|---|---|---|
|Ford-Fulkerson|$O(cE)$|Psuedo-polynomial
|Scaled-FF| $O(E^2lgc)$ | Weakly-polynomial|
|Edmonds-Karp| $O(VE^2)$ | strongly polynomial|
|Orlin+ KTR| $O(VE)$ | Strongly polynomial|

---

## Circulation network

- circulation network problem
- circulation with lower bounds

### Circulation network problem

- Is a directed graph
- Has capacity on edge
- Each node has demands:
  - if $d_v > 0$: sink node
  - if $d_v < 0$: source node
  - if $d_v = 0$: neither

Solutions:

- Identify all source nodes and all sink nodes
- Create one Super source node $S^*$ and one Super sink node $T^*$
- $S^*$ to {$S$} have capacity of {$d_v$} and {$T$} to $T^*$ have capacity of {$d_v$}
- Run max flow
- Observation of value of flow $v(f)$ and Total demand $D = \sum _{d_v >0} d_v$
  - If $v(f) < D$: No feasible circulation
  - If $v(f) > 0$: Not possible
  - If $v(f) = D$: Found the feasible circulation

### Circulation with lower bounds

- **Capacity condition: $l_e \leq f(e) \leq c_e$**
- Demand condition: Same

Solution:

- Step 1: Set for every edge that: $f_0(e) = l_e$, and for every node: $f_0^{in}(v) - f_0^{out}(v) = L_v$
- Step 2: Construct a  circulation network where:
  - For each edge: $c_e' = c_e - l_e$
  - For each node: $d_v' = d_v - L_v$
- Step 3: Find the feasible circulation $f_1$ in this network
- Step 4: Results:
  - If there is no feasible circulation: Then no
  - If there is, then the final circulation should be : $f_0 + f_1$