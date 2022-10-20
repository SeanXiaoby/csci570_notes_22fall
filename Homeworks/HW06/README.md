# CSCI 570 - Homework 06

- **Author:** Boyang Xiao
- **Due Date:** Oct. 12<sup>th</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>

--- 

## Problem 1

### Answer

We set $OPT[i][w]$ to be the optimal value when we only get items from $0~i$ and the backpack capacity is $w$.

Then we have:$$OPT[i][w] = max(OPT[i-1][w], OPT[i][w-w_i]+v[i])$$

That is:

```python
for i = 1:n
    for w = 0:W
        OPT[i][w] = max(OPT[i-1][w], OPT[i][w-w_i]+v[i])
    endif
endif
```

And we initialize all $OPT$ with $w == 0$ to be 0.

After we iterate all the i and w, the value $OPT[n][W]$ should be our final result.

---

## Problem 2

### Answer

We set $OPT[i]$ to be true if the sub-string of the first i characters can be segmented into words in the dictionary, else to be false.

Then we got: $$\begin{align}
    OPT[i] = (OPT[i-1] == true) \And (substr[i-1 : i] \in dict) || \\ 
    = (OPT[i-2] == true) \And (substr[i-2 : i] \in dict) || \\
    = (OPT[i-3] == true) \And (substr[i-3 : i] \in dict) || \\
    = ...                                                    \\
    = (OPT[0] == true) \And (substr[0 : i] \in dict) ||
\end{align}$$ 

That is:

```python
for i = 0 : string.size()
    if string.substr(0:i) in dict
        OPT[i] = true
    endif
    for j = i+1 ： string.size()
        if string.substr(i:j) in dict
            OPT[j] = true
        endif
    endfor
endfor
```

And the value $OPT[string.size()]$ should be our final answer.

---

## Problem 3

### Answer

We define $OPT(i,j)$ to be the optimal value to burst the balloons between index i and index j.

Say we pick $k$ that: $i\leq k \leq j$ to be the last one to be burst in these balloons, than we got:

$$OPT(i,j) = max(OPT(i,j), nums[i-1]*nums[k]*nums[j+1]+OPT(i,k-1)+OPT(k+1, j))$$

We initialize all the OPT values with $i ==j$ to be $nums[i-1]*nums[i]*nums[i+1]$ and we iterate the dp arrays in a asending order of difference between i and j.

The final result should be the value of $OPT(0, n-1)$

---

## Problem 4

### Answer

We set $OPT[i][n]$ to be the maximum value when the rod length equals to $n$, and the current index is i

For each index, we have two options: to cut the rod here or not to cut. Then we got:

$$OPT(n) = max(OPT[i-1][n], OPT[i-1][n-i]+p_i)$$

We also have to initialize: $OPT[0][n] = n*p_0$

---

## Problem 5

### Answer

We set $OPT(n)$ to be the minimum slack value if we only consider words from 0 to n.

Then we got:

$OPT(n) = min(Slack(i:n)+OPT(i))$ for each $i = 1:n$

That is:

```python
for n = 1:N
    for i = 1:n
        OPT(n) = min(Slack(i:n)+OPT(i))
    endfor
endfor
```

And the value $OPT(N)$ should be the final result.

---


## Problem 6

### Answer (a)

A counter-example:

|Minutes| 1|2|3|4|
|---|---|---|---|---|
|A|5|1|1|10000|
|B|1|1|3|10|

In this example, the greedy algorithm provided will choose: $a_1, move, a_3, move$, which adds up to be 10. However, the optimal solution should be $a_1, a_2, a_3, a_4$, which adds up to be 10007.

### Answer (b)

Dynamic programming solution:

We set two memorization array $OPT_a(i) and OPT_b(i)$ to be the optimal value when we consider the sequence from 1 to i, and the current machine is A or B.

Then, the origin of the $i^{th}$ minute choice can come from two ways. For example, if at the $i^{th}$ minute we are using machine A, then it can either be proceeded with machine A from the ${i-1}^{th}$ minute or be moved from machine B from the ${i-2}^{th}$ minute. That is:

$$OPT_a(i) = a_i + max(OPT_a(i-1), OPT_b(i-2)+1)$$

We initialize $OPT_a(1) = a_1$ and $OPT_b(1) = b_1$ and calculate in recurrence all the way to OPT_a(n) and OPT_b(n) and the maximum value among these two should be our final result.