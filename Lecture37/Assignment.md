# 📶 Assignment 30 — Segment Trees & Fenwick Trees

> **Lecture:** 37 of 45 — Segment Trees & Fenwick Trees
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 6 days · **Total Problems:** 22 (3 Easy · 12 Medium · 7 Hard)
> **Goal:** Choose the cheapest correct structure for a range workload, and write a segment tree and a Fenwick tree from memory.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                  | Pattern                            | Move                                                  |
| ------------------------------------------------------ | ---------------------------------- | ----------------------------------------------------- |
| Range query, array never changes                       | Prefix sums (or sparse table)      | Build once, subtract two entries                      |
| All updates first, then all queries                    | Difference array                   | +v at l, −v at r+1, one prefix pass                   |
| Point update + range sum, interleaved                  | Fenwick tree                       | Twelve lines, i AND -i, 1-based indices               |
| Point update + range min / max / gcd                   | Segment tree                       | Min and max are not invertible, so a BIT cannot do it |
| Range update + range query                             | Segment tree with lazy propagation | Mark the covering node, push before descending        |
| Count how many earlier values are smaller              | BIT over compressed values         | Sweep once; each step is a prefix count               |
| Coordinates up to 10⁹, few operations                  | Compress, or build nodes on demand | Only touched ranges need to exist                     |
| DP transition needs the best previous state in a range | Segment tree over the value axis   | O(n) per step becomes O(log n)                        |

---

## 🟢 Easy Tier (3 Problems)

_Three range questions that need no structure. Solve each one and say out loud why a tree would be the wrong answer — that judgement is the point of the tier._

### E1 · Count Odd Numbers in an Interval Range

**🔗 [LC 1523 — Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/)** · Easy
**Pattern:** Closed-form range count | **Companies:** Amazon

**Hint:** No structure at all — derive it from the count of odd numbers below each endpoint.

---

### E2 · Count the Number of Vowel Strings in Range

