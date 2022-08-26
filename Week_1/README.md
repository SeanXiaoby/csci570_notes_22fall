# CSCI-570
### Week 01 - Aug. 24th 2022

### Contents

- Greedy
- Devide and conquere

---

- DP
- Network flow

---

- Computational complexity theory
- approximation algorithms
- Linear Programming

### Pre-requisites

- Discrete Maths
- Sorting algorithms
- Basic data structures
- Graph
- Graph searching algorithms: BFS DFS

## Introductions

- ### Why algorithms
  
- ### Solve a problem faster
  
  - Performance -->Hardwares / Softwares
  - Understand the **hardware** / Focus on the **Softwares**
  - Example:
    - **Parallel Processing**
      - SMP
      - DMP
    - **Memory Hierachy**
- ### Soving a problem
  
  When studying a problem, follow these steps:
  
  - Come up with a concise problem statement
  - Present a solution
  - Prove correctness
  - Perform complexity analysis
 ---
- ### Example problem: *Stable Matching*
    ##### Problem Statement: 
    - n men: {m1, m2, m3....mn}
    - n women: {w1, .... wn}
    - Attempt **perfect matching**: one man to one woman
    - Each man/woman has a peferance list: From best to worst
    - **Satble Matching**: Perfect matching + no instatblity
    - Input: Peference lists of men and women
    - Output: Set of n pairs w/ no instability
    ##### Solution: Gale-Shapley algorithm:
    - Pick a man and match to the woman of his list top
    - Pick the next man and match to the woman of his list top
    - If they are matched to the same woman, decide from the woman's list to save the higher man
    - Match the other man to the next woman of his list
    - Iterate all the men like this
    ##### Proof of correctneess
    - From the women's sides: they can only get into better engagements
    - From the men's sides: they may get rejected repeatly only to settle for a lower ranking woman
    - Worst runtime complexity: O(n^2) to get a perfect matching
    - **Need to show that the matching has no instability:**
        - **Proof by contradictions**
    - ⚠️ **Stable matching does not have to be unique**
        - If starting from men proposing: men end up with their best partners
        - If ... women, women ... best partners.
        - Woman w is **valid** partner of man m if there is one stable matching that contains pair(m, w)
    ##### Complexity analysis
    - Preparations: Flipping women's preference lists(ranking->man's id) into ranking lists(man's id->ranking): **O(n^2)**
    - GS-Alg: **O(n^2)**
    ##### Claims issue1: If starting from the men, every man will get their best valid partners
    - Proof by contradictions
    ##### Claim issue2: If starting from women, every man will end up with getting their worst valid partner
