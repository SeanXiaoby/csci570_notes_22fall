# CSCI 570 - Week 03

**Lecture date:** Sep. 7<sup>th</sup>, 2022

---
## Greedy Algorithm

### Sequence of requests

Last lecture 👉 [here]()

### Fractional knapsack problems

- Problem: 
  - Knapsack has a capacity of n
  - Put items into knapsack so that can get a highest value
- Greedy solution:
  - Put items in order of value/weight descending
  - Put items into knapsack until reach weight capacity

### Scheduling to minimize lateness

Claims 1-5

### Coffin Scheduling


---

## Discussions

### Problem 1

**Idea:** 
- Starting from left or right endpoint, find the first house that has not been covered and build the base station in its right 4 miles.
- FInd the next house that is not covered and do it again until reach the last house

**Proof**

⚠️ By contradictions


### Problem 2

#### Idea:

- If we don't consider biking and running, different portions of swimming times make no difference
- The person with longer time to finish biking+running use the pool first

#### Proof

- Inversion: schedule athelete i before athelete j where $(b_i+r_i)$ is less than $(b_j+r_j)$
- Show that removing this inversion will not increase the complete time but decrease the complete time
- Therefore, we schedule the person with less $(b_i+r_i)$ first

---

## Priority Queues

### Functions/Definitions:

- Insert an element into the set **very fast**
- Find the smallest/largest element in the set **very fast**

### Implementation

- #### Using basic data structures

|Data structure| Insert | Find|
|---|---|---|
|Unsorted Array|O(1)| O(n)|
|Sorted Array| O(n)| O(1)|
|Linked List| O(1)| O(n)|
|Sorted Linked List| O(n)| O(1)|

- #### Background of binary trees
  
  - **Full binary tree** fillin every node
  - **Complete binary tree** fillin every node except last level, last level from left to right

- #### Traversing a complete binary tree stored in an array
  - Navigation: For every node Node[i] (⚠️ Node index start from 1)
    - Its parent(i): Node[i/2] or it is a root
    - Its lChild(i): Node[2i]
    - Its rChild(i): Node[2i+1]

- #### Max heap
  - a complete binary tree in which the value in each internal node is greater than or equal to the values in the children of that node
  - ##### Insert method:  -- $O(logn)$
    - Insert the new item to the end
    - Trickle up to make sure it is a max heap
  - ##### Extract_max / pop method:  -- $O(logn)$
    - Pop the root which is the largest item
    - Take the last node up to the root
    - Trickle down to make sure it is a max heap
  - ##### Delete method: -- $O(logn)$
    - Remove the item
    - Take the last one fill in the gap
    - Trickle up or down, depending on its parent and children (**But only need to do one-way trickle)**
  - ##### Change key value: -- $O(logn)$
    - Change an arbitrary key value in the max heap
    - Trickle down or trickle up
  - ##### Constructions of a Max Heap
    - Case 1 : Bottom-up construcions ---> $O(n)$
    - **Proooooof!!** on slides
  - ##### Merge two max heaps of size n --->$O(n)$
    - Linear time complexity using **Bottom up constructions**

#### Problem:
Input: Array of n elemetns
Output: Top k elements
Constraints: No additioanl memory && $O(nlogk)$

##### Idea:
- Construct min heap of size k $O(k)$
- Check all the remaining elements: if larger than the samllest one, move in, else, skip: $O((n-k)logk)$

### Binomial Tree / Binomial Min Heap

  - Find min: $O(logn)$
  - Insert: $O(logn)$
  - Merge two trees: $O(logn)$

---

## Discussions:

### Problem 3:

6

### Problem 4:

Done above

### Problem 5

Compare $Root_a$ and $Root_b$ every time,
If $Root_a$ <$Root_b$, Drop $Root_a$ on A_Tree;
else if $Root_a$ > $Root_b$, Drop $Root_b$ on B_Tree;
else, return true.

