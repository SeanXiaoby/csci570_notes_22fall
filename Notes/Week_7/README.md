# CSCI 570 - Week 07

## Dynamic programming *Part I*

**Lecture date:** Oct. 5<sup>th</sup>, 2022

---

## General approaches to optimize using Dynamic Programming

- Characterize the structure of an optimal solution
- Recursively define the value of an optimal solution
- Compute the value of an opt. solution in a bottom up fashion
- Construct an optimal solution from computed infomation

### Example problem: *n requests to 1 resource*

- Brute force problem:

We find every combination subset out from the whole set and test if it meets the requirements

- DP soulution
  
```
Compute opt(j)
if j == 0
  return o
else
  return max(wj + opt(p(j)), opt(j-1))
endif
```

- Runtime complexity:
  - Initial sorting: $O(nlogn)$
  - Build the $p()$ array: $O(nlogn)$
  - M-compute-opt: $O(n)$
  - **Overall**: $O(nlogn)$


### DP component: Memorization

Store the output of specific inputs globally that can be accessed by the recursive function and use this pre-computed value in place of all future recurive calls. 


---

### Recursion vs Iteration

Compiler usually prefers iterations because recursion requires calling functions, which can be expensive

---

## Video game problem

### Problem statement:

Starting from stage 0 and end in stage n

Initial energy $E_0$, the $i^{th}$ stage takes energy units: $e_i$

Jumping choices:
- Walk into next stage takes 50 energy units
- Jumping over one stage takes 150 energy units
- Jumping over two stages takes 350 energy units

Goal: Going home with most energy

### DP solution

- **Recursive component:** $OPT(i)$: optimal level of energy when we reach stage $i$

$$\begin{align}
  OPT(i) = max(OPT(i-1)-50-e_i,\\
   OPT(i-2)-150-e_i,\\
    OPT(i-3)-350-e_i)
\end{align}$$

Also, remember some **corner cases** initializations:

$OPT(0) = E_0$

$OPT(1) = E_0 - 50 -e_1$

$OPT(2) = max(OPT(1)- 50- e_2, E_0 - 150 -e_2)$


- **Memorization component:** 

- **Runtime complexity analysis**:  $O(n)$

---

## Coin Problem

### Problem statement

To pay n schillings, use minimized number of coins:

|1|5|10|20|25|
|---|---|---|---|---|

### DP solution

- $OPT(i)$: Min num of coins to pay i schillings

$$\begin{align}
  OPT(i) = min(OPT(i-1)+1, \\
   OPT(i-5)+1, \\ 
   OPT(i-10)+1, \\ 
   OPT(i-20)+1, \\ 
   OPT(i-25)+1)
\end{align}$$ 

Initializations:

$OPT(0) = 0$
$OPT(1) = 1$
...
$OPT(24) = min(...)$

---

## 0-1 Knapsack problem / Subset sum problem

### Problem statement:

On slides

### DP solution:

- $OPT(i)$: value of optimal solutions for requests from 1 to i

<!-- If $n\notin O(n)$, $OPT(n) = OPT(n-1)$
If $n\in O(n)$, $OPT(n) = OPT(n-1) + w_n$ -->

SEE slides and textbook!!


### Psuedo polynomial runtime complexity!


---

## Discussion session

### Problem 1 

Two variables same as the last problem in the lecture


### Problem 2

$$OPT(i) = \begin{cases}
  OPT(i-1)\\
  min( OPT(i-1) + 3, OPT(i-7) +10)
\end{cases} $$

### Problem 3

- #### Figure (a)

$OPT(i,j) = OPT(i-1,j) + OPT(i,j-1)$

Runtime: $O(nm)$

- #### Figure (b)

Corner cases initialization (There are only two dead end intersections):

$OPT(3,2) = 0$ (dead end)
$OPT(2,2) = OPT(1,2)$ (Only one way to go))

for other normal cases, same as figure (a):

$OPT(i,j) = OPT(i-1,j) + OPT(i,j-1)$

### Backup problem: Skiing problem

$OPT(i,j)$ : length of the longest downhill path starting from $(i,j)$

$OPT(i,j) = max( OPT(i',j') + 1)$ where $OPT(i',j')$ are all the neighbors that are lower than $OPT(i,j)$

Initializations:

Set all the local Minimum points to be 0

Sort all the points in the grid by elevations, and fill in 2-d array $OPT(i,j)$ based on increasing order

**Sorting step can be changed to finding topological sotring, which has a linear complexity, because this is a 非循环 graph**