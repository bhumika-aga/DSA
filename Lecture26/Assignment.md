# 🧾 Assignment 19 — Prefix Sums & Difference Arrays

> **Lecture:** 26 of 45 — Prefix Sums & Difference Arrays
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 4 days · **Total Problems:** 20 (7 Easy · 9 Medium · 4 Hard)
> **Goal:** Pay O(n) once so every range question costs O(1) — and recognise the difference array as the same trick run backwards.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                          | Pattern          | Move                                       |
| ---------------------------------------------- | ---------------- | ------------------------------------------ |
| "sum between index i and j", many queries      | Prefix Sum Array | `P[r+1] - P[l]`, built once                |
| "how many subarrays sum to k"                  | Prefix + HashMap | count earlier prefixes equal to `sum - k`  |
| "add v to every element in [l, r]", many times | Difference Array | `+v` at `l`, `-v` at `r+1`, sweep once     |
| "sum of a sub-rectangle"                       | 2D Prefix Sum    | four corners, inclusion–exclusion          |
| "XOR of a range"                               | Prefix XOR       | `px[r+1] ^ px[l]` — XOR undoes itself      |
| a sliding window that breaks on negatives      | Prefix Sums      | windows need monotonicity; prefixes do not |

---

## 🟢 Easy Tier (7 Problems)

_Build the array, query it, and meet the difference array on small ranges._

### E1 · Left and Right Sum Differences

