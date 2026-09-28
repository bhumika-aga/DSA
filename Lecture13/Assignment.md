# 🔎 Assignment 10 — Searching Algorithms

> **Lecture:** 13 of 45 — Searching Algorithms
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 5 days · **Total Problems:** 28 (6 Easy · 16 Medium · 6 Hard)
> **Goal:** Master unconditional Linear Searching, classic O(log n) Binary Search templates, **Binary Search on
> Answer Space** (Monotonic optimisation), and matrix traversal boundaries.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                         | Pattern                 | Move                                             |
| --------------------------------------------- | ----------------------- | ------------------------------------------------ |
| "sorted array" + "find"                       | Classic Binary Search   | `while lo <= hi`, `mid = lo + (hi - lo) / 2`     |
| "first / last position"                       | Lower / Upper Bound     | keep searching after a match                     |
| "rotated sorted array"                        | Find the Sorted Half    | compare `nums[mid]` with `nums[lo]`              |
| "minimum capacity / speed / days such that …" | Binary Search on Answer | search the answer space with a feasibility check |
| "peak", "mountain"                            | Slope Search            | move toward the rising side                      |
| "sorted matrix"                               | 2D Binary Search        | flatten indices, or search the value range       |

---

## 🟢 Easy Tier (6 Problems)

_No Easy problems at this stage of the course._

### E1 · Binary Search

