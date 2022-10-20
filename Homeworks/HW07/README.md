# CSCI 570 - Homework 07

- **Author:** Boyang Xiao
- **Due Date:** Oct. 19<sup>th</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>

--- 

## Problem 1

### Answer

a. Subproblem: When we land on a posistion of the array, if the previous sum can get larger when adding the current item, then we update the current sum with this result, othtewise, we use the current item as the current sum.

b. Recurrence relations: Define $OPT[i]$ as the max sum we get from item 0 to i.

$$OPT[i] = max(OPT[i-1]+nums[i], nums[i])$$

c. Psuedo codes:

```python
for i = 1:n
    OPT[i] = max(OPT[i-1] + nums[i], nums[i])
end for
```

d. Base case: $OPT[0] = nums[0]$. Final answer is the value of $OPT[n]$

e. Runtime complexity: $O(n)$.  Space complexity: $O(n)$

---

## Problem 2

### Answer:

We assume that we can hold at most one share of stock at one time.

a. For each day, we can hold a share of stock or do not hold any stock. If we do not hold a share, we could have sold a share the day before and we sell it or we did not hold a share the day before. Same, if we hold a share today, we could have no stock the day before and just bought it today or we held the same share the day before.

b. We define $OPT[i][b]$ to be the the max profits we made from day 0 to day i. If $b == 0$, we do not have stock on day i, else if $b == 1$, we have stock on day i. Assume the transaction fee is T.

$$OPT[i][0] = max(OPT[i-1][0], OPT[i-1][1]+prices[i]-T) \\
OPT[i][1] = max(OPT[i-1][1], OPT[i-1][0]-prices[i]-T)$$

c. Psuedo codes

```python
for i = 1:n
    OPT[i][0] = max(OPT[i-1][0], OPT[i-1][1]+prices[i]-T)
    OPT[i][1] = max(OPT[i-1][1], OPT[i-1][0]-prices[i]-T)
end for
```

d. Base cases: 

$$OPT[0][0] = 0\\
OPT[0][1] = -prices[0]-T$$

Final answer:

$$max(OPT[n][0], OPT[n][1])$$

e. Time complexity: O(n), Space complexity: O(n)

---

## Problem 3

### Answer:

a. Subproblem:  For each item in the given array, we have to find all the items before it that are lower than it, compare which one of them can make highest happiness score within this current item and save this result.

b. We define $OPT[i]$ as the maximum happiness score we got cosidering the item index from 0 to i.

To simplify the description, we define a function that can calculate the happiness score for specified item index: $CalHappy$(int newIndex, int LastIndex)

$OPT[i] = max(CalHappy(i,j))$ for all j that: $a[j]<a[i]$

If there is no such j existing prior to i, then $OPT[i] = a[i]$

c. Psuedo codes:

```python
for i = 1: n
    for j = n-1:1
        if a[i] > a[j]
            OPT[i] = max[OPT[i], CalHappy(i,j)]
        end if
    end for
end for
```

d. Base case: $OPT[0] = a[0]$. Final result: $OPT[n]$

e. Runtime complexity: $O(n^2)$

---

## Problem 4

### Answer:

a. Subproblem: For each item in the matrix, say the coordinate is $(i,j)$, if the small square before it (items at $(i-1,j), (i, j-1), (i-1,j-1)$) are all 1's, then we expand the maximum squre's side length by 1. Else, we start over using the current item as the first corner of the new square.

b. We define $OPT[i][j]$ as the maximum square side length if we only consider the rectagle area of $(0:i, 0:j)$.

If $g[i][j] == 1$:

$OPT[i][j] = min(OPT[i-1][j], OPT[i][j-1], OPT[i-1][j-1]) + 1$

Else if $g[i][j] != 1$:

$OPT[i][j] = 0$

c. Psuedo codes:

```python
for i = 1:m
    for j = 1:n
        if g[i][j] == 1
            OPT[i][j] = min(OPT[i-1][j], OPT[i][j-1], OPT[i-1][j-1]) + 1
        else if g[i][j] == 0
            OPT[i][j] = 0
        end if
    end for
end for
```

d. Base case: 

$OPT[i][0] = g[i][0]$ for $i = 0:m$

$OPT[0][j] = g[0][j]$ for $j = 0:n$

Final result: $OPT[m][n]$

e: Time complexity: $O(mn)$, Space complexity: $O(mn)$