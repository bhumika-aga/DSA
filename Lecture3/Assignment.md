# 🧪 Assignment 3 — Testing & Debugging Your Own Code

> **Lecture:** 3 of 45 — Testing & Debugging Your Own Code
> **Phase:** 1 — Foundations
> **Estimated Time:** 3 days · **Total Problems:** 15 (12 Easy · 3 Medium · 0 Hard)
> **Goal:** Find your own bugs before anyone else does: trace by hand, run the edge-case checklist, and read a judge's verdict calmly.
> **No Java yet:** for each problem, write the edge cases and trace your idea by hand. Code them after Lecture 4.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                 | Pattern                    | Move                                       |
| ------------------------------------- | -------------------------- | ------------------------------------------ |
| Multiplying or adding many values     | Watch for overflow         | Compute the property, not the value        |
| Values can be equal                   | Check strict vs non-strict | Test with all-equal input                  |
| Processing runs or groups             | Leftover-group bug         | Handle the last group after the loop       |
| Dates, times, versions, addresses     | Parsing edge cases         | Write every rule down first                |
| Several possible verdicts or outcomes | Enumerate all cases        | Test one input per outcome                 |
| Geometry with points and lines        | Degenerate cases           | Duplicates, collinear points, zero lengths |
| A process that repeats                | Simulate one cycle         | Reason about what one cycle proves         |

---

## 🟢 Easy Tier (12 Problems)

_Easy algorithms, tricky edges. For each one, write the edge cases you will test before anything else — the hint tells you which one catches most people._

### E1 · Sign of the Product of an Array

**🔗 [LC 1822 — Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/)** · Easy
**Pattern:** Avoid overflow | **Companies:** Amazon, Microsoft

**Hint:** Multiplying overflows. You only need the sign: any zero, and how many negatives.

---

### E2 · Monotonic Array

**🔗 [LC 896 — Monotonic Array](https://leetcode.com/problems/monotonic-array/)** · Easy
**Pattern:** Equal values | **Companies:** Amazon, Google

**Hint:** Test with [2, 2, 2] and [1]. Both are monotonic — does your check agree? Use ≤ and ≥, not < and >.

---

### E3 · Consecutive Characters

**🔗 [LC 1446 — Consecutive Characters](https://leetcode.com/problems/consecutive-characters/)** · Easy
**Pattern:** The leftover run | **Companies:** Amazon, Google

**Hint:** Trace "aaa". If the best is only updated when a run ends, the last run is never counted.

---

### E4 · Longer Contiguous Segments of Ones than Zeros

**🔗 [LC 1869 — Longer Contiguous Segments of Ones than Zeros](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/)** · Easy
**Pattern:** Two counters, last run | **Companies:** Amazon

**Hint:** Same leftover bug twice over — both the longest ones-run and zeros-run can end at the last character.

---

### E5 · Remove Trailing Zeros From a String

**🔗 [LC 2710 — Remove Trailing Zeros From a String](https://leetcode.com/problems/remove-trailing-zeros-from-a-string/)** · Easy
**Pattern:** String boundaries | **Companies:** Amazon

**Hint:** What if the whole string is… well, it cannot be all zeros here. Check the constraints to see which edge cases you can skip.

---

### E6 · Slowest Key

**🔗 [LC 1629 — Slowest Key](https://leetcode.com/problems/slowest-key/)** · Easy
**Pattern:** Tie-breaking | **Companies:** Amazon

**Hint:** Ties are broken by the larger letter. Write a tie example first. The first key's duration is releaseTimes[0], not a difference.

---

### E7 · Check if One String Swap Can Make Strings Equal

**🔗 [LC 1790 — Check if One String Swap Can Make Strings Equal](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/)** · Easy
**Pattern:** Enumerate the cases | **Companies:** Amazon, Google

**Hint:** Zero differences, exactly two differences that swap, or anything else. Trace "aa" vs "aa" and "ab" vs "ba".

---

### E8 · Valid Boomerang

**🔗 [LC 1037 — Valid Boomerang](https://leetcode.com/problems/valid-boomerang/)** · Easy
**Pattern:** Degenerate inputs | **Companies:** Google

**Hint:** Duplicate points and collinear points both fail. The cross-product test catches both in one line — and avoids dividing by zero.

---

### E9 · Day of the Year

**🔗 [LC 1154 — Day of the Year](https://leetcode.com/problems/day-of-the-year/)** · Easy
**Pattern:** Leap years | **Companies:** Amazon

**Hint:** Divisible by 4 — unless divisible by 100 — unless divisible by 400. Test 1900, 2000 and 2004.

---

### E10 · Find Winner on a Tic Tac Toe Game

**🔗 [LC 1275 — Find Winner on a Tic Tac Toe Game](https://leetcode.com/problems/find-winner-on-a-tic-tac-toe-game/)** · Easy
**Pattern:** All the outcomes | **Companies:** Amazon, Google

**Hint:** Four answers: A, B, Draw, Pending. A game can be won before the board is full — and "Pending" is easy to forget.

---

### E11 · Distribute Candies to People

**🔗 [LC 1103 — Distribute Candies to People](https://leetcode.com/problems/distribute-candies-to-people/)** · Easy
**Pattern:** Last partial round | **Companies:** Amazon

**Hint:** The final person may get fewer candies than their turn asks for. That leftover case is the whole bug.

---

### E12 · Reformat Date

**🔗 [LC 1507 — Reformat Date](https://leetcode.com/problems/reformat-date/)** · Easy
**Pattern:** Parsing and padding | **Companies:** Amazon

**Hint:** Day "1st" becomes "01"; single-digit days need padding. Test the 1st, 2nd, 3rd, 11th and 22nd.

---

## 🟡 Medium Tier (3 Problems)

_Parsing and simulation problems where the difficulty is completeness. Write every rule down as its own line first._

### M1 · Compare Version Numbers

**🔗 [LC 165 — Compare Version Numbers](https://leetcode.com/problems/compare-version-numbers/)** · Medium
**Pattern:** Different lengths, leading zeros | **Companies:** Amazon, Google, Microsoft

**Hint:** "1.0" equals "1.0.0" and "01" equals "1". Pad the shorter version with zeros.

---

### M2 · Validate IP Address

**🔗 [LC 468 — Validate IP Address](https://leetcode.com/problems/validate-ip-address/)** · Medium
**Pattern:** One check per rule | **Companies:** Amazon, Microsoft, Meta

**Hint:** List every rule before coding. "1..1.1", "01.1.1.1", "256.1.1.1" and a trailing "." should all fail.

---

### M3 · Robot Bounded In Circle

**🔗 [LC 1041 — Robot Bounded In Circle](https://leetcode.com/problems/robot-bounded-in-circle/)** · Medium
**Pattern:** Simulate one cycle | **Companies:** Amazon, Google

**Hint:** After one run of the instructions, the robot is bounded if it is back at the start OR not facing north. Test a single "L".

---

## 🔴 Hard Tier (0 Problems)

_No Hard problems here — the Medium tier already contains two of the most edge-case-heavy problems on LeetCode._

## 📊 Complexity Analysis Exercises

Counting exactly — not just the Big-O — is how off-by-one errors are caught. Give the exact count for each.

```pseudocode
// Snippet 1 — how many times does the body run?
for i from 0 to n - 1:
    body()

// Snippet 2 — how many times does the body run?
for i from 1 to n:
    body()

// Snippet 3 — how many times does the body run?
i ← 0
while i ≤ n:
    body();  i ← i + 1

// Snippet 4 — pairs (i, j) with i < j, visited by:
for i from 0 to n - 1:
    for j from i + 1 to n - 1:
        visit(i, j)

// Snippet 5 — a fence of length L with a post every metre.
// How many posts?

// Snippet 6 — the stress test from the lecture runs 1,000 trials,
// each calling an O(n²) brute force on n ≤ 8. Roughly how many steps?
```

**Complexity Answers:**

1. **n** times — i takes the values 0, 1, …, n − 1.
2. **n** times — i takes the values 1, 2, …, n. Same count, different values: a classic source of off-by-one.
3. **n + 1** times — ≤ includes n itself.
4. **n(n − 1) ÷ 2** pairs — O(n²).
5. **L + 1** posts — the fencepost question.
6. About **1,000 × 64 = 64,000** steps — trivial. Small inputs make stress testing cheap.

---

## 🔍 Self-Assessment — True / False

1. If a solution passes all the example tests, it is correct. → **False** — the examples are chosen to be friendly; hidden tests target the edges
2. An integer overflow crashes the program so you notice it. → **False** — it silently wraps to a wrong value
3. "for i from 0 to n − 1" and "for i from 1 to n" run the same number of times. → **True** — n times each, over different values
4. Time Limit Exceeded means the answer is wrong. → **False** — it means the answer took too long — often a Big-O problem
5. A trace table is only useful for beginners. → **False** — it is the fastest reliable way to find a bug in short code, at any level
6. Starting a "maximum so far" variable at 0 is always safe. → **False** — it fails when every value is negative
7. Comparing two decimal results with = can fail even when the maths says they are equal. → **True** — 0.1 + 0.2 is not exactly 0.3 in floating point

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Trace table**: Draw one for the leftover-bug example on "aabbb" and point to the exact row where the answer goes wrong.
2. **Checklist**: Recite the edge-case checklist and, for Monotonic Array, say which rows matter and which do not.
3. **Off-by-one**: Give the four boundary questions and one example of a bug caused by each.
4. **Invariant**: State an invariant for a loop that finds the largest value in a list.
5. **Verdicts**: For each of Wrong Answer, Time Limit, Runtime Error and Memory Limit, name the first thing you would check.
6. **Stress testing**: Explain how a slow brute force helps you test a fast solution, and why small random inputs are enough.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Day of the Year](https://leetcode.com/problems/day-of-the-year/), [Distribute Candies to People](https://leetcode.com/problems/distribute-candies-to-people/), [Longer Contiguous Segments of Ones than Zeros](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/), [Reformat Date](https://leetcode.com/problems/reformat-date/)             |
| **Google**    | [Valid Boomerang](https://leetcode.com/problems/valid-boomerang/), [Robot Bounded In Circle](https://leetcode.com/problems/robot-bounded-in-circle/), [Check if One String Swap Can Make Strings Equal](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/), [Consecutive Characters](https://leetcode.com/problems/consecutive-characters/) |
| **Microsoft** | [Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/), [Compare Version Numbers](https://leetcode.com/problems/compare-version-numbers/), [Validate IP Address](https://leetcode.com/problems/validate-ip-address/)                                                                                                          |
| **Meta**      | [Validate IP Address](https://leetcode.com/problems/validate-ip-address/)                                                                                                                                                                                                                                                                                                |

---

## ✅ Completion Checklist

- [ ] All 12 Easy problems solved
- [ ] All 3 Medium problems solved
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I wrote an edge-case list for each problem before looking at its hint
- [ ] I traced at least three of my solutions with a full trace table
- [ ] I have come back after Lecture 4 and coded all 15

---

**← [Lecture 2 · Attacking an Unseen Problem](../Lecture2/Assignment.md)** &nbsp;·&nbsp; **[Lecture 4 · Java & Programming Fundamentals](../Lecture4/Assignment.md) →**
