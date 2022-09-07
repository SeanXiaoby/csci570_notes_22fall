# CSCI-570 HW-2

- **Author:** Boyang Xiao
- **Due Date:** Sep. 7<sup>th</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>

---

### Problem 1

**Descriptions:** What is the worst-case runtime performance of the procedure below?

```
c = 0
i = n
while i >1 do
	for j= 1 to i do
		c = c+ 1
		end for
	i= floor(i/2)
end while
return c
```

Provide a brief explanation for your answer.

#### Answer:

The worst-case runtime performance is **O(nlogn)**.

For the outer loop, i starts from n and desend into half every iteration till it reaches 1. So the outer loop has a complexity of **O(logn)**

For the inner loop, it is linear for every i and j goes through i times of iterations for every i. Therefore, the whole runtime complexity adds up to **O(nlogn)**.


---
### Problem 2

**Descriptions**: Arrange these functions under the O notation using only = (equivalent) or ⊂ (strict subset of):

- (a) $2 ^{\log n} $
- (b) $2^{3n}$
- (c) $n^{n\log n}$
- (d) $\log n$
- (e) $n\log n^2$
- (f) $n^{n^2}$
- (g) $\log (\log (n^n))$

#### Answers:

**In increasing order: (d) ⊂ (g) ⊂ (e) ⊂ (c) ⊂ (a) ⊂ (b)**

First, we simplifiy them into Big O notations:

- $2 ^{\log n} $ --> $O(2 ^{\log n})$ 
- $2^{3n}$ --> $O(2^{3n})$
- $n^{n\log n}$ --> $O(n^{n\log n})$
- $\log n$ --> $O(\log n)$
- $n\log n^2$ --> $O(n\log n)$
- $n^{n^2}$ --> $O(n^{n^2})$
- $\log (\log (n^n))$ --> $O(\log (n\log (n)))$

Then we put them in orders of **Logarithmic -> Polynomial -> Exponential**:

$O(\log n)$ ⊂ $O(\log (n\log (n)))$ ⊂ $O(n\log n)$ ⊂ $O(n^{n\log n})$ ⊂ $O(n^{n^2})$ ⊂ $O(2 ^{\log n})$ ⊂ $O(2^{3n})$

And we got the answer: 

**(d) ⊂ (g) ⊂ (e) ⊂ (c) ⊂ (a) ⊂ (b)**

---

### Problem 3

#### Answers

##### (a) $f_1(n) · f_2(n) = O (g_1(n) · g_2(n))$ --- **True**

Accrording to Big O notation definitions:

If we got $f_1(n) < c_1g_1(n)$ and $f_2(n) < c_2g_2(n)$, for large n,

Then $f_1(n)·f_2(n) < c_1c_2g_1(n)g_2(n)$, which is equivalent to $f_1(n)·f_2(n) < cg_1(n)g_2(n)$, 

That is: $f_1(n) · f_2(n) = O (g_1(n) · g_2(n))$ Q.E.D.

##### (b) $f_1(n) + f_2(n) = O (max(g_1(n) , g_2(n)))$ --- **True**

If we got $f_1(n) < c_1g_1(n)$ and $f_2(n) < c_2g_2(n)$, for large n,

Then $f_1(n)+f_2(n) < c_1g_1(n)+c_2g_2(n)$, which is equivalent to $f_1(n)+f_2(n) < c·max(g_1(n),g_2(n))$, 

That is: $f_1(n) + f_2(n) = O (max(g_1(n) , g_2(n)))$ Q.E.D.

##### (c) $f_1(n)^2 = O(g_1(n)^2)$ --- **True**

If we got $f_1(n) < c_1g_1(n)$ ,for large n,

Then: $f_1(n)^2 < c_1^2g_1(n)^2$, which is equivalent to $f_1(n)^2 < c·g_1(n)^2$

That is: $f_1(n)^2 = O(g_1(n)^2)$

##### (d) $log_2f_1(n) = O(log_2f_1(n))$ --- **True**

If we got $f_1(n) < c_1g_1(n)$ ,for large n,

Then: $log_2f_1(n) < log_2(c·g_1(n))$

--> $log_2f_1(n) < c_3log_2(g_1(n)) + log_2c$ --->$log_2f_1(n) < clog_2(g_1(n))$

That is: $log_2f_1(n) = O(log_2f_1(n))$ Q.E.D.

---

### Problem 4

**Descriptions**: Given an undirected graph G with n nodes and m edges, design an O(m+
n) algorithm to detect whether G contains a cycle. Your algorithm should
output a cycle if G contains one.

#### Answer
**Main Idea**: We use the DFS to iterate all nodes and marked them as VISITED if so. If we visit a visited node again during the DFS iterations, we can say that there is at least one cycle lying in the graph. Else, there is no cycle.

**Steps:**
1. We create a table to record if nodes are visited, initialize them to be false(not vistited). We choose an arbitrary as the starting node and mark it as visited.
2. We detect if the starting node's adjacent nodes are visted. If there is any node visited, we can return true(there is a cycle). If not, we iterate every adjacent node ,use them as the new parent node and call this same step recursively.
3. After the above recursion is over, we check if there is any node not visited. If is, we start Step 2 again on that node and repeat this until all nodes recorded are visited.
4. If all nodes are visited without quiting half-way, there is no cycle. If any node is visited twice, there is at least one cycle.

---

### Problem 5

**Description**: We have a connected graph G = (V, E), and a specific vertex u ∈ V. Suppose we compute a depth-first search tree rooted at u, and obtain a tree T that includes all nodes of G. Suppose we then compute a breadth-first search tree rooted at u, and obtain the same tree T. Prove that G = T. (In other words, if T is both a depth-first search tree and a breadth-first search tree rooted at u, then G cannot contain any edges that do not belong to T.)

##### Answer

Let's suppose there is an edge f that belongs to G but does not belong to T, and the two ends of f are x and y. Since T is a DFS tree, x and y must differ by one level on the tree, say x is higher and y is lower. Than the distance of (u,x) is at most 1 less than that of (u,y), since T is a BFS tree rooted from u. That is to say x is the parent of y and there should be an edge on T that connects x and y, which contradicts the assumption.

Therefore, we can say that every edge on G belongs to T.

---

### Problem 6 (Ungraded)

**(a)** $O(n^3)$

**(b)** For the outer loop, it always goes through n iterations, so it always has a tight lower bound of $\Omega(n)$. For the inner loop, when $i = n/2$, it can reach a lowest value, that is, j goes througth n/2 iterations and adding up items from A[i] to A[j] takes n/2 iterations at least. So the inner loop has a tight lower bound of $\Omega(n^2/4) = \Omega(n^2)$. To add up, the whole algorithm has a tight lower bound of $\Omega(n^3)$ as same as the tight upper bound, so the running time is $\Theta(n^3)$.

**(c)** Didn't get what it means :(