**🔗 [LC 704 — Binary Search](https://leetcode.com/problems/binary-search/)** · Easy
**Pattern:** Classic Binary Search | **Companies:** Google, Amazon, Microsoft

**Hint:** The template: `lo = 0`, `hi = n - 1`, `while lo <= hi`, `mid = lo + (hi - lo) / 2`. Compare and discard half. Write it until you can do it without thinking — every later problem modifies this loop.

---

### E2 · Search Insert Position

**🔗 [LC 35 — Search Insert Position](https://leetcode.com/problems/search-insert-position/)** · Easy
**Pattern:** Lower Bound | **Companies:** Amazon, Google, Microsoft

**Hint:** Find the first index with `nums[i] >= target` (lower bound). With `lo = 0, hi = n` and `while lo < hi`, set `hi = mid` when `nums[mid] >= target` and `lo = mid + 1` otherwise. The answer is `lo`, even if the target isn't present.

---

### E3 · Guess Number Higher or Lower

**🔗 [LC 374 — Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)** · Easy
**Pattern:** Classic Binary Search | **Companies:** Google, Amazon

**Hint:** Plain binary search over `[1, n]`, but the comparison comes from `guess(mid)`: -1 means go left, 1 means go right. Use `lo + (hi - lo) / 2` — `n` can be `2³¹ - 1`.

---

### E4 · Valid Perfect Square

**🔗 [LC 367 — Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)** · Easy
**Pattern:** Binary Search on Answer | **Companies:** Google, Amazon, LinkedIn

**Hint:** Binary search `mid` in `[1, num]` and compare `mid * mid` with `num` using `long`. No `sqrt` allowed.

---

### E5 · Arranging Coins

**🔗 [LC 441 — Arranging Coins](https://leetcode.com/problems/arranging-coins/)** · Easy
**Pattern:** Binary Search on Answer | **Companies:** Amazon, Microsoft

**Hint:** Find the largest `k` with `k(k + 1) / 2 <= n`. The condition is monotonic in `k`, so binary search over `[0, n]` with `long` arithmetic.

---

### E6 · Maximum Count of Positive Integer and Negative Integer

**🔗 [LC 2529 — Maximum Count of Positive Integer and Negative Integer](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/)** · Easy
**Pattern:** Lower / Upper Bound | **Companies:** Amazon, Microsoft

**Hint:** The array is sorted. `neg` = first index with value ≥ 0 (lower bound of 0), `pos` = n − first index with value > 0 (upper bound of 0). Return `max(neg, pos)` in O(log n).

---

## 🟡 Medium Tier (16 Problems)

_Focus on Rotated Arrays, Index Parity, and Monotonic Optimisation problems._

### M1 · Find First and Last Position of Element in Sorted Array

**🔗 [LC 34 — Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)** · Medium
**Pattern:** Boundary Search | **Companies:** Meta, Amazon, Google, LinkedIn

**Hint:** Run two boundary searches: the first index `>= target` and the first index `> target`. If the first one is out of range or doesn't hold `target`, return `[-1, -1]`; otherwise return `[first, second - 1]`.

---

### M2 · Peak Index in a Mountain Array

**🔗 [LC 852 — Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/)** · Medium
**Pattern:** Peak | **Companies:** Google, Amazon

**Hint:** Compare `arr[mid]` with `arr[mid + 1]`: if it is rising, the peak is to the right (`lo = mid + 1`); otherwise it's at `mid` or to the left (`hi = mid`). Loop while `lo < hi`.

---

### M3 · Search in Rotated Sorted Array

**🔗 [LC 33 — Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)** · Medium
**Pattern:** Rotated | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** At every `mid`, one half is sorted. If `nums[lo] <= nums[mid]`, the left half is sorted — check whether the target lies in `[nums[lo], nums[mid])` to decide the side. Otherwise the right half is sorted; apply the mirror check.

---

### M4 · Search in Rotated Sorted Array II

**🔗 [LC 81 — Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)** · Medium
**Pattern:** Rotated | **Companies:** Amazon, Google, Meta

**Hint:** Same as the version without duplicates, but when `nums[lo] == nums[mid] == nums[hi]` you can't tell which half is sorted — shrink with `lo++` and `hi--`. This makes the worst case O(n).

---

### M5 · Find Minimum in Rotated Sorted Array

**🔗 [LC 153 — Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)** · Medium
**Pattern:** Index-based | **Companies:** Microsoft, Amazon, Google

**Hint:** Compare `nums[mid]` with `nums[hi]`: if `nums[mid] > nums[hi]`, the minimum is to the right (`lo = mid + 1`); otherwise it's at `mid` or to the left (`hi = mid`). Loop while `lo < hi`.

---

### M6 · Search a 2D Matrix

**🔗 [LC 74 — Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)** · Medium
**Pattern:** 2D | **Companies:** Amazon, Microsoft, Meta

**Hint:** Treat the matrix as one sorted array of length `m × n`. Binary search the index and convert it to a cell with `row = mid / n`, `col = mid % n`.

---

### M7 · Find Peak Element

**🔗 [LC 162 — Find Peak Element](https://leetcode.com/problems/find-peak-element/)** · Medium
**Pattern:** Peak | **Companies:** Uber, Google, Meta

**Hint:** Any neighbour that's bigger leads uphill to a peak. If `nums[mid] < nums[mid + 1]`, go right; otherwise go left, keeping `mid`. The array ends count as -∞, so a peak always exists.

---

### M8 · Single Element in a Sorted Array

**🔗 [LC 540 — Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)** · Medium
**Pattern:** Binary Search on Pairs | **Companies:** Amazon, Google, Meta

**Hint:** Before the single element, pairs start at even indices. Force `mid` to be even (`mid -= mid % 2`); if `nums[mid] == nums[mid + 1]`, the single is to the right (`lo = mid + 2`), otherwise `hi = mid`.

---

### M9 · Koko Eating Bananas

**🔗 [LC 875 — Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)** · Medium
**Pattern:** Search-on-Answer | **Companies:** Airbnb, Google, Amazon

**Hint:** Binary search the speed `k` in `[1, max(piles)]`. Hours needed is `sum(ceil(pile / k))` — use `(pile + k - 1) / k`. Find the smallest `k` whose hours are `<= h`.

---

### M10 · Capacity To Ship Packages Within D Days

**🔗 [LC 1011 — Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)** · Medium
**Pattern:** Search-on-Answer | **Companies:** Amazon, Google, Meta

**Hint:** The answer lies between `max(weights)` and `sum(weights)`. For a capacity, greedily fill days and count how many you need. Find the smallest capacity that needs at most `days` days.

---

### M11 · Find the Smallest Divisor Given a Threshold

**🔗 [LC 1283 — Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/)** · Medium
**Pattern:** Binary Search on Answer | **Companies:** Amazon, Google

**Hint:** The sum of `ceil(num / d)` only shrinks as `d` grows, so binary search `d` in `[1, max(nums)]` for the smallest divisor whose sum is `<= threshold`.

---

### M12 · Minimum Number of Days to Make m Bouquets

**🔗 [LC 1482 — Minimum Number of Days to Make m Bouquets](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/)** · Medium
**Pattern:** Binary Search on Answer | **Companies:** Amazon, Google

**Hint:** If `m * k > n`, return -1. Otherwise binary search the day in `[min(bloom), max(bloom)]`. For a day, count bouquets by scanning runs of consecutive flowers that have bloomed. Find the first day that yields `m`.

---

### M13 · Magnetic Force Between Two Balls

**🔗 [LC 1552 — Magnetic Force Between Two Balls](https://leetcode.com/problems/magnetic-force-between-two-balls/)** · Medium
**Pattern:** Binary Search on Answer (Max-Min) | **Companies:** Amazon, Google

**Hint:** Sort positions. Binary search the minimum distance `d`; it's feasible if greedily placing each ball at the first position at least `d` from the previous one fits all `m` balls. Find the largest feasible `d`.

---

### M14 · Maximum Candies Allocated to K Children

**🔗 [LC 2226 — Maximum Candies Allocated to K Children](https://leetcode.com/problems/maximum-candies-allocated-to-k-children/)** · Medium
**Pattern:** Binary Search on Answer | **Companies:** Google, Amazon

**Hint:** Search `x` in `[1, max(candies)]`. `x` is feasible if `sum(pile / x) >= k` (use `long`). Find the largest feasible `x`; if even `x = 1` fails, return 0.

---

### M15 · Heaters

**🔗 [LC 475 — Heaters](https://leetcode.com/problems/heaters/)** · Medium
**Pattern:** Sort + Binary Search | **Companies:** Amazon, Google

**Hint:** Sort the heaters. For each house, binary search its nearest heater on each side and take the smaller distance. The answer is the largest of these distances.

---

### M16 · Kth Smallest Element in a Sorted Matrix

**🔗 [LC 378 — Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)** · Medium
**Pattern:** 2D Value Search | **Companies:** Amazon, Google, Meta

**Hint:** Binary search the value, not the index: in `[matrix[0][0], matrix[n-1][n-1]]`, count cells `<= mid` with a staircase walk from the bottom-left (O(n)). The smallest value with count `>= k` is the answer.

---

## 🔴 Hard Tier (6 Problems)

_Focus on extremely tight constraints and dual-array partitioning logic._

### H1 · Median of Two Sorted Arrays

**🔗 [LC 4 — Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)** · Hard
**Pattern:** Dual-Partitioning | **Companies:** Apple, Google, Amazon, Adobe

**Hint:** Binary search a cut in the smaller array so the left parts of both arrays hold half the elements. The cut is correct when `maxLeftA <= minRightB` and `maxLeftB <= minRightA`. The median comes from the max-left and min-right values. O(log(min(m, n))).

---

### H2 · Split Array Largest Sum

**🔗 [LC 410 — Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)** · Hard
**Pattern:** Binary Search on Answer (Min-Max) | **Companies:** Google, Amazon, Meta

**Hint:** Binary search the largest allowed subarray sum in `[max(nums), sum(nums)]`. For a limit, greedily count how many pieces you need; find the smallest limit that needs at most `k` pieces.

---

### H3 · Maximise the Minimum Powered City

**🔗 [LC 2528 — Maximize the Minimum Powered City](https://leetcode.com/problems/maximize-the-minimum-powered-city/)** · Hard
**Pattern:** Max-Min | **Companies:** Google, Amazon

**Hint:** The "maximise the minimum" dual of Split Array Largest Sum: binary search the answer, then greedily place stations with a difference array to check feasibility.

---

### H4 · Find K-th Smallest Pair Distance

**🔗 [LC 719 — Find K-th Smallest Pair Distance](https://leetcode.com/problems/find-k-th-smallest-pair-distance/)** · Hard
**Pattern:** Binary Search on Answer + Two Pointers | **Companies:** Google, Amazon

**Hint:** Sort. Binary search the distance `d` in `[0, max - min]`. Count pairs with distance `<= d` using a sliding right pointer (O(n)). Find the smallest `d` whose count is `>= k`.

---

### H5 · Preimage Size of Factorial Zeroes Function

**🔗 [LC 793 — Preimage Size of Factorial Zeroes Function](https://leetcode.com/problems/preimage-size-of-factorial-zeroes-function/)** · Hard
**Pattern:** Binary Search on a Monotonic Function | **Companies:** Google, Amazon

**Hint:** The number of trailing zeros of `x!` is `x/5 + x/25 + …`, which never decreases as `x` grows. Binary search the smallest `x` with at least `k` zeros; if it has exactly `k`, the answer is 5, otherwise 0.

---

### H6 · Smallest Good Base

**🔗 [LC 483 — Smallest Good Base](https://leetcode.com/problems/smallest-good-base/)** · Hard
**Pattern:** Binary Search per Length | **Companies:** Google, Amazon

**Hint:** `n = 1 + k + k² + … + k^m`. Try each length `m` from the largest (about 60) down to 1, and binary search the base `k` for that length. Watch overflow when summing. The first match gives the smallest base.

---

## 📊 Complexity Analysis Exercises

| Search Space         | Conditions      | Complexity       | Use Case         |
| :------------------- | :-------------- | :--------------- | :--------------- |
| Unsorted Array       | None            | O(n)             | General search   |
| Sorted Array         | Monotonicity    | O(log n)         | Standard BS      |
| Rotated Array        | Sorted segments | O(log n)         | Pivot search     |
| Matrix (m × n)       | Row/Col Sorted  | O(log(m · n))    | 2D Mapping       |
| Integer Range [1, k] | `isValid(mid)`  | O(check · log k) | Search-on-Answer |

---

## 🔍 Self-Assessment — True / False

1. Binary search works on any array. → **False** — only on data where the condition is monotonic, such as a sorted array
2. mid = (lo + hi) / 2 can overflow. → **True** — lo + hi can exceed the int limit; use lo + (hi − lo) / 2
3. Binary search on the answer requires the input array to be sorted. → **False** — it requires the yes/no check to be monotonic in the answer
4. A binary search over n items needs about log₂ n steps. → **True** — each step halves the range
5. Finding the first occurrence and any occurrence cost the same Big-O. → **True** — both O(log n); only the update rule differs
6. A rotated sorted array cannot be binary searched. → **False** — one half is always sorted, and you can tell which

---

## 🧠 Conceptual Check

1. **The Invariant**: What property MUST `isValid(mid)` satisfy to allow Binary Search? (Hint: Monotonicity).
2. **Post-Loop State**: If the target is NOT found, what is the relative position of `lo` and `hi`?
3. **Infinite Loops**: Why is `mid = lo + (hi - lo + 1) / 2` necessary in some variants?
4. **Binary Search on Doubles**: How do you decide the loop condition for decimal ranges? (e.g., while
   `hi - lo > 1e-9`).

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Find K-th Smallest Pair Distance](https://leetcode.com/problems/find-k-th-smallest-pair-distance/), [Maximize the Minimum Powered City](https://leetcode.com/problems/maximize-the-minimum-powered-city/), [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/), [Preimage Size of Factorial Zeroes Function](https://leetcode.com/problems/preimage-size-of-factorial-zeroes-function/) |
| **Google**    | [Smallest Good Base](https://leetcode.com/problems/smallest-good-base/), [Find Peak Element](https://leetcode.com/problems/find-peak-element/), [Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/), [Heaters](https://leetcode.com/problems/heaters/)                                                                                                   |
| **Meta**      | [Find Peak Element](https://leetcode.com/problems/find-peak-element/), [Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/), [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/), [Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)                                 |
| **Microsoft** | [Arranging Coins](https://leetcode.com/problems/arranging-coins/), [Maximum Count of Positive Integer and Negative Integer](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/), [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/), [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)                       |
| **LinkedIn**  | [Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/), [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)                                                                                                                                                                                                 |

---

## ✅ Completion Checklist

- [ ] All 8 Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 7 Hard problems attempted
- [ ] Self-assessment completed without looking at the notes
- [ ] Every complexity exercise answered before checking
- [ ] All 4 conceptual questions answered out loud
- [ ] I can write lower bound and upper bound without off-by-one errors
- [ ] I can recognise a monotonic feasibility function in a word problem

---

**← [Lecture 12 · Sorting Algorithms](../Lecture12/Assignment.md)** &nbsp;·&nbsp; **[Lecture 14 · Linked Lists](../Lecture14/Assignment.md) →**
