# CSCI 570 - Week 09

## Network Flow

**Lecture date:** Oct. 19<sup>th</sup>, 2022

---

## Network flow problems

### Examples

- How much data we can send from one node in the network to another node
- How much traffic can a freeway system sustain for travel between two cities

- #### Supply chain problem

Network:

Supply -> cutting locations -> Sewing locations -> Finishing locations -> Distribution centers -> Customers

### Definitions

- #### A flow network

A directed graph $G= (V,E)$ with flowing features:

- Each edge has a non-negative capacity $c_e$
- Has a single source node $s \in V$
- Has a single sink node (only going in) $t \in V$

- #### Assumptions:

- no edges enter s or leave t
- at least one edge is connected to each node
- all capacities are integers

- #### Notations

- $f(e)$ flow through edge $e$. and $f(e)$ has following properties:
  - $0 \leq f(e) \leq c_e$
  - $\sum _{e \,into\, v}f(e) = \sum _{e \,out\,of\, v}f(e)$

- #### Steady state flow

The flow **does not change** over time.

For a steady state flow , the value of flow $v(f)$ is defined as :

$$v(f) = \sum _{e\,out \,of s} f(e)$$

---

### Max flow problem

Given a flow network G, find an $s-t$ flow with max value

<!-- #### Greedy approach -- Not applicable

- ##### Try #1

Use the highest capacity edges first -> **This does not get the optimal solution**

- ##### Try #2

Use lowest capacity edges first -> **Not either** -->

#### Residual Graph

A residual graph $G_f$ of $G$ is:

- $G_f$ has the same set of nodes as $G$
- for each edge e with $f(e)<c_e$, we incldue e in  $G_f$ with capacity $c_e - f(e)$
- for each edge e with $f(e) > 0$, we include edge e' (opposite direction to e) in $G_f$ with $f(e)$ units of capacity -> **Backwoard edges that we can undo**

To create $G_f$:

- if $f(e) = 0$ : forward edge with capacity $c_e$
- if $0 < f(e) < c_e$ : 
  - one forward edge with capacity $c_e - f(e)$
  - one backward edge with capacity $f(e)$
- if $f(e) = c_e$ : Backward edge with capacity c_e

#### Resudual Graph approach ideas

- If P is a simple path from s to t in $G_f$, then bottleneck (P) is the minimum residual capacity of andy edge on P (both forward and backward)

**Overrall strategy to find the max flow**

- Find a path from s to t
- Find the vottleneck value for this path
- Push flow through this path value equal to bottleneck value
- Repeat

---

#### Ford-Fulkerson algorithm for max Flow

Full algorithm:

```python
maxFlow(G, s, t, c)
  Initialize f(e) = 0 for all e in G
  while there is an s-t path in G_f
    Let P be a simple path from s to t
    f' = augment(f, c, p)
    f = f'
    Update G_f
  end while
```

##### Proof


---

#### Min cut


---

## Discussion session

### Problem 1

We generate the residual graph from the original max flow