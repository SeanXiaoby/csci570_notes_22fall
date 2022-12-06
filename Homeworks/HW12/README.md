# CSCI 570 - Homework 12

- **Name:** Boyang Xiao
- **Due Date:** Dec. 1<sup>st</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>


---

## Problem 1

???

Didn't figure this one out. I'm gonna check the solutions after submission.

---

## Problem 2

#### LP problem:

$\min \sum c(u,v) * x(u,v) $ for $u, v \in V$

$x(u,v) = 0$ iff u and v are at the same side of the cut

$x(u,v) = 1$ iff u and v are at the different side of the cut

#### Explanations:

u and v are vertices in the graph and $c(u,v)$ is the cost of these specific edges. If the edge is crossing the cut, then we give it a weight $x(u,v) = 1$, otherwise, the weight $x(u,v) = 0$, meaning that this edge's cost is not in our considerations. And the final goal is to minimize the whole cost of all edges crossing the cut.

---

## Problem 3


$\min \sum ^{16} _i (D_i - S_i)$

$D_i \geq S_i$ for $0 \leq i \leq 16$

$S_i \geq 0$ for $0 \leq i \leq 16$

$\sum ^{16} _i S_i = 720$

---

## Problem 4

(a) My variables:

$r_i$ standing for the power/cost/radius of the $i_{th}$ station for $i \in \lbrace 1,2,3...,n \rbrace$

(b) Objective function

$\min \sum ^n _{i = 1} r_i$

(c) Constraints:

$r_i + r_j \geq \sqrt{(x_i - x_j)^2 + (y_i - y_j)^2 + (z_i - z_j)^2}$ 

(The sum of radiuses of each two stations is greater than the Euclidean distance of them)

