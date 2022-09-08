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

#### Idea

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
