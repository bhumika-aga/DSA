# 🪵 Assignment 38 — Square Root Decomposition & Mo’s Algorithm

> **Lecture:** 38 of 45 — Square Root Decomposition & Mo’s Algorithm
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 3 days · **Total Problems:** 12 (2 Easy · 6 Medium · 4 Hard)
> **Goal:** Split into blocks when a tree is too much, and answer batches of range queries in an order that reuses work.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                                    | Pattern              | Move                                        |
| ------------------------------------------------------------------------ | -------------------- | ------------------------------------------- |
| Updates and range queries, and a tree feels like too much                | Square root blocks   | Block summaries; O(√n) per query            |
| Many range queries, all known up front, answers do not split into halves | Mo’s algorithm       | Sort by (l ÷ √n, r); slide a window         |
| Adding or removing one element changes the answer by a simple amount     | Add/remove primitive | Keep counts; update the answer in O(1)      |
| Values lie in a small range                                              | Counting buckets     | Scan the buckets instead of sorting         |
| A few values appear very often, most rarely                              | Heavy/light split    | Precompute for heavy, brute force for light |
| Queries can be answered in any order                                     | Offline processing   | Sort queries; remember original positions   |

---

## 🟢 Easy Tier (2 Problems)

_Small inputs. Solve them directly, but notice which running summary you keep as the window or subarray grows._

### E1 · Subarrays Distinct Element Sum of Squares I

