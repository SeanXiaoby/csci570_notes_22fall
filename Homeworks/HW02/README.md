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


