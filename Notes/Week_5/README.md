# CSCI 570 - Week 05

**Lecture date:** Sep. 21<sup>th</sup>, 2022

---

## Divide and conqueror

- **Divide** large problems into smaller sub-problems
- **Conqueror**: Resolve the sub-problems **recursively**, or solve the them directly if not important.
- **Combine** the solutions

### Example: Merge Sort

Find out which steps are Divide, conqueror and merge

### Runtime complexity ananysis

|Divide|Conqueror|Merge|
|---|---|---|---|
|O(1)|a*T(n/b) on m sub-problems|O(n) on array size of n|

$T(n) = T(1)$ or $aT(n/b) + D(n) + C(n)$

**Refer to slides about the meanings of each term**

**Totol costs of Divide n conqueror**: $O(nlogn)$

### Master method

Three cases runtime complexity analysis

---

## Stock market Problem

- Divide the whole stock curve into two halfs
- Compare the first half and the second half:
  - Case 1: 
  - Case 2:
  - Case 3:
- Runtime complexity: $\theta(n)$ -- Linear time

---

## Dense matrix multiplications

- Brute force $\theta(n^3)$

### Break into four sub matrixes

- a: 8 (Sub problems number)
- b: 2 (Sub problem size)
- $f(n)$: $D(n) + C(n) = \theta(1) + \theta(n^2)$ (matrix addition) $ = \theta(n^2)$

**It belongs to case #1**:  $T(n) = \theta(n^3)$


---

## Find min & max in an *unsorted array*

- Brute force: $(n-1)+(n-1)=2n-2=O(n)$

- #### Devide and conqueror:
  - Devide into two parts
  - Find the min & max respectively
  - Do it recursively

##### Time saving happens at the last but one layer: 
- We have n leaves node, which stand for the single item in the array
- When we proceed to the next upper layer, we compare for **2 times** to merge two node
- But at the **last but one** layer, we only compare **once** for each merging, because one is the max and the other is the min
- THerefore, the runtime should be $2n-2 -n/2 = 3n/2 -2$

---

## Closest pair of points problem

- Brute force: $(n-1)+(n-2)+...+1 = \theta(n^2)$

- #### Divide and conqueror

Divide the whole plain into two parts:

- Case #1: Both points are in $P_1$
- Case #2: Both points are in $P_2$
- Case #3: One in $P_1$ and one in $P_2$

**Refer to the recordings**

- Overall costs: 
  - Driver: $\theta(nlogn)$
  - a = 2
  - b = 2
  - $f(n) = \theta(n)$
  - Overall: **Case#2** : $\theta(nlogn)$

---

## Discussions

### Problem 1 -- False

Conter-example on slides

### Problem 2
