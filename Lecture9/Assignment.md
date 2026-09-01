# ⚖️ Assignment 09 — Sorting & Cyclic Patterns

> **Lecture:** Topic 9 — Sorting Algorithms
> **Topic Count:** 9 of 30 — Phase 2 Core Data Structures
> **Duration:** 4 Days
> **Core Problems:** 25 (10 Easy · 10 Medium · 5 Hard) + 4 Complexity Exercises
> **Goal:** Master core comparison sorts ($O (N^2)$ to $O (N \log N)$), non-comparison sorting ($O (N)$), partitioning
> paradigms, and the **Cyclic Sort** invariant for range-limited domains.

---

## 🟢 Easy Tier (Warm-up & Mechanics)

_Focus on implementing pure logic, counting swaps, and in-place sorting._

1. **Bubble Sort Implementation** — Optimized with `swapped` flag. `[Pattern: Basic]`  
   **🔗 [LC 912](https://leetcode.com/problems/sort-an-array/)** · **Companies:** Amazon, Adobe
2. **Selection Sort Implementation** — Find and swap min elements. `[Pattern: Basic]`  
   **🔗 [LC 912](https://leetcode.com/problems/sort-an-array/)** · **Companies:** Amazon, Adobe
3. **Insertion Sort Implementation** — Adaptive sorting for $N < 64$. `[Pattern: Basic]`  
   **🔗 [LC 912](https://leetcode.com/problems/sort-an-array/)** · **Companies:** Amazon, Adobe
4. **[Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) (LC 88)** — Merge two arrays from the back.
   `[Companies: Amazon, Microsoft, Meta]`
5. **[Missing Number](https://leetcode.com/problems/missing-number/) (LC 268)** — Solve using **Cyclic Sort** only.

**Companies:** Amazon, Google, Microsoft
`[Pattern: Cyclic] [LC Easy]` 6. **[Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/) (LC 448)** — All missing.

**Companies:** Amazon, Google, Apple
`[Pattern: Cyclic] [LC Easy]` 7. **[Set Mismatch](https://leetcode.com/problems/set-mismatch/) (LC 645)** — Duplicate + Missing.

**Companies:** Amazon, Google
`[Pattern: Cyclic] [LC Easy]` 8. **[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) (LC 217)** — Solve with $O (N \log N)$ sort

**Companies:** Amazon, Google, Apple
first. `[LC Easy]` 9. **[Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/) (LC 977)** — Two pointers or

**Companies:** Amazon, Meta, Google
sort? `[LC Easy]` 10. **[Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/) (LC 905)** — Fundamental partitioning.

**Companies:** Amazon, Google
`[LC Easy]`

---

## 🟡 Medium Tier (Standard & Divide-and-Conquer)

_Focus on complexity, stable merging, and randomized pivoting._

1. **[Sort Colors](https://leetcode.com/problems/sort-colors/) (LC 75)** — **Dutch National Flag** (3-way partition).

**Companies:** Microsoft, Amazon, Meta
`[Pattern: Two Pointers] [LC Medium]` 2. **[Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) (LC 287)** — Solve via Cyclic

**Companies:** Amazon, Google, Meta, Microsoft
Sort. `[Pattern: Cyclic] [LC Medium]` 3. **[Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/) (LC 442)** — Use

**Companies:** Amazon, Google, Meta
the Negative Marking trick. `[Pattern: Cyclic] [LC Medium]` 4. **[Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) (LC 215)** —

**Companies:** Meta, Amazon, Google, Microsoft
Solve using **QuickSelect** ($O (N)$ Avg). `[Pattern: Partitioning] [LC Medium]` 5. **[Largest Number](https://leetcode.com/problems/largest-number/) (LC 179)** — Custom comparator logic for combined

**Companies:** Google, Amazon, Microsoft
strings. `[Companies: Google, Amazon, Microsoft]` 6. **[Merge Intervals](https://leetcode.com/problems/merge-intervals/) (LC 56)** — Sort by start time then merge.

**Companies:** Google, Amazon, Meta, Microsoft
`[Pattern: Intervals] [LC Medium]` 7. **[Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) (LC 347)** — **Bucket Sort** or

**Companies:** Amazon, Meta, Google
Priority Queue. `[Pattern: Bucket Sort] [LC Medium]` 8. **[Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/) (LC 280)** — $O (N)$ Greedy local-parity swapping.

**Companies:** Google, Amazon, Meta
`[Pattern: Greedy] [LC Medium]` 9. **[Sort List](https://leetcode.com/problems/sort-list/) (LC 148)** — Merge Sort on Linked Lists.

**Companies:** Amazon, Google, Meta, Microsoft
`[Pattern: D&C] [LC Medium]` 10. **[Custom Sort String](https://leetcode.com/problems/custom-sort-string/) (LC 791)** — Frequency maps as custom

**Companies:** Meta, Amazon, Google
order. `[LC Medium]`

---

## 🔴 Challenge Zone (Mastery)

_Focus on O (1) space constraints and optimal sorting pivots._

1. **[First Missing Positive](https://leetcode.com/problems/first-missing-positive/) (LC 41)** — Ultimate Cyclic Sort
   **Companies:** Google, Amazon, Meta, Microsoft
   challenge. `[Pattern: Cyclic] [LC Hard]`

2. **[Maximum Gap](https://leetcode.com/problems/maximum-gap/) (LC 164)** — Solve in $O (N)$ using \*\*Bucket/Radix
   **Companies:** Apple, Amazon, Google
   Sort\*\*. `[LC Hard]`

3. **[Reverse Pairs](https://leetcode.com/problems/reverse-pairs/) (LC 493)\*\* — Merge Sort "Modification" to count
   **Companies:\*\* Google, Amazon, Meta
   pairs. `[Pattern: D&C] [LC Hard]`

4. **[Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) (LC 315)** — Merge Sort or BIT? `[LC Hard]` `[Companies: Google, Amazon, Meta]`

5. **[Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/) (LC 373)** —
   **Companies:** Google, Amazon, Meta
   Sorting vs Multi-pointer. `[LC Hard]`

---

## 📊 Complexity Analysis Exercises

Complete the table based on the best/worst cases:

| Snippet          | Best Case     | Worst Case    | Space       | Stability |
| :--------------- | :------------ | :------------ | :---------- | :-------- |
| `Selection Sort` | $O(N^2)$      | ??            | $O(1)$      | No        |
| `Merge Sort`     | ??            | $O(N \log N)$ | $O(N)$      | Yes       |
| `Quick Sort`     | $O(N \log N)$ | $O(N^2)$      | $O(\log N)$ | No        |
| `Counting Sort`  | $O(N+K)$      | ??            | $O(K)$      | Yes       |
| `Cyclic Sort`    | $O(N)$        | $O(N)$        | $O(1)$      | No        |

---

## 🧠 Conceptual Check

1. **Stability**: Why is Merge Sort stable while standard Quick Sort is not?
2. **In-place**: Can Merge Sort be implemented in $O (1)$ extra space? (Research "In-place Merge Sort").
3. **Pivots**: How does randomized pivoting prevent $O (N^2)$ in Quick Sort?
4. **Comparison**: Why is $O (N \log N)$ the mathematical lower bound for comparison sorts?

---

**Next:** [Topic 10 — Binary Search & Searching Algorithms](../Lecture10/lecture10_notes.html) →