**🔗 [LC 2574 — Left and Right Sum Differences](https://leetcode.com/problems/left-and-right-sum-differences/)** · Easy
**Pattern:** Prefix + Suffix Sums | **Companies:** Amazon, Google

**Hint:** Build the running sum from the left and from the right (or take the total and subtract). `answer[i] = |leftSum[i] - rightSum[i]|`, with the element itself in neither side.

---

### E2 · Minimum Value to Get Positive Step by Step Sum

**🔗 [LC 1413 — Minimum Value to Get Positive Step by Step Sum](https://leetcode.com/problems/minimum-value-to-get-positive-step-by-step-sum/)** · Easy
**Pattern:** Running Minimum of Prefixes | **Companies:** Amazon, Microsoft

**Hint:** Track the running sum and the smallest value it ever reaches. The starting value must be at least `1 - minPrefix`, and never below 1.

---

### E3 · Find the Middle Index in Array

**🔗 [LC 1991 — Find the Middle Index in Array](https://leetcode.com/problems/find-the-middle-index-in-array/)** · Easy
**Pattern:** Prefix Sum | **Companies:** Amazon, Google, Meta

**Hint:** Total first, then a running `left`. The right side is `total - left - nums[i]`; compare before adding the pivot to `left`.

---

### E4 · Points That Intersect With Cars

**🔗 [LC 2848 — Points That Intersect With Cars](https://leetcode.com/problems/points-that-intersect-with-cars/)** · Easy
**Pattern:** Difference Array | **Companies:** Amazon

**Hint:** Coordinates are at most 100, so allocate a small difference array: `+1` at `start`, `-1` after `end`. Sweep once and count the positions with a positive value.

---

### E5 · Maximum Population Year

**🔗 [LC 1854 — Maximum Population Year](https://leetcode.com/problems/maximum-population-year/)** · Easy
**Pattern:** Difference Array | **Companies:** Amazon, Adobe

**Hint:** A person alive from `birth` to `death - 1` is a range update: `+1` at birth, `-1` at death. Sweep the years and return the earliest year holding the maximum.

---

### E6 · Check if All the Integers in a Range Are Covered

**🔗 [LC 1893 — Check if All the Integers in a Range Are Covered](https://leetcode.com/problems/check-if-all-the-integers-in-a-range-are-covered/)** · Easy
**Pattern:** Difference Array | **Companies:** Amazon, Microsoft

**Hint:** Mark `+1` at each range start and `-1` just after each end, prefix once, then check that every value in `[left, right]` is at least 1.

---

### E7 · Sum of All Odd Length Subarrays

**🔗 [LC 1588 — Sum of All Odd Length Subarrays](https://leetcode.com/problems/sum-of-all-odd-length-subarrays/)** · Easy
**Pattern:** Contribution Counting | **Companies:** Amazon, Google

**Hint:** Brute force with prefix sums is O(n²). Better: count how many odd-length subarrays contain index `i` — `((i + 1) * (n - i) + 1) / 2` — and weight each element by that.

---

## 🟡 Medium Tier (9 Problems)

_The two workhorses: prefix + HashMap for counting, difference arrays for bulk updates._

### M1 · Corporate Flight Bookings

**🔗 [LC 1109 — Corporate Flight Bookings](https://leetcode.com/problems/corporate-flight-bookings/)** · Medium
**Pattern:** Difference Array | **Companies:** Amazon, Google, Microsoft

**Hint:** Each booking is two writes: `+seats` at `first - 1`, `-seats` at `last`. One prefix sweep at the end produces every flight's total. Watch the 1-based indexing.

---

### M2 · Car Pooling

**🔗 [LC 1094 — Car Pooling](https://leetcode.com/problems/car-pooling/)** · Medium
**Pattern:** Difference Array on Locations | **Companies:** Amazon, Google, Meta

**Hint:** Locations go up to 1000, so use a difference array over stops: `+passengers` at `from`, `-passengers` at `to`. Sweep, and fail if the running total ever exceeds capacity.

---

### M3 · Matrix Block Sum

**🔗 [LC 1314 — Matrix Block Sum](https://leetcode.com/problems/matrix-block-sum/)** · Medium
**Pattern:** 2D Prefix Sum | **Companies:** Amazon, Google, Microsoft

**Hint:** Build the integral image once, then clamp each block's corners to the grid: rows `max(0, i-k)` to `min(m-1, i+k)`. Each answer cell is four lookups.

---

### M4 · XOR Queries of a Subarray

**🔗 [LC 1310 — XOR Queries of a Subarray](https://leetcode.com/problems/xor-queries-of-a-subarray/)** · Medium
**Pattern:** Prefix XOR | **Companies:** Amazon, Google

**Hint:** `x ^ x = 0`, so XOR is its own inverse: build `px` with a leading 0 and answer each query with `px[r+1] ^ px[l]`.

---

### M5 · Plates Between Candles

**🔗 [LC 2055 — Plates Between Candles](https://leetcode.com/problems/plates-between-candles/)** · Medium
**Pattern:** Prefix Counts + Nearest Candle | **Companies:** Amazon, Google, Meta

**Hint:** Precompute three arrays: plates before each index, the nearest candle to the left, and the nearest candle to the right. Each query is then a subtraction between the two inner candles.

---

### M6 · Shifting Letters II

**🔗 [LC 2381 — Shifting Letters II](https://leetcode.com/problems/shifting-letters-ii/)** · Medium
**Pattern:** Difference Array over Shifts | **Companies:** Amazon, Google

**Hint:** Each shift is a range update of `+1` or `-1`. Accumulate them in a difference array, sweep once, then rotate each letter by its total shift modulo 26 (normalise negatives).

---

### M7 · Count the Hidden Sequences

**🔗 [LC 2145 — Count the Hidden Sequences](https://leetcode.com/problems/count-the-hidden-sequences/)** · Medium
**Pattern:** Prefix Sums of Differences | **Companies:** Amazon, Google

**Hint:** The differences fix the whole sequence up to one offset. Take the running sum of `differences`, find its minimum and maximum, and count how many starting values keep the range inside `[lower, upper]`.

---

### M8 · Binary Subarrays With Sum

**🔗 [LC 930 — Binary Subarrays With Sum](https://leetcode.com/problems/binary-subarrays-with-sum/)** · Medium
**Pattern:** Prefix + HashMap | **Companies:** Amazon, Google, Meta

**Hint:** Two prefixes differing by `goal` bound a valid subarray. Keep a map of prefix counts seeded with `{0: 1}` and add `map[sum - goal]` at each step. (The at-most trick also works.)

---

### M9 · Number of Sub-arrays With Odd Sum

**🔗 [LC 1524 — Number of Sub-arrays With Odd Sum](https://leetcode.com/problems/number-of-sub-arrays-with-odd-sum/)** · Medium
**Pattern:** Prefix Parity Counting | **Companies:** Amazon, Google

**Hint:** Only the parity of each prefix matters. Count how many prefixes so far were even and how many odd; a subarray is odd exactly when its two ends have different parity. Take the answer modulo 1e9+7.

---

## 🔴 Hard Tier (4 Problems)

_Prefix sums combined with another structure — a deque, a stack, or a segment tree._

### H1 · Shortest Subarray with Sum at Least K

**🔗 [LC 862 — Shortest Subarray with Sum at Least K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/)** · Hard
**Pattern:** Prefix + Monotonic Deque | **Companies:** Google, Amazon, Meta

**Hint:** Negatives break sliding windows, so work on prefix sums: find the shortest `j - i` with `P[j] - P[i] >= k`. Keep a deque of increasing prefixes, popping the front once it qualifies and the back when a new prefix is no larger.

---

### H2 · Number of Submatrices That Sum to Target

**🔗 [LC 1074 — Number of Submatrices That Sum to Target](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/)** · Hard
**Pattern:** 2D Compression + Prefix Map | **Companies:** Google, Amazon, Meta

**Hint:** Fix a pair of rows, collapse the columns between them into a 1D array of sums, and count subarrays equal to `target` with the prefix-map trick. O(m² · n).

---

### H3 · Handling Sum Queries After Update

**🔗 [LC 2569 — Handling Sum Queries After Update](https://leetcode.com/problems/handling-sum-queries-after-update/)** · Hard
**Pattern:** Difference Array + Segment Tree | **Companies:** Google, Amazon

**Hint:** `nums1` only ever flips, so track the count of ones in each range with a lazy segment tree; `nums2`'s total changes by `p × onesCount` per operation. The answers are then a running sum.

---

### H4 · Sum of Total Strength of Wizards

**🔗 [LC 2281 — Sum of Total Strength of Wizards](https://leetcode.com/problems/sum-of-total-strength-of-wizards/)** · Hard
**Pattern:** Prefix of Prefix Sums + Monotonic Stack | **Companies:** Google, Amazon

**Hint:** For each element as the minimum (bounds from a monotonic stack), you need the sum of all subarray sums in that span — which is a prefix sum of the prefix sums. Keep everything modulo 1e9+7 and use 64-bit.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — build a prefix-sum array of length n

// Snippet 2 — answer q range-sum queries after building it

// Snippet 3 — answer q range-sum queries by summing each range directly

// Snippet 4 — count subarrays summing to k with prefix sums + a hash map

// Snippet 5 — apply q range-add updates with a difference array, then read all values

// Snippet 6 — build a 2D prefix-sum table for an m × n grid
```

**Complexity Answers:**

1. **O(n)**.
2. **O(q)** — O(1) each.
3. **O(n · q)**.
4. **O(n)** time, **O(n)** space.
5. **O(n + q)**.
6. **O(m · n)**.

---

## 🔍 Self-Assessment — True / False

1. Prefix sums answer range-sum queries in O(1) after O(n) preparation. → **True**
2. Prefix sums only work for positive numbers. → **False** — any numbers; it is sliding windows that need non-negatives
3. A difference array makes range updates O(1). → **True** — two writes per update, one pass at the end
4. An extra leading 0 in the prefix array removes the L = 0 special case. → **True**
5. Prefix sums still help if values change between queries. → **False** — each change would cost O(n); use a Fenwick tree (Lecture 37)
6. Counting subarrays with sum k needs O(n²) time. → **False** — prefix sums + a hash map give O(n)

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The extra slot:** Why does `prefix` have `n + 1` entries, and what breaks if you drop the leading zero?
2. **The seed:** Why is the prefix map initialised with `{0: 1}`? Give an input that returns the wrong answer without it.
3. **Order of operations:** Why must you look up `sum - k` before inserting the current prefix? Which value of `k` exposes the bug?
4. **Count vs index:** When do you store a _count_ in the prefix map, and when do you store the _first index_? What question does each one answer?
5. **Inverses:** Prefix sums work for `+` and `^` but not for `min`. State the property that decides it.
6. **Updates:** An interviewer adds "and the array can change between queries". Why does a prefix sum stop being the right answer, and what replaces it?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Points That Intersect With Cars](https://leetcode.com/problems/points-that-intersect-with-cars/), [Handling Sum Queries After Update](https://leetcode.com/problems/handling-sum-queries-after-update/), [Sum of Total Strength of Wizards](https://leetcode.com/problems/sum-of-total-strength-of-wizards/), [Count the Hidden Sequences](https://leetcode.com/problems/count-the-hidden-sequences/)                           |
| **Google**    | [Number of Sub-arrays With Odd Sum](https://leetcode.com/problems/number-of-sub-arrays-with-odd-sum/), [Shifting Letters II](https://leetcode.com/problems/shifting-letters-ii/), [XOR Queries of a Subarray](https://leetcode.com/problems/xor-queries-of-a-subarray/), [Left and Right Sum Differences](https://leetcode.com/problems/left-and-right-sum-differences/)                                                         |
| **Meta**      | [Number of Submatrices That Sum to Target](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/), [Shortest Subarray with Sum at Least K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/), [Binary Subarrays With Sum](https://leetcode.com/problems/binary-subarrays-with-sum/), [Car Pooling](https://leetcode.com/problems/car-pooling/)                                             |
| **Microsoft** | [Check if All the Integers in a Range Are Covered](https://leetcode.com/problems/check-if-all-the-integers-in-a-range-are-covered/), [Minimum Value to Get Positive Step by Step Sum](https://leetcode.com/problems/minimum-value-to-get-positive-step-by-step-sum/), [Corporate Flight Bookings](https://leetcode.com/problems/corporate-flight-bookings/), [Matrix Block Sum](https://leetcode.com/problems/matrix-block-sum/) |
| **Adobe**     | [Maximum Population Year](https://leetcode.com/problems/maximum-population-year/)                                                                                                                                                                                                                                                                                                                                                |

---

## ✅ Completion Checklist

- [ ] All 7 Easy problems solved
- [ ] All 9 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write the range-sum formula from memory, with correct off-by-one handling
- [ ] I can explain the difference array as the inverse of a prefix sum

---

**← [Lecture 25 · Two Pointers & Sliding Window](../Lecture25/Assignment.md)** &nbsp;·&nbsp; **[Lecture 27 · Monotonic Stack & Queue](../Lecture27/Assignment.md) →**
