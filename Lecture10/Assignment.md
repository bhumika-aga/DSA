# 🔍 Assignment 10 — Searching Algorithms

> **Lecture:** Topic 10 — Searching Algorithms
> **Topic Count:** 10 of 30 — Phase 2 Core Data Structures
> **Duration:** 5 Days
> **Core Problems:** 28 (8 Easy · 13 Medium · 7 Hard)
> **Goal:** Master unconditional Linear Searching, classic $O(\log N)$ Binary Search templates, **Binary Search on Answer Space** (Monotonic optimization), and matrix traversal boundaries.

---

## 🟢 Easy Tier (Foundations & Templates)

_Focus on loop conditions (`lo <= hi`), non-overflow mid calculation, and understanding $O(1)$ vs $O(\log N)$ search spaces._

1. **[Binary Search](https://leetcode.com/problems/binary-search/) (LC 704)** — Baseline template. `[Basic]`
2. **[Search Insert Position](https://leetcode.com/problems/search-insert-position/) (LC 35)** — Understanding binary boundary behavior. `[LC Easy]`
3. **[Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) (LC 34)** — Building boundary-seeking templates. `[Pattern: Boundary Search]`
4. **[Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/) (LC 374)** — Simple BS in a fixed range. `[LC Easy]`
5. **[Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/) (LC 367)** — Monotonic search on whole numbers. `[LC Easy]`
6. **[Arranging Coins](https://leetcode.com/problems/arranging-coins/) (LC 441)** — Binary Search on integer solutions. `[LC Easy]`
7. **[Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/) (LC 852)** — Simple local maxima search. `[Pattern: Peak]`
8. **Binary Search on Negative Range** — Search a target in an array containing $[-10^9, 10^9]$. `[Basic]`

---

## 🟡 Medium Tier (The Power of Mid & Answer Space)

_Focus on Rotated Arrays, Index Parity, and Monotonic Optimization problems._

1. **[Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) (LC 33)** — Core logic: Checking which side is sorted. `[Pattern: Rotated] [LC Medium]`
2. **[Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/) (LC 81)** — Handling duplicates (Worst case $O(N)$). `[Pattern: Rotated] [LC Medium]`
3. **[Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) (LC 153)** — Finding the pivot. `[Pattern: Index-based] [LC Medium]`
4. **[Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) (LC 74)** — 1D to 2D index mapping: `[mid/col][mid%col]`. `[Pattern: 2D] [LC Medium]`
5. **[Find Peak Element](https://leetcode.com/problems/find-peak-element/) (LC 162)** — Binary search for local maxima in non-sorted data. `[Pattern: Peak] [LC Medium]`
6. **[Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/) (LC 540)** — Using index parity (even/odd pairs). `[Company: Amazon] [LC Medium]`
7. **[Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) (LC 875)** — Gateway into **Binary Search on Answer**. `[Pattern: Search-on-Answer] [LC Medium]`
8. **[Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/) (LC 1011)** — Classic Master-tier Optimization. `[Pattern: Search-on-Answer] [LC Medium]`
9. **[Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/) (LC 1283)** — Monotonic optimization on sums. `[LC Medium]`
10. **[Minimum Number of Days to Make m Bouquets](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/) (LC 1482)** — Range-based search on time. `[LC Medium]`
11. **[Magnetic Force Between Two Balls](https://leetcode.com/problems/magnetic-force-between-two-balls/) (LC 1552)** — Gold standard for Distance Max-Min. `[Company: Google] [LC Medium]`
12. **[Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) (LC 287)** — Binary Search on the value range $[1, N]$. `[Pattern: Discrete Space] [LC Medium]`
13. **[Heaters](https://leetcode.com/problems/heaters/) (LC 475)** — Binary Search + Two Pointers variant. `[LC Medium]`

---

## 🔴 Challenge Zone (Boundary Masters)

_Focus on extremely tight constraints and dual-array partitioning logic._

1. **[Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) (LC 4)** — The hardest partitioning problem. `[Pattern: Dual-Partitioning] [LC Hard]`
2. **[Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/) (LC 410)** — Binary Search on the range $[\max(arr), \sum(arr)]$. `[LC Hard]`
3. **Book Allocation Problem** — Classic interview variation: Allocate $N$ books to $M$ students. `[Pattern: Max-Min]`
4. **[Find K-th Smallest Pair Distance](https://leetcode.com/problems/find-k-th-smallest-pair-distance/) (LC 719)** — Binary Search + Two Pointers. `[LC Hard]`
5. **[Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/) (LC 378)** — BS on value range, not indices. `[Pattern: 2D Value Search] [LC Medium/Hard]`
6. **[Preimage Size of Factorial Zeroes Function](https://leetcode.com/problems/preimage-size-of-factorial-zeroes-function/) (LC 793)** — BS on extremely large ranges. `[LC Hard]`
7. **[Smallest Good Base](https://leetcode.com/problems/smallest-good-base/) (LC 483)** — Searching mathematically derived boundaries. `[LC Hard]`

---

## 📊 Complexity Analysis Exercises

| Search Space           | Conditions      | Complexity                      | Use Case         |
| :--------------------- | :-------------- | :------------------------------ | :--------------- |
| Unsorted Array         | None            | $O(N)$                          | General search   |
| Sorted Array           | Monotonicity    | $O(\log N)$                     | Standard BS      |
| Rotated Array          | Sorted segments | $O(\log N)$                     | Pivot search     |
| Matrix $(M \times N)$  | Row/Col Sorted  | $O(\log(M \times N))$           | 2D Mapping       |
| Integer Range $[1, K]$ | $isValid(mid)$  | $O(\text{check} \times \log K)$ | Search-on-Answer |

---

## 🧠 Conceptual Check

1. **The Invariant**: What property MUST $isValid(mid)$ satisfy to allow Binary Search? (Hint: Monotonicity).
2. **Post-Loop State**: If the target is NOT found, what is the relative position of `lo` and `hi`?
3. **Infinite Loops**: Why is `mid = lo + (hi - lo + 1) / 2` necessary in some variants?
4. **Binary Search on Doubles**: How do you decide the loop condition for decimal ranges? (e.g., while `hi - lo > 1e-9`).

---

**Next:** [Topic 11 — Linked Lists Foundations](../Lecture11/lecture11_notes.html) →
