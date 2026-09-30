# 🔀 Assignment 12 — Sorting Algorithms

> **Lecture:** 12 of 45 — Sorting Algorithms
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 4 days · **Total Problems:** 25 (9 Easy · 12 Medium · 4 Hard)
> **Goal:** Master core comparison sorts (O(n²) to O(n log n)), non-comparison sorting (O(n)), partitioning
> paradigms, and the **Cyclic Sort** invariant for range-limited domains.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                        | Pattern             | Move                                          |
| -------------------------------------------- | ------------------- | --------------------------------------------- |
| "sort" with a small value range              | Counting Sort       | count, then write back in order               |
| "numbers from 1 to n", "missing / duplicate" | Cyclic Sort         | swap each value to index `value - 1`          |
| "kth largest / smallest"                     | QuickSelect         | partition around a pivot, recurse on one side |
| "count pairs where i < j and …"              | Merge Sort Counting | count during the merge step                   |
| "order by a custom rule"                     | Custom Comparator   | define `compare(a, b)` and sort               |
| "overlapping intervals"                      | Sort + Sweep        | sort by start, then merge in one pass         |

---

## 🟢 Easy Tier (9 Problems)

_Focus on implementing pure logic, counting swaps, and in-place sorting._

### E1 · Height Checker

**🔗 [LC 1051 — Height Checker](https://leetcode.com/problems/height-checker/)** · Easy
**Pattern:** Bubble Sort (Implement Yourself) | **Companies:** Amazon, Google

**Hint:** Build `expected` by copying the array and sorting it with your own bubble sort (stop early when a pass makes no swaps). Then count the mismatched positions.

---

### E2 · Find Target Indices After Sorting Array

**🔗 [LC 2089 — Find Target Indices After Sorting Array](https://leetcode.com/problems/find-target-indices-after-sorting-array/)** · Easy
**Pattern:** Selection Sort (Implement Yourself) | **Companies:** Amazon, Google

**Hint:** Sort with your own selection sort, then collect the indices equal to `target`. Follow-up: skip sorting — the answer depends only on how many values are `< target` and `== target`.

---

### E3 · Merge Sorted Array

**🔗 [LC 88 — Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)** · Easy
**Pattern:** Merge from the Back | **Companies:** Amazon, Microsoft, Meta

**Hint:** Fill from the back: pointers `i = m - 1`, `j = n - 1`, `k = m + n - 1`. Write the larger of `nums1[i]` and `nums2[j]` at `k`. Stop when `nums2` is used up — any leftover `nums1` is already in place.

---

### E4 · Rank Transform of an Array

**🔗 [LC 1331 — Rank Transform of an Array](https://leetcode.com/problems/rank-transform-of-an-array/)** · Easy
**Pattern:** Sort + Rank Map | **Companies:** Amazon, Google

**Hint:** Copy and sort the array, assign ranks to distinct values in a map (rank increases only on a new value), then map every original element to its rank.

---

### E5 · Find All Numbers Disappeared in an Array

**🔗 [LC 448 — Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)** · Easy
**Pattern:** Cyclic | **Companies:** Amazon, Google, Apple

**Hint:** Cyclic sort: swap each value `v` into index `v - 1` until the spot already holds `v`. Then every index `i` with `nums[i] != i + 1` means `i + 1` is missing. (Negative marking also works in O(1) space.)

---

### E6 · Set Mismatch

**🔗 [LC 645 — Set Mismatch](https://leetcode.com/problems/set-mismatch/)** · Easy
**Pattern:** Cyclic | **Companies:** Amazon, Google

**Hint:** Cyclic sort the array. The index `i` with `nums[i] != i + 1` gives both answers: `nums[i]` is the duplicate and `i + 1` is the missing number.

---

### E7 · Can Make Arithmetic Progression From Sequence

**🔗 [LC 1502 — Can Make Arithmetic Progression From Sequence](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/)** · Easy
**Pattern:** Sort Then Verify | **Companies:** Amazon, Google

**Hint:** Sort, then check every adjacent difference equals `arr[1] - arr[0]`. O(n) follow-up: min, max and a set — the step must be `(max - min) / (n - 1)`.

---

### E8 · Relative Sort Array

**🔗 [LC 1122 — Relative Sort Array](https://leetcode.com/problems/relative-sort-array/)** · Easy
**Pattern:** Counting Sort | **Companies:** Amazon, Google, Meta

**Hint:** Values are ≤ 1000, so count them in `int[1001]`. Emit the values in `arr2`'s order first, then the leftovers in ascending order. O(n + range).

---

### E9 · Sort Array By Parity

**🔗 [LC 905 — Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)** · Easy
**Pattern:** Two-Pointer Partition | **Companies:** Amazon, Google

**Hint:** Two pointers: `lo` from the start, `hi` from the end. If `nums[lo]` is odd, swap it with `nums[hi]` and move `hi` left; otherwise move `lo` right. It's the two-way partition from quicksort.

---

## 🟡 Medium Tier (12 Problems)

_Focus on complexity, stable merging, and randomized pivoting._

### M1 · Insertion Sort List

**🔗 [LC 147 — Insertion Sort List](https://leetcode.com/problems/insertion-sort-list/)** · Medium
**Pattern:** Insertion Sort | **Companies:** Microsoft, Amazon

**Hint:** Build a sorted list behind a dummy head. For each node, walk from the dummy to find its insertion point and splice it in. The same insertion idea as on arrays, but without shifting.

---

### M2 · Sort Colors

**🔗 [LC 75 — Sort Colors](https://leetcode.com/problems/sort-colors/)** · Medium
**Pattern:** Two Pointers | **Companies:** Microsoft, Amazon, Meta

**Hint:** Dutch National Flag with three pointers `lo`, `mid`, `hi`: a 0 swaps with `lo` (advance both), a 1 just advances `mid`, and a 2 swaps with `hi` (move `hi` left but don't advance `mid` — the swapped-in value is unchecked). One pass.

---

### M3 · Find the Duplicate Number

**🔗 [LC 287 — Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)** · Medium
**Pattern:** Cyclic | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Cyclic sort idea: values are 1..n in n + 1 slots, so place each value at its index; the value that finds its index already occupied is the duplicate. With the read-only constraint, treat `i → nums[i]` as a linked list and use Floyd's cycle entry instead.

---

### M4 · Find All Duplicates in an Array

**🔗 [LC 442 — Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)** · Medium
**Pattern:** Cyclic | **Companies:** Amazon, Google, Meta

**Hint:** Negative marking: for each `v`, look at index `|v| - 1`. If it's already negative, `|v|` is a duplicate; otherwise negate it. O(n) time, O(1) extra space.

---

### M5 · Find the Kth Largest Integer in the Array

**🔗 [LC 1985 — Find the Kth Largest Integer in the Array](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/)** · Medium
**Pattern:** QuickSelect with a Custom Comparator | **Companies:** Amazon, Google

**Hint:** The numbers are strings with up to 100 digits: compare by length first, then lexicographically. Then QuickSelect (random pivot) for the kth largest, or a size-k min-heap.

---

### M6 · Largest Number

**🔗 [LC 179 — Largest Number](https://leetcode.com/problems/largest-number/)** · Medium
**Pattern:** Custom Comparator | **Companies:** Google, Amazon, Microsoft

**Hint:** Sort the numbers as strings with the comparator `(a, b) -> (b + a).compareTo(a + b)`, so `a` goes first when `a + b` is the bigger string. Join them. If the first string is "0", the answer is "0".

---

### M7 · Merge Intervals

**🔗 [LC 56 — Merge Intervals](https://leetcode.com/problems/merge-intervals/)** · Medium
**Pattern:** Intervals | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Sort by start. Keep the last merged interval; if the next start is ≤ its end, extend the end to `max(end, next end)`, otherwise start a new interval. O(n log n).

---

### M8 · Maximum Element After Decreasing and Rearranging

**🔗 [LC 1846 — Maximum Element After Decreasing and Rearranging](https://leetcode.com/problems/maximum-element-after-decreasing-and-rearranging/)** · Medium
**Pattern:** Sort + Greedy | **Companies:** Amazon

**Hint:** Sort, set `arr[0] = 1`, then clamp each element to `min(arr[i], arr[i-1] + 1)`. The last element is the answer. A counting sort on `min(value, n)` makes it O(n).

---

### M9 · Wiggle Sort II

**🔗 [LC 324 — Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/)** · Medium
**Pattern:** Partitioning | **Companies:** Google, Amazon, Meta

**Hint:** Sort, then interleave the two halves from the back (O(N log N)); follow-up: QuickSelect the median + 3-way partition for O(N).

---

### M10 · Sort the Matrix Diagonally

**🔗 [LC 1329 — Sort the Matrix Diagonally](https://leetcode.com/problems/sort-the-matrix-diagonally/)** · Medium
**Pattern:** Sort Each Diagonal | **Companies:** Amazon, Google

**Hint:** Cells on the same diagonal share `i - j`. Collect each diagonal into a list (or a counting array — values ≤ 100), sort it, and write it back in the same walk order.

---

### M11 · Custom Sort String

**🔗 [LC 791 — Custom Sort String](https://leetcode.com/problems/custom-sort-string/)** · Medium
**Pattern:** Custom Order / Counting | **Companies:** Meta, Amazon, Google

**Hint:** Count every character of `s`, emit characters in `order`'s order as many times as they appear, then append whatever is left. That's counting sort with a custom key order: O(n + 26).

---

### M12 · Maximum Gap

**🔗 [LC 164 — Maximum Gap](https://leetcode.com/problems/maximum-gap/)** · Medium
**Pattern:** Bucket Sort (Pigeonhole) | **Companies:** Apple, Amazon, Google

**Hint:** Pigeonhole: with `n` numbers between `min` and `max`, the max gap is at least `ceil((max - min) / (n - 1))`. Use buckets of that width, store only each bucket's min and max, and scan the gaps between non-empty buckets. O(n).

---

## 🔴 Hard Tier (4 Problems)

_Focus on O(1) space constraints and optimal sorting pivots._

### H1 · First Missing Positive

**🔗 [LC 41 — First Missing Positive](https://leetcode.com/problems/first-missing-positive/)** · Hard
**Pattern:** Cyclic | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Cyclic sort values `1..n` into index `value - 1`, ignoring values that are out of range or would swap with an equal value. The first index `i` with `nums[i] != i + 1` gives the answer `i + 1`; if there is none, it's `n + 1`.

---

### H2 · Reverse Pairs

**🔗 [LC 493 — Reverse Pairs](https://leetcode.com/problems/reverse-pairs/)** · Hard
**Pattern:** D&C | **Companies:** Google, Amazon, Meta

**Hint:** Modify merge sort: before merging two sorted halves, count pairs with a second pointer — for each `i` in the left half, advance `j` in the right half while `nums[i] > 2 * nums[j]` (use `long`). Then merge as usual.

---

### H3 · Count of Smaller Numbers After Self

**🔗 [LC 315 — Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)** · Hard
**Pattern:** Merge Sort Counting | **Companies:** Google, Amazon, Meta

**Hint:** Merge sort on indices. While merging, when you take an element from the left half, every right-half element already placed was smaller and came after it — add that count to the element's answer. Or use a Fenwick tree over compressed values.

---

### H4 · Count of Range Sum

**🔗 [LC 327 — Count of Range Sum](https://leetcode.com/problems/count-of-range-sum/)** · Hard
**Pattern:** Merge Sort Counting | **Companies:** Google, Amazon

**Hint:** Work on prefix sums. During merge sort, for each left-half prefix `p`, move two pointers over the sorted right half to count prefixes in `[p + lower, p + upper]`, then merge. O(n log n). Use `long`.

---

## 📊 Complexity Analysis Exercises

Complete the table based on the best/worst cases:

| Snippet          | Best Case  | Worst Case | Space    | Stability |
| :--------------- | :--------- | :--------- | :------- | :-------- |
| `Selection Sort` | O(n²)      | ??         | O(1)     | No        |
| `Merge Sort`     | ??         | O(n log n) | O(n)     | Yes       |
| `Quick Sort`     | O(n log n) | O(n²)      | O(log n) | No        |
| `Counting Sort`  | O(n + k)   | ??         | O(k)     | Yes       |
| `Cyclic Sort`    | O(n)       | O(n)       | O(1)     | No        |

---

## 🔍 Self-Assessment — True / False

1. Quick sort is always faster than merge sort. → **False** — its worst case is O(n²); merge sort is O(n log n) always
2. A stable sort keeps equal elements in their original order. → **True** — that is the definition
3. Any comparison sort needs at least on the order of n log n comparisons in the worst case. → **True** — there are n! orderings, and each comparison halves the possibilities at best
4. Counting sort beats n log n for any input. → **False** — only when values lie in a small known range
5. Insertion sort is O(n) on already-sorted input. → **True** — each element compares once with its left neighbour and stops
6. Java's Arrays.sort on an int[] is stable. → **False** — it uses quicksort for primitives; stability only matters — and is only guaranteed — for objects

---

## 🧠 Conceptual Check

1. **Stability**: Why is Merge Sort stable while standard Quick Sort is not?
2. **In-place**: Can Merge Sort be implemented in O(1) extra space? (Research "In-place Merge Sort").
3. **Pivots**: How does randomized pivoting prevent O(n²) in Quick Sort?
4. **Comparison**: Why is O(n log n) the mathematical lower bound for comparison sorts?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Maximum Element After Decreasing and Rearranging](https://leetcode.com/problems/maximum-element-after-decreasing-and-rearranging/), [Count of Range Sum](https://leetcode.com/problems/count-of-range-sum/), [Find the Kth Largest Integer in the Array](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/), [Sort the Matrix Diagonally](https://leetcode.com/problems/sort-the-matrix-diagonally/) |
| **Google**    | [Can Make Arithmetic Progression From Sequence](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/), [Find Target Indices After Sorting Array](https://leetcode.com/problems/find-target-indices-after-sorting-array/), [Height Checker](https://leetcode.com/problems/height-checker/), [Rank Transform of an Array](https://leetcode.com/problems/rank-transform-of-an-array/)                   |
| **Meta**      | [Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/), [Reverse Pairs](https://leetcode.com/problems/reverse-pairs/), [Custom Sort String](https://leetcode.com/problems/custom-sort-string/), [Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)                                                                         |
| **Microsoft** | [Insertion Sort List](https://leetcode.com/problems/insertion-sort-list/), [Largest Number](https://leetcode.com/problems/largest-number/), [Sort Colors](https://leetcode.com/problems/sort-colors/), [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)                                                                                                                                               |
| **Apple**     | [Maximum Gap](https://leetcode.com/problems/maximum-gap/), [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)                                                                                                                                                                                                                                               |

---

## ✅ Completion Checklist

- [ ] All 9 Easy problems solved
- [ ] All 12 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Self-assessment completed without looking at the notes
- [ ] Every complexity exercise answered before checking
- [ ] All 4 conceptual questions answered out loud
- [ ] I can state the time, space and stability of every sort in the lecture
- [ ] I can write the Lomuto or Hoare partition from memory

---

**← [Lecture 11 · Arrays & Strings](../Lecture11/Assignment.md)** &nbsp;·&nbsp; **[Lecture 13 · Searching Algorithms](../Lecture13/Assignment.md) →**