**🔗 [LC 2586 — Count the Number of Vowel Strings in Range](https://leetcode.com/problems/count-the-number-of-vowel-strings-in-range/)** · Easy
**Pattern:** Prefix sums | **Companies:** Amazon · Google

**Hint:** Build one prefix array of vowel-string counts; every query is a subtraction.

---

### E3 · Sum of Variable Length Subarrays

**🔗 [LC 3427 — Sum of Variable Length Subarrays](https://leetcode.com/problems/sum-of-variable-length-subarrays/)** · Easy
**Pattern:** Prefix sums | **Companies:** Google

**Hint:** The sum over a variable-length window is still prefix[i] − prefix[start].

---

## 🟡 Medium Tier (12 Problems)

_The main set. Some need a Fenwick tree, some a segment tree, and several deliberately need neither. Decide which before you write a line._

### M1 · Range Sum Query - Mutable

**🔗 [LC 307 — Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/)** · Medium
**Pattern:** Fenwick tree / segment tree | **Companies:** Google · Amazon · Microsoft

**Hint:** Update with the delta, not the value, and keep the original array beside the tree.

---

### M2 · Count Number of Teams

**🔗 [LC 1395 — Count Number of Teams](https://leetcode.com/problems/count-number-of-teams/)** · Medium
**Pattern:** Fenwick tree over values | **Companies:** Amazon · Google

**Hint:** Fix the middle soldier; count smaller on the left and larger on the right.

---

### M3 · Queries on a Permutation With Key

**🔗 [LC 1409 — Queries on a Permutation With Key](https://leetcode.com/problems/queries-on-a-permutation-with-key/)** · Medium
**Pattern:** Fenwick tree (positions) | **Companies:** Amazon · Google

**Hint:** Reserve m slots in front so a queried element can move to the front in O(log n).

---

### M4 · Best Team With No Conflicts

**🔗 [LC 1626 — Best Team With No Conflicts](https://leetcode.com/problems/best-team-with-no-conflicts/)** · Medium
**Pattern:** Segment tree over values + DP | **Companies:** Amazon · Google

**Hint:** Sort by age, then dp[score] = best total ending at that score — a range max query.

---

### M5 · Range Frequency Queries

**🔗 [LC 2080 — Range Frequency Queries](https://leetcode.com/problems/range-frequency-queries/)** · Medium
**Pattern:** Positions per value + binary search | **Companies:** Amazon · Google

**Hint:** Nothing is ever updated, so a map from value to sorted indices beats any tree.

---

### M6 · Most Beautiful Item for Each Query

**🔗 [LC 2070 — Most Beautiful Item for Each Query](https://leetcode.com/problems/most-beautiful-item-for-each-query/)** · Medium
**Pattern:** Offline queries + prefix max | **Companies:** Amazon · Google

**Hint:** Sort items and queries by price, sweep once, and keep a running maximum beauty.

---

### M7 · Minimum Absolute Difference Queries

**🔗 [LC 1906 — Minimum Absolute Difference Queries](https://leetcode.com/problems/minimum-absolute-difference-queries/)** · Medium
**Pattern:** Prefix counts per value | **Companies:** Google · Amazon

**Hint:** Values are at most 100, so 100 prefix-count arrays answer every query in O(100).

---

### M8 · Intervals Between Identical Elements

**🔗 [LC 2121 — Intervals Between Identical Elements](https://leetcode.com/problems/intervals-between-identical-elements/)** · Medium
**Pattern:** Prefix sums per value | **Companies:** Google

**Hint:** Group the indices by value, then use prefix sums inside each group.

---

### M9 · Count Vowel Strings in Ranges

**🔗 [LC 2559 — Count Vowel Strings in Ranges](https://leetcode.com/problems/count-vowel-strings-in-ranges/)** · Medium
**Pattern:** Prefix sums | **Companies:** Amazon

**Hint:** One pass to mark the qualifying strings, one prefix array, O(1) per query.

---

### M10 · Sum of Even Numbers After Queries

**🔗 [LC 985 — Sum of Even Numbers After Queries](https://leetcode.com/problems/sum-of-even-numbers-after-queries/)** · Medium
**Pattern:** Running aggregate | **Companies:** Amazon

**Hint:** Keep the even sum and patch it per query — no range structure is needed at all.

---

### M11 · Subrectangle Queries

**🔗 [LC 1476 — Subrectangle Queries](https://leetcode.com/problems/subrectangle-queries/)** · Medium
**Pattern:** Store the updates | **Companies:** Google

**Hint:** With few updates, replaying them newest-first beats maintaining the matrix.

---

### M12 · Sum of Matrix After Queries

**🔗 [LC 2718 — Sum of Matrix After Queries](https://leetcode.com/problems/sum-of-matrix-after-queries/)** · Medium
**Pattern:** Reverse-time processing | **Companies:** Google · Amazon

**Hint:** Process the queries backwards; the last write to a row or column is the one that survives.

---

## 🔴 Hard Tier (7 Problems)

_Lazy propagation, coordinate compression, dynamic trees, offline queries and a DP accelerated by a range maximum — the five ways this material actually shows up._

### H1 · Falling Squares

**🔗 [LC 699 — Falling Squares](https://leetcode.com/problems/falling-squares/)** · Hard
**Pattern:** Coordinate compression + lazy assign | **Companies:** Google · Amazon

**Hint:** Query the max under the square, then assign that plus the side to the whole interval.

---

### H2 · My Calendar III

**🔗 [LC 732 — My Calendar III](https://leetcode.com/problems/my-calendar-iii/)** · Hard
**Pattern:** Lazy segment tree / sweep | **Companies:** Google · Amazon

**Hint:** Range add and a global maximum. The root holds the answer.

---

### H3 · Range Module

**🔗 [LC 715 — Range Module](https://leetcode.com/problems/range-module/)** · Hard
**Pattern:** Interval map / segment tree | **Companies:** Google · Amazon

**Hint:** A sorted map of disjoint intervals is shorter than a tree here — merge on add, split on remove.

---

### H4 · Longest Increasing Subsequence II

**🔗 [LC 2407 — Longest Increasing Subsequence II](https://leetcode.com/problems/longest-increasing-subsequence-ii/)** · Hard
**Pattern:** Segment tree (max) over values | **Companies:** Google · Amazon

**Hint:** dp indexed by value; the k constraint becomes a contiguous range maximum query.

---

### H5 · Count Integers in Intervals

**🔗 [LC 2276 — Count Integers in Intervals](https://leetcode.com/problems/count-integers-in-intervals/)** · Hard
**Pattern:** Interval map | **Companies:** Google · Amazon

**Hint:** Merge on insert and maintain the covered count incrementally.

---

### H6 · Find Building Where Alice and Bob Can Meet

**🔗 [LC 2940 — Find Building Where Alice and Bob Can Meet](https://leetcode.com/problems/find-building-where-alice-and-bob-can-meet/)** · Hard
**Pattern:** Offline queries + monotonic stack or segment tree | **Companies:** Google · Amazon

**Hint:** Sort the queries by right index and sweep, or query the first index to the right with a larger height.

---

### H7 · Peaks in Array

**🔗 [LC 3187 — Peaks in Array](https://leetcode.com/problems/peaks-in-array/)** · Hard
**Pattern:** Segment tree (sum of flags) | **Companies:** Google

**Hint:** A peak flag changes only for the neighbours of an updated index — repair those three, then query the range.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — build a segment tree over n items

// Snippet 2 — one range query or one point update

// Snippet 3 — q range queries with no updates, using prefix sums instead

// Snippet 4 — range add + range sum with lazy propagation

// Snippet 5 — Fenwick tree prefix query and point update

// Snippet 6 — count inversions with a Fenwick tree over compressed values
```

**Complexity Answers:**

1. **O(n)**.
2. **O(log n)**.
3. **O(n + q)** — no tree needed.
4. **O(log n)** per operation.
5. **O(log n)** each.
6. **O(n log n)**.

---

## 🔍 Self-Assessment — True / False

1. A segment tree array is sized 4n. → **True** — a safe bound for any n
2. A Fenwick tree can answer range-minimum queries with updates. → **False** — minimum is not invertible; use a segment tree
3. Fenwick trees are indexed from 1. → **True** — index 0 has no lowest set bit
4. Lazy propagation defers range updates until a node is visited. → **True**
5. If there are no updates, a segment tree is the simplest tool. → **False** — prefix sums are simpler
6. The no-overlap case in a minimum query should return 0. → **False** — it should return +infinity, the identity for min

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The trade-off:** With n = q = 10⁵ mixed queries and updates, give the total cost of a plain array, a prefix-sum array and a segment tree. Which of the three is actually feasible?
2. **Why 4n:** Why is a segment tree array sized 4n rather than 2n? What input breaks the 2n version?
3. **Identity:** Name the value the no-overlap branch must return for sum, minimum, maximum and gcd queries.
4. **Associativity:** Which operations can a segment tree aggregate, and which cannot? Justify the rule.
5. **Lazy rules:** State the two invariants that keep lazy propagation correct, and name the bug that follows from breaking the second one.
6. **Add versus assign:** Why does a range-assign lazy value need a separate flag, when a range-add value does not?
7. **Low bit:** Explain what `i AND -i` computes and which elements `bit[6]` covers in a Fenwick tree.
8. **One-based:** Why must a Fenwick tree be indexed from 1? What happens at index 0?
9. **BIT limits:** Give a query a Fenwick tree cannot answer directly, and say what property of the operation is missing.
10. **Compression:** When values reach 10⁹ but n is 10⁵, why is coordinate compression valid? What property of the queries does it rely on?
11. **Not a tree:** Give two situations in this lecture where the right answer was no tree at all, and say what replaced it.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | [Peaks in Array](https://leetcode.com/problems/peaks-in-array/), [Intervals Between Identical Elements](https://leetcode.com/problems/intervals-between-identical-elements/), [Subrectangle Queries](https://leetcode.com/problems/subrectangle-queries/), [Sum of Variable Length Subarrays](https://leetcode.com/problems/sum-of-variable-length-subarrays/)                                                   |
| **Amazon**    | [Count Vowel Strings in Ranges](https://leetcode.com/problems/count-vowel-strings-in-ranges/), [Sum of Even Numbers After Queries](https://leetcode.com/problems/sum-of-even-numbers-after-queries/), [Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/), [Count Integers in Intervals](https://leetcode.com/problems/count-integers-in-intervals/) |
| **Microsoft** | [Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/)                                                                                                                                                                                                                                                                                                                              |

---

## ✅ Completion Checklist

- [ ] All 3 Easy problems solved
- [ ] All 12 Medium problems solved
- [ ] All 7 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 11 conceptual questions answered out loud
- [ ] I can write a segment tree and a Fenwick tree from memory
- [ ] I can decide between prefix sums, a difference array, a BIT and a segment tree in under a minute
- [ ] I can add lazy propagation without forgetting a push
- [ ] I can use a BIT over compressed values to count inversions
- [ ] I can name the structure each of the 22 problems needs, and why
- [ ] I revisited every problem I needed a hint for

---

**← [Lecture 36 · Tries (Prefix Trees)](../Lecture36/Assignment.md)** &nbsp;·&nbsp; **Lecture 38 · Square Root Decomposition & Mo's Algorithm — coming soon →**
