# CSCI-570 HW-1

- **Author:** Boyang Xiao
- **Due Date:** Aug. 31<sup>st</sup> 2022
- **USC id**: 3326-7302-74
- **Email**: <a href="mailto:boyangxi@usc.edu">boyangxi@usc.edu</a>

---

### Problem 1

**Descriptions:** Decide whether you think the following statement is true or false. If it is true, give a short explanation. If it is false, give a counterexample.

- True or false? In every instance of the Stable Matching Problem, there is a stable matching containing a pair (m, w) such that m is ranked first on the preference list of w and w is ranked first on the preference list of m

#### Answer: FALSE

Let's suppose there are only two men(m1,m2) and two women(w1, w2). The preference lists are like:

- $m_1: w_2, w_1$
- $m_2: w_1, w_2$
- $w_1: m_1, m_2$
- $w_2: m_2, m_1$

The instance of a stable matching is that: {$(m_1,w_2)$, $(m_2, w_1)$}. There is no instability and it does not comply to the statement. So the statement is false.

---

### Problem 2

**Descriptions**: Decide whether you think the following statement is true or false. If it is true, give a short explanation. If it is false, give a counterexample.

- True or false? Consider an instance of the Stable Matching Problem in which there exists a man m and a woman w such that m is ranked first on the preference list of w and w is ranked first on the preference list of m. Then in every stable matching S for this instance, the pair (m, w) belongs to S.

#### Answer: TRUE

Let's suppose there is one statble matching that does not have this pair, say (m,w') and (m'', w). Then there is instability right in this two pairs, because m has a higher preference w while w has a higher preference m, too. So this situation does not exist.

---

### Problem 3

**Descriptions**:Determine whether the following statement is true or false. If it is true, give an example. If it is false, give a short explanation. (5pts)

- For some n ≥ 2, there exists a set of preferences for n men and n women such that in the stable matching returned by the G-S algorithm, every woman is matched with their most preferred man, even though that man does not prefer that woman the most.

#### Answer: TRUE

Given women's preference list below:

- $w_1: m_1, m_2, m_3$
- $w_2: m_2, m_3, m_1$
- $w_3: m_3, m_1, m_2$

We don't care men's preference list and we let the women propose first. Then every woman will get their highest ranked choice and there is no instability because even though some man might has a better choice over their match, the preferred woman has already get a the highest choice so it does not form instatbilty.

---

### Problem 4

**Descriptions** : Four students, a, b, c, and d, are rooming in a dormitory. Each student ranks the others in strict order of preference. A roommate matching is defined as a partition of the students into two groups of two roommates each. A roommate matching is stable if no two students who are not roommates prefer each other over their roommate.

Does a stable roommate matching always exist? If yes, give a proof. Otherwise, give an example of roommate preferences where no stable roommate matching exists. (8pts)

#### Answer: Not always exsiting

Say the preference lists given below:

- a: b, c, d
- b: c, a, d
- c: a, b, d
- d: a, b, c

Then we have three ways to match:

- (a,b) and (c,d): b, c make the instability
- (a,c) and (b,d): b, a make the instability
- (a,d) and (b,c): a, c make the instability

---

### Problem 5

#### Answer:

##### Algorithm idea:

- We start from letting every student to apply for the job from their highest ranked hospital to lowest ranked hospital one by one in a loop. If the hospital refuses the student, then the student goes to the next hospital on the his/her preference list. If all the hospitals refuse the student, the student then is not assigned.
- From the hospital side, if it receive a student's application AND it still got empty postions, it will accept the student immediately. If the postions are all filled, it will compare the student with the hospitals' prefenrence list and replace the student with the lowest ranked student that they have already accepted. If the current student is of the lowest rank, they will refuse this student.
- If the some student is kicked out from a hospital(gets replaced in STEP2.), then he/she will go to the next hospital on his/her preference list, and repeat the last two steps.
- We end the loop until all the students have gone through their preference lists.

##### Proof of that there is always a stable assignment.

- Suppose there exists the first kind of instability. If s applies earlier than s', then when s' comes to hospital h, he/she will kicked s out and enter h, which is contradictory to the statement. Else if s' applied ealier than s, then when s comes to h, h will not kick s' because of s. So this instatbility does not exist.
- Suppose there exists the second kind of instatbility. If s applies earlier than s' and s is settled in hospital h, then when s' will come to h first and h will accept s' but not let s' to go to the next hospital. Even if s' is kicked by someone else in hospital h, s should be kicked out earlier than s' because h prefer s' than s. So this instatbility does not exisit.

$Q.E.D.$

---

### Problem 6

#### Answer: NO

**Proof**

If the men propose, and m, m' propose earlier than m''.  Even though we switch m and m' on w's list and w might have chosen m' before m'' comes. But m'' will not come to w because w might have a very low rank on m'' 's preference list so this will not help.

If women propose, w will propose to m'' directly and w might be beaten by someone else because she has a low rank on m'' 's list and then w finally will come back to m and m'.

---

### Problem 7

**Descriptions**: Determine whether the following statement is true or false. If it is true, give a short explanation. If it is false, give a counterexample. (5pts)
- For all n ≥ 2, there exists a set of preferences for n men and n women such that in the stable matching returned by the G-S algorithm, every man is matched with their most preferred woman.

#### Answer: TRUE

Given a list below:

- $m_1: w_1, w_2, w_3$
- $m_2: w_2, w_3, w_1$
- $m_3: w_3, w_1, w_2$

We let the men propose and this statement can hold no matter what women's preference lists look like.

---

### Problem 8

#### Answer:

In a statle matching solution returned by G-S algorithm, suppose there exists instatbility, say a pair ($m_i, w_j$), where $m_i$ prefer $w_i$ over $w_j$ ($i<j$) and $w_i$ prefer $m_i$ over $m_j$. Then this pair would never exist. So we can say that there is always a stable matching.