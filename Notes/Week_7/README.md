# CSCI 570 - Week 07

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

$OPT(i) = max(OPT(i-1)-50-e_i, OPT(i-2)-150-e_i, OPT(i-3)-350-e_i)$

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