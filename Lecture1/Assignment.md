# 🚀 Assignment 1 — How Fast Is It? — Complexity Analysis

> **Lecture:** 1 of 45 — How Fast Is It? — Complexity Analysis
> **Phase:** 1 — Foundations
> **Estimated Time:** 4 days · **Total Problems:** 20 (15 Easy · 5 Medium · 0 Hard)
> **Goal:** Read the cost of any solution from its structure, and turn a problem's size limit into the speed your solution needs.
> **No Java yet:** every task here can be done on paper — describe the obvious solution, then state its Big-O. Come back after Lecture 4 and code them.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                | Pattern            | Move       |
| ---------------------------------------------------- | ------------------ | ---------- |
| One pass over the input                              | Linear             | O(n)       |
| A loop inside a loop over the same input             | Quadratic          | O(n²)      |
| The problem halves (or divides) something every step | Logarithmic        | O(log n)   |
| Sort first, then scan                                | Sort-dominated     | O(n log n) |
| A loop of fixed length (26 letters, 10 digits)       | Constant           | O(1)       |
| n ≤ 20 and "every subset"                            | Exponential        | O(2ⁿ)      |
| Simulation that gives a suspiciously clean pattern   | Look for a formula | Often O(1) |

---

## 🟢 Easy Tier (15 Problems)

_For each problem: read it, describe the obvious solution in one sentence, and write down its Big-O. Only then read the hint. You are practising analysis, not coding — you will code these after Lecture 4._

### E1 · Count Good Triplets

**🔗 [LC 1534 — Count Good Triplets](https://leetcode.com/problems/count-good-triplets/)** · Easy
**Pattern:** Nested loops, counted exactly | **Companies:** Amazon, Google

**Hint:** Three loops, O(n³). Now read the constraint: n ≤ 100. Is O(n³) fast enough? Say why before you decide to optimise.

---

### E2 · Build Array from Permutation

**🔗 [LC 1920 — Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/)** · Easy
**Pattern:** Single pass | **Companies:** Amazon, Google

**Hint:** One pass builds the answer — O(n) time, O(n) space. Follow-up: can you do it in O(1) extra space by storing two numbers in one slot?

---

### E3 · Find Numbers with Even Number of Digits

**🔗 [LC 1295 — Find Numbers with Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/)** · Easy
**Pattern:** Digit counting | **Companies:** Amazon

**Hint:** Counting digits of x takes about log₁₀(x) steps. So the whole thing is O(n · d), where d is the number of digits.

---

### E4 · Average Salary Excluding the Minimum and Maximum Salary

**🔗 [LC 1491 — Average Salary Excluding the Minimum and Maximum Salary](https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/)** · Easy
**Pattern:** One pass vs sorting | **Companies:** Amazon, Google

**Hint:** Sorting gives min and max, but costs O(n log n). One pass tracking min, max and sum is O(n).

---

### E5 · Find Lucky Integer in an Array

**🔗 [LC 1394 — Find Lucky Integer in an Array](https://leetcode.com/problems/find-lucky-integer-in-an-array/)** · Easy
**Pattern:** Counting vs nested loops | **Companies:** Amazon

**Hint:** Counting each value by rescanning the list is O(n²). Values are at most 500 — a tally list of size 501 makes it O(n).

---

### E6 · Maximum Product of Three Numbers

**🔗 [LC 628 — Maximum Product of Three Numbers](https://leetcode.com/problems/maximum-product-of-three-numbers/)** · Easy
**Pattern:** Sort vs single pass | **Companies:** Amazon, Google

**Hint:** Sorting makes the answer easy to see: O(n log n). The three largest and two smallest can also be tracked in one O(n) pass.

---

### E7 · Count of Matches in Tournament

**🔗 [LC 1688 — Count of Matches in Tournament](https://leetcode.com/problems/count-of-matches-in-tournament/)** · Easy
**Pattern:** Simulation → formula | **Companies:** Amazon, Google

**Hint:** Simulating the rounds is O(log n). Each match eliminates exactly one team — how many teams must be eliminated?

---

### E8 · Count Operations to Obtain Zero

**🔗 [LC 2169 — Count Operations to Obtain Zero](https://leetcode.com/problems/count-operations-to-obtain-zero/)** · Easy
**Pattern:** Repeated subtraction → division | **Companies:** Amazon

**Hint:** Subtracting one at a time can take a billion steps. Division does many subtractions at once: O(log n).

---

### E9 · XOR Operation in an Array

**🔗 [LC 1486 — XOR Operation in an Array](https://leetcode.com/problems/xor-operation-in-an-array/)** · Easy
**Pattern:** Loop vs pattern | **Companies:** Amazon

**Hint:** The loop is O(n) and completely fine here. Write out the first few XORs by hand and notice how few operations each step really needs.

---

### E10 · Largest Positive Integer That Exists With Its Negative

**🔗 [LC 2441 — Largest Positive Integer That Exists With Its Negative](https://leetcode.com/problems/largest-positive-integer-that-exists-with-its-negative/)** · Easy
**Pattern:** Pairs vs lookup | **Companies:** Amazon, Google

**Hint:** Checking every pair is O(n²). If you could ask "is −x in the list?" instantly, it would be O(n) — that is what a hash set does (Lecture 16).

---

### E11 · Largest Number At Least Twice of Others

**🔗 [LC 747 — Largest Number At Least Twice of Others](https://leetcode.com/problems/largest-number-at-least-twice-of-others/)** · Easy
**Pattern:** Single pass, two trackers | **Companies:** Google

**Hint:** Track the largest and second largest in one pass: O(n), O(1) space. Sorting would work too, at O(n log n).

---

### E12 · Self Dividing Numbers

**🔗 [LC 728 — Self Dividing Numbers](https://leetcode.com/problems/self-dividing-numbers/)** · Easy
**Pattern:** Range × digits | **Companies:** Amazon

**Hint:** For each number in [left, right], check each digit: O(range · digits). Count exactly how many steps for left=1, right=10,000.

---

### E13 · Ugly Number

**🔗 [LC 263 — Ugly Number](https://leetcode.com/problems/ugly-number/)** · Easy
**Pattern:** Dividing loop | **Companies:** Amazon, Google

**Hint:** Keep dividing by 2, 3 and 5. Each division at least halves n, so the loop runs O(log n) times.

---

### E14 · Minimum Number of Moves to Seat Everyone

**🔗 [LC 2037 — Minimum Number of Moves to Seat Everyone](https://leetcode.com/problems/minimum-number-of-moves-to-seat-everyone/)** · Easy
**Pattern:** Sort, then pair | **Companies:** Amazon

**Hint:** Sort both lists and pair them in order: O(n log n). Say why sorting is the expensive part.

---

### E15 · Find N Unique Integers Sum up to Zero

**🔗 [LC 1304 — Find N Unique Integers Sum up to Zero](https://leetcode.com/problems/find-n-unique-integers-sum-up-to-zero/)** · Easy
**Pattern:** Construct directly | **Companies:** Amazon, Google

**Hint:** No searching at all — write the numbers down in pairs x and −x. O(n) is the best possible, because you must output n numbers.

---

## 🟡 Medium Tier (5 Problems)

_Here the obvious solution is too slow for the constraint. Find the work that repeats, and say what the faster version would cost. The techniques get their own lectures later; spotting the need for them is the skill._

### M1 · Sum of Absolute Differences in a Sorted Array

**🔗 [LC 1685 — Sum of Absolute Differences in a Sorted Array](https://leetcode.com/problems/sum-of-absolute-differences-in-a-sorted-array/)** · Medium
**Pattern:** Remove repeated work | **Companies:** Amazon, Google

**Hint:** Every pair is O(n²) — with n up to 100,000, that is too slow. Keep running totals of the left and right sides instead: O(n).

---

### M2 · K Radius Subarray Averages

**🔗 [LC 2090 — K Radius Subarray Averages](https://leetcode.com/problems/k-radius-subarray-averages/)** · Medium
**Pattern:** Recomputed windows | **Companies:** Amazon, Google

**Hint:** Recomputing each window from scratch is O(n · k). Each window shares all but two numbers with the last one — reuse the sum.

---

### M3 · Count Number of Homogenous Substrings

**🔗 [LC 1759 — Count Number of Homogenous Substrings](https://leetcode.com/problems/count-number-of-homogenous-substrings/)** · Medium
**Pattern:** Count runs, not substrings | **Companies:** Amazon, Google

**Hint:** Listing every substring is O(n²). A run of L equal characters contains L·(L+1)÷2 homogenous substrings — count runs in O(n).

---

### M4 · Strictly Palindromic Number

**🔗 [LC 2396 — Strictly Palindromic Number](https://leetcode.com/problems/strictly-palindromic-number/)** · Medium
**Pattern:** Reason before you loop | **Companies:** Google, Amazon

**Hint:** Before converting to every base, write n in base n − 2 by hand for n = 5, 6, 7. What do you see?

---

### M5 · Minimized Maximum of Products Distributed to Any Store

**🔗 [LC 2064 — Minimized Maximum of Products Distributed to Any Store](https://leetcode.com/problems/minimized-maximum-of-products-distributed-to-any-store/)** · Medium
**Pattern:** Search over the answer | **Companies:** Amazon, Google

**Hint:** Try every possible maximum: too slow. The answer is between 1 and max(quantities) — halve that range each time: O(n log max). (Taught fully in Lecture 13.)

---

## 🔴 Hard Tier (0 Problems)

_No Hard problems here — this lecture is about reading cost, and the Easy and Medium tiers already stretch that skill._

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1
for i from 0 to n - 1:
    print(i)
for j from 0 to n - 1:
    print(j)

// Snippet 2
for i from 0 to n - 1:
    for j from 0 to n - 1:
        print(i, j)

// Snippet 3
for i from 0 to n - 1:
    for j from i + 1 to n - 1:
        print(i, j)

// Snippet 4
i ← 1
while i < n:
    i ← i × 2

// Snippet 5
i ← 0
while i < n:
    i ← i + 2

// Snippet 6
for i from 0 to n - 1:
    for j from 0 to m - 1:
        print(i, j)

// Snippet 7
for i from 0 to n - 1:
    for c from 'a' to 'z':
        print(c)

// Snippet 8
function f(n):
    if n ≤ 1: return 1
    return f(n - 1) + f(n - 1)

// Snippet 9
sort(a)                               // a has n items
for i from 0 to n - 1:
    print(a[i])

// Snippet 10
i ← n
while i > 0:
    for j from 0 to i - 1:
        print(j)
    i ← i ÷ 2
```

**Complexity Answers:**

1. **O(n)** time, O(1) space — two separate loops add: n + n = 2n.
2. **O(n²)** time — nested loops multiply.
3. **O(n²)** time — the inner loop is about half as long on average, but half of n² is still n² growth.
4. **O(log n)** time — doubling i reaches n after about log₂ n steps.
5. **O(n)** time — adding 2 each step means n ÷ 2 steps, which is still linear.
6. **O(n · m)** time — two different inputs keep two different letters.
7. **O(n)** time — the inner loop always runs 26 times, a constant.
8. **O(2ⁿ)** time, **O(n)** space — two calls per level, n levels deep.
9. **O(n log n)** time — the sort dominates; the O(n) pass after it is the smaller term.
10. **O(n)** time — the inner loop runs n + n/2 + n/4 + … which adds up to at most 2n.

---

## 🔍 Self-Assessment — True / False

1. Big-O measures how many seconds a program takes. → **False** — it measures how the number of steps grows with the input
2. O(2n) and O(n) describe the same growth. → **True** — constant multipliers are dropped
3. A loop that runs from i + 1 to n inside another loop is O(n log n). → **False** — it is still O(n²) — about half of n²
4. Sorting is free if you only do it once. → **False** — one sort is O(n log n), which is often the most expensive step
5. A recursive function that creates no lists uses O(1) space. → **False** — each unfinished call is held in memory, so depth counts
6. Adding to a growable list is O(1) every single time. → **False** — it is O(1) amortised; the occasional resize is O(n)
7. With n ≤ 100,000, an O(n²) solution is usually too slow. → **True** — 10¹⁰ steps is about 100 seconds at 10⁸ per second
8. O(log n) grows faster than O(n). → **False** — log n grows far slower — 20 for a million, versus a million

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Why not seconds?**: Explain why computer scientists count steps rather than time a program with a stopwatch.
2. **The ladder**: List the seven common Big-O classes from fastest to slowest and give one everyday example of each.
3. **Halving**: Explain in your own words why halving something repeatedly takes only about 20 steps to get from a million down to one.
4. **Two inputs**: A function loops over a list of n names and, inside, over a list of m emails. What is its Big-O, and why is O(n²) wrong?
5. **Space**: What is the difference between the space an algorithm needs in total and its _auxiliary_ space? Which one do interviewers usually mean?
6. **Amortised**: Explain amortised O(1) to a friend using the growing-list (or moving-house) example.
7. **Constraints**: A problem says n ≤ 20. Another says n ≤ 1,000,000. What does each tell you about the solution before you read anything else?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon** | [Count Operations to Obtain Zero](https://leetcode.com/problems/count-operations-to-obtain-zero/), [Find Lucky Integer in an Array](https://leetcode.com/problems/find-lucky-integer-in-an-array/), [Find Numbers with Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/), [Minimum Number of Moves to Seat Everyone](https://leetcode.com/problems/minimum-number-of-moves-to-seat-everyone/)                                 |
| **Google** | [Largest Number At Least Twice of Others](https://leetcode.com/problems/largest-number-at-least-twice-of-others/), [Count Number of Homogenous Substrings](https://leetcode.com/problems/count-number-of-homogenous-substrings/), [K Radius Subarray Averages](https://leetcode.com/problems/k-radius-subarray-averages/), [Minimized Maximum of Products Distributed to Any Store](https://leetcode.com/problems/minimized-maximum-of-products-distributed-to-any-store/) |

---

## ✅ Completion Checklist

- [ ] All 15 Easy problems solved
- [ ] All 5 Medium problems solved
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 7 conceptual questions answered out loud
- [ ] I can find the Big-O of any loop structure in this assignment without help
- [ ] I can name the target complexity from a constraint in under ten seconds
- [ ] I have come back after Lecture 4 and coded at least the Easy tier

---

**← [Study Plan](../README.md)** &nbsp;·&nbsp; **[Lecture 2 · Attacking an Unseen Problem](../Lecture2/Assignment.md) →**