**🔗 [LC 2913 — Subarrays Distinct Element Sum of Squares I](https://leetcode.com/problems/subarrays-distinct-element-sum-of-squares-i/)** · Easy
**Pattern:** Every subarray with a running set | **Companies:** Amazon, Google

**Hint:** n ≤ 100: for each start, extend the end and grow a set of values. The distinct count after each step is the set size; add its square.

---

### E2 · Find X-Sum of All K-Long Subarrays I

**🔗 [LC 3318 — Find X-Sum of All K-Long Subarrays I](https://leetcode.com/problems/find-x-sum-of-all-k-long-subarrays-i/)** · Easy
**Pattern:** Window with a frequency count | **Companies:** Amazon, Google

**Hint:** n ≤ 50, so recount each window: count frequencies, sort by (count, value) descending, and sum the top x values times their counts.

---

## 🟡 Medium Tier (6 Problems)

_Windows and offline queries. Each one is solved by keeping a count table up to date as elements enter and leave._

### M1 · Sliding Subarray Beauty

**🔗 [LC 2653 — Sliding Subarray Beauty](https://leetcode.com/problems/sliding-subarray-beauty/)** · Medium
**Pattern:** Counting buckets | **Companies:** Amazon, Google

**Hint:** Values lie in [−50, 50]. Keep 50 counters for the negatives; the x-th smallest is found by walking them from −50 upwards.

---

### M2 · Count Complete Subarrays in an Array

**🔗 [LC 2799 — Count Complete Subarrays in an Array](https://leetcode.com/problems/count-complete-subarrays-in-an-array/)** · Medium
**Pattern:** Distinct-count window | **Companies:** Amazon, Google

**Hint:** Let D be the number of distinct values in the whole array. For each right end, shrink the left while the window still has D distinct values; every start before the left end works.

---

### M3 · Continuous Subarrays

**🔗 [LC 2762 — Continuous Subarrays](https://leetcode.com/problems/continuous-subarrays/)** · Medium
**Pattern:** Window with min and max | **Companies:** Amazon, Google

**Hint:** A window is valid while max − min ≤ 2. Keep a sorted multiset (or two monotonic deques) of the window; each right end adds (right − left + 1) subarrays.

---

### M4 · Count Zero Request Servers

**🔗 [LC 2747 — Count Zero Request Servers](https://leetcode.com/problems/count-zero-request-servers/)** · Medium
**Pattern:** Offline queries, sorted by time | **Companies:** Amazon, Google

**Hint:** Sort logs and queries by time. Both window ends only move forward; keep a count of servers with at least one request.

---

### M5 · Count the Number of Good Subarrays

**🔗 [LC 2537 — Count the Number of Good Subarrays](https://leetcode.com/problems/count-the-number-of-good-subarrays/)** · Medium
**Pattern:** Add/remove with a pair count | **Companies:** Amazon, Google

**Hint:** Adding a value that already appears c times creates c new equal pairs. Shrink from the left while the window has at least k pairs.

---

### M6 · K Divisible Elements Subarrays

**🔗 [LC 2261 — K Divisible Elements Subarrays](https://leetcode.com/problems/k-divisible-elements-subarrays/)** · Medium
**Pattern:** Every subarray, deduplicated | **Companies:** Amazon, Google

**Hint:** n ≤ 200: generate each subarray while counting elements divisible by p, stop at k + 1, and put each subarray (as a string or a trie path) into a set.

---

## 🔴 Hard Tier (4 Problems)

_The four big ideas at full strength: heavy/light, Mo’s algorithm with frequency buckets, two ordered sets in a window, and binary search on the answer._

### H1 · Online Majority Element In Subarray

**🔗 [LC 1157 — Online Majority Element In Subarray](https://leetcode.com/problems/online-majority-element-in-subarray/)** · Hard
**Pattern:** Heavy/light split | **Companies:** Google, Amazon

**Hint:** A range longer than √n needs more than √n/2 copies of its majority, so only values appearing more than √n/2 times overall can win — at most 2√n of them. Give each a prefix-count array; for ranges up to √n, a Boyer-Moore pass.

---

### H2 · Threshold Majority Queries

**🔗 [LC 3636 — Threshold Majority Queries](https://leetcode.com/problems/threshold-majority-queries/)** · Hard
**Pattern:** Mo’s algorithm with frequency buckets | **Companies:** Google, Amazon

**Hint:** Answer the queries offline in Mo’s order. Keep count[v] and, for each frequency f, the values that currently have it; the answer is the smallest value in the highest frequency, if that frequency reaches the threshold.

---

### H3 · Find X-Sum of All K-Long Subarrays II

**🔗 [LC 3321 — Find X-Sum of All K-Long Subarrays II](https://leetcode.com/problems/find-x-sum-of-all-k-long-subarrays-ii/)** · Hard
**Pattern:** Window with two ordered sets | **Companies:** Google, Amazon

**Hint:** Split the window’s distinct values into the top x (by count, then value) and the rest, each kept in an ordered set, plus the running sum of the top group. Moving the window changes one count; rebalance the two sets.

---

### H4 · Find the Median of the Uniqueness Array

**🔗 [LC 3134 — Find the Median of the Uniqueness Array](https://leetcode.com/problems/find-the-median-of-the-uniqueness-array/)** · Hard
**Pattern:** Binary search on the answer + window | **Companies:** Google, Amazon

**Hint:** The uniqueness array has n(n+1)/2 entries. Binary search for the smallest m such that at least half of all subarrays have at most m distinct values; count those with a sliding window.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — build square root blocks over n items

// Snippet 2 — one range-sum query with blocks of size √n

// Snippet 3 — one point update with blocks

// Snippet 4 — Mo's algorithm: n items, q queries

// Snippet 5 — answering q range-distinct queries by scanning each range

// Snippet 6 — heavy/light: prefix counts for every value appearing more than √n times
```

**Complexity Answers:**

1. **O(n)**.
2. **O(√n)** — at most two ragged ends of √n plus √n whole blocks.
3. **O(1)** — the item and its block total.
4. **O((n + q)√n)**, plus O(q log q) to sort the queries.
5. **O(n · q)**.
6. **O(n√n)** — at most √n heavy values, each with an array of n + 1 counts.

---

## 🔍 Self-Assessment — True / False

1. Square root decomposition is faster than a segment tree. → **False** — O(√n) against O(log n); its advantage is simplicity
2. Mo’s algorithm needs every query before it answers any of them. → **True** — it reorders them; that is what "offline" means
3. At most √n values can each appear more than √n times in an array of n items. → **True** — otherwise they would need more than n items
4. The best block size is always exactly 100. → **False** — about √n, from balancing the whole-block and ragged-end costs
5. Mo’s algorithm returns its answers in the order the queries were given. → **False** — you must store each answer at its original index
6. Counting buckets beat sorting when values lie in a small range. → **True** — scanning 101 buckets is constant work

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Balancing**: Show why a block size of about √n minimises n ÷ B + 2B.
2. **Heavy values**: Why can at most √n different values appear more than √n times each?
3. **Mo’s order**: Explain why sorting queries by the block of their left end, then by their right end, bounds the total pointer movement.
4. **Offline**: What makes a set of queries "offline", and give an example where Mo’s algorithm cannot be used.
5. **Frequency of frequencies**: How does a second count table let you track the most frequent value as elements are removed?
6. **Choosing**: When would you pick square root blocks over a Fenwick tree, and when not?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon** | [Find X-Sum of All K-Long Subarrays II](https://leetcode.com/problems/find-x-sum-of-all-k-long-subarrays-ii/), [Find the Median of the Uniqueness Array](https://leetcode.com/problems/find-the-median-of-the-uniqueness-array/), [Online Majority Element In Subarray](https://leetcode.com/problems/online-majority-element-in-subarray/), [Threshold Majority Queries](https://leetcode.com/problems/threshold-majority-queries/) |
| **Google** | [Continuous Subarrays](https://leetcode.com/problems/continuous-subarrays/), [Count Complete Subarrays in an Array](https://leetcode.com/problems/count-complete-subarrays-in-an-array/), [Count Zero Request Servers](https://leetcode.com/problems/count-zero-request-servers/), [Count the Number of Good Subarrays](https://leetcode.com/problems/count-the-number-of-good-subarrays/)                                           |

---

## ✅ Completion Checklist

- [ ] Both Easy problems solved
- [ ] All 6 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name which of the six ideas each problem uses before solving it
- [ ] I solved at least one problem with Mo’s algorithm from scratch

---

**← [Lecture 37 · Segment Trees & Fenwick Trees](../Lecture37/Assignment.md)** &nbsp;·&nbsp; **[Lecture 39 · String Algorithms (KMP, Z, Rabin-Karp, Manacher)](../Lecture39/Assignment.md) →**
