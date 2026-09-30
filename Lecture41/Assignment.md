# 🎚️ Assignment 41 — Balanced BSTs & Ordered Structures

> **Lecture:** 41 of 45 — Balanced BSTs & Ordered Structures
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 4 days · **Total Problems:** 18 (4 Easy · 9 Medium · 5 Hard)
> **Goal:** Reach for TreeMap and TreeSet whenever a problem needs the nearest value, the smallest or largest item that can change, or keys kept in order — and know what keeps those structures fast.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                    | Pattern                | Move                                                         |
| -------------------------------------------------------- | ---------------------- | ------------------------------------------------------------ |
| "Closest value to x", "nearest on either side"           | Floor / ceiling query  | `floor(x)` and `ceiling(x)` on a TreeSet                     |
| Max or min must survive updates **and** deletions        | TreeMap as a multiset  | Value → count; remove the key when the count reaches 0       |
| A window of recent items, and you need the nearest value | Ordered sliding window | Add the new item, remove the one that left, query neighbours |
| Keys kept in order, merged with their neighbours         | Interval map           | `floorKey` finds the interval that might overlap             |
| The smallest free slot, wrapping around                  | TreeSet of free slots  | `ceiling(i)`, else `first()`                                 |
| "The k-th best so far", k grows by one each query        | Two heaps split at k   | The heap boundary moves one step per query                   |
| The input is already a BST                               | In-order traversal     | In-order visits the keys in sorted order                     |

---

## 🟢 Easy Tier (4 Problems)

_The BST ordering and the "only neighbours in sorted order matter" idea that every ordered query rests on._

### E1 · Minimum Absolute Difference in BST

**🔗 [LC 530 — Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)** · Easy
**Pattern:** In-order = sorted order | **Companies:** Google, Amazon

**Hint:** In-order traversal visits the values in sorted order, and the closest pair in a sorted list is always two neighbours. Remember the previous value as you go.

---

### E2 · Two Sum IV - Input is a BST

**🔗 [LC 653 — Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)** · Easy
**Pattern:** In-order + two pointers | **Companies:** Amazon, Meta, Microsoft

**Hint:** An in-order traversal gives a sorted list; then move two pointers inwards from the ends. A HashSet of values seen so far also works.

---

### E3 · Increasing Order Search Tree

**🔗 [LC 897 — Increasing Order Search Tree](https://leetcode.com/problems/increasing-order-search-tree/)** · Easy
**Pattern:** In-order rewiring | **Companies:** Amazon, Microsoft

**Hint:** Walk in order, keeping a tail pointer: set each node's left to null and hang it on the tail's right. The result is exactly the degenerate "linked-list" BST that balancing prevents.

---

### E4 · Minimum Absolute Difference

**🔗 [LC 1200 — Minimum Absolute Difference](https://leetcode.com/problems/minimum-absolute-difference/)** · Easy
**Pattern:** Sort, then neighbours only | **Companies:** Amazon, Google

**Hint:** After sorting, only adjacent elements can form the minimum difference. One pass finds it, a second collects every pair that achieves it.

---

## 🟡 Medium Tier (9 Problems)

_TreeMap and TreeSet doing real work: multisets, nearest-value lookups, ordered design problems._

### M1 · Stock Price Fluctuation

**🔗 [LC 2034 — Stock Price Fluctuation](https://leetcode.com/problems/stock-price-fluctuation/)** · Medium
**Pattern:** TreeMap as a multiset | **Companies:** Google, Amazon

**Hint:** Keep time → price in a HashMap and price → count in a TreeMap. A correction removes one copy of the old price before adding the new one; max and min are `lastKey()` and `firstKey()`.

---

### M2 · Exam Room

**🔗 [LC 855 — Exam Room](https://leetcode.com/problems/exam-room/)** · Medium
**Pattern:** TreeSet of occupied seats | **Companies:** Google

**Hint:** Keep the taken seats sorted. The best seat is either seat 0, the middle of the widest gap between two neighbours, or seat n − 1 — check them in that order and break ties towards the smaller index.

---

### M3 · Design a Food Rating System

**🔗 [LC 2353 — Design a Food Rating System](https://leetcode.com/problems/design-a-food-rating-system/)** · Medium
**Pattern:** One TreeSet per group | **Companies:** Amazon, Bloomberg

**Hint:** For each cuisine keep a TreeSet ordered by (rating descending, name ascending). To change a rating, remove the food, update the rating, and re-insert — never change a key while it sits inside the set.

---

### M4 · Design a Number Container System

**🔗 [LC 2349 — Design a Number Container System](https://leetcode.com/problems/design-a-number-container-system/)** · Medium
**Pattern:** Map to TreeSet | **Companies:** Google, Amazon

**Hint:** index → number in a HashMap, number → TreeSet of indices. Replacing a number removes the index from the old set first; `find` returns the set's `first()`.

---

### M5 · Minimum Absolute Sum Difference

**🔗 [LC 1818 — Minimum Absolute Sum Difference](https://leetcode.com/problems/minimum-absolute-sum-difference/)** · Medium
**Pattern:** Floor / ceiling in a sorted copy | **Companies:** Amazon, Google

**Hint:** Replacing nums1[i] helps most when the replacement is the value in nums1 closest to nums2[i] — its floor or ceiling in a sorted copy. Track the largest saving; take the modulo only at the end.

---

### M6 · Minimum Absolute Difference Between Elements With Constraint

**🔗 [LC 2817 — Minimum Absolute Difference Between Elements With Constraint](https://leetcode.com/problems/minimum-absolute-difference-between-elements-with-constraint/)** · Medium
**Pattern:** Growing TreeSet + floor / ceiling | **Companies:** Google, Amazon

**Hint:** Walk j from x upwards, adding nums[j − x] to a TreeSet before each query. Every value in the set is at least x positions behind j, so the answer is the nearest of `floor(nums[j])` and `ceiling(nums[j])`.

---

### M7 · Divide Array in Sets of K Consecutive Numbers

**🔗 [LC 1296 — Divide Array in Sets of K Consecutive Numbers](https://leetcode.com/problems/divide-array-in-sets-of-k-consecutive-numbers/)** · Medium
**Pattern:** TreeMap counts, smallest first | **Companies:** Google, Amazon

**Hint:** The smallest remaining number must start a group. Take `firstKey()`, then use one copy of each of the next k − 1 numbers; any missing number means false.

---

### M8 · Tweet Counts Per Frequency

**🔗 [LC 1348 — Tweet Counts Per Frequency](https://leetcode.com/problems/tweet-counts-per-frequency/)** · Medium
**Pattern:** TreeMap range views | **Companies:** Twitter, Amazon

**Hint:** Per tweet name, keep a TreeMap time → count. For each chunk, iterate `subMap(start, true, end, true)` and add its counts — the view jumps straight to the first time in range.

---

### M9 · All Elements in Two Binary Search Trees

**🔗 [LC 1305 — All Elements in Two Binary Search Trees](https://leetcode.com/problems/all-elements-in-two-binary-search-trees/)** · Medium
**Pattern:** Two in-orders, then merge | **Companies:** Meta, Amazon

**Hint:** Each in-order traversal is sorted, so merge the two lists as in merge sort. For less memory, run two iterative in-orders with stacks and advance whichever is smaller.

---

## 🔴 Hard Tier (5 Problems)

_Ordered structures under pressure: windows, interval merging, wrap-around searches, building a balanced structure yourself, and a moving k-th element._

### H1 · Contains Duplicate III

**🔗 [LC 220 — Contains Duplicate III](https://leetcode.com/problems/contains-duplicate-iii/)** · Hard
**Pattern:** Ordered sliding window | **Companies:** Google, Airbnb, Amazon

**Hint:** Keep the last indexDiff values in a TreeSet. For each new x, the only value worth checking is `ceiling(x − valueDiff)`: if it exists and is ≤ x + valueDiff, you are done.

---

### H2 · Design Skiplist

**🔗 [LC 1206 — Design Skiplist](https://leetcode.com/problems/design-skiplist/)** · Hard
**Pattern:** Linked levels with random heights | **Companies:** Google, Amazon

**Hint:** Each node has one next-pointer per level. Search from the top level, moving right while the next value is smaller, then dropping down. Insert with a coin-flip height, splicing in after the predecessor you recorded on each level.

---

### H3 · Data Stream as Disjoint Intervals

**🔗 [LC 352 — Data Stream as Disjoint Intervals](https://leetcode.com/problems/data-stream-as-disjoint-intervals/)** · Hard
**Pattern:** TreeMap of intervals | **Companies:** Amazon, Google

**Hint:** Store start → end. For a new value v, `floorKey(v)` is the only interval that can contain or touch it from the left, and `ceilingKey(v + 1)` the only one that can touch it from the right. Merge with either or both.

---

### H4 · Find Servers That Handled Most Number of Requests

**🔗 [LC 1606 — Find Servers That Handled Most Number of Requests](https://leetcode.com/problems/find-servers-that-handled-most-number-of-requests/)** · Hard
**Pattern:** TreeSet of free servers + heap of busy ones | **Companies:** Amazon, Google

**Hint:** Before each request, move every server whose job has finished from a (finish time, server) min-heap back into the free TreeSet. Then take `ceiling(i % k)`, or `first()` if that is null.

---

### H5 · Sequentially Ordinal Rank Tracker

**🔗 [LC 2102 — Sequentially Ordinal Rank Tracker](https://leetcode.com/problems/sequentially-ordinal-rank-tracker/)** · Hard
**Pattern:** Two heaps split at the query count | **Companies:** Google, Amazon

**Hint:** One heap holds the best items already returned (worst of them on top), the other holds the rest (best on top). Each add passes through the first heap; each get moves one item across.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — insert n keys, already in sorted order, into a plain (unbalanced) BST

// Snippet 2 — insert the same n sorted keys into a TreeMap

// Snippet 3 — for each of n values: floor(x) and ceiling(x) on a TreeSet of size n

// Snippet 4 — map.subMap(a, true, b, true) and then iterate over its k entries

// Snippet 5 — k-th smallest in a BST where every node stores its subtree size

// Snippet 6 — search in a skip list with n keys
```

**Complexity Answers:**

1. **O(n²)** — every insert walks the whole right-leaning chain.
2. **O(n log n)** — the red-black tree keeps its height O(log n).
3. **O(n log n)**.
4. **O(log n + k)** — find the start, then walk k entries.
5. **O(h)** — O(log n) when the tree is balanced.
6. **O(log n)** expected — the levels behave like a binary search.

---

## 🔍 Self-Assessment — True / False

1. A BST built by inserting keys in sorted order has height O(log n). → **False** — it becomes a chain of height n
2. Java's TreeMap is a red-black tree, so its get, put and remove are O(log n) in the worst case. → **True**
3. `floorKey(x)` returns the smallest key strictly greater than x. → **False** — that is `higherKey`; `floorKey` is the largest key ≤ x
4. A rotation changes the in-order sequence of the keys. → **False** — it changes the shape only; the in-order order is preserved
5. A PriorityQueue can remove an arbitrary element in O(log n). → **False** — finding it is O(n); a TreeMap can do it in O(log n)
6. A skip list stays balanced without any rotations. → **True** — random node heights keep searches O(log n) in expectation

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Degeneration**: Which insertion orders turn a plain BST into a linked list, and why does that make every operation O(n)?
2. **Rotations**: Draw a right rotation. Which pointers change, and why is the BST order still correct afterwards?
3. **Invariants**: State the AVL invariant and two red-black rules in plain words. Which one keeps the tree more tightly balanced?
4. **Multiset**: Java has no built-in multiset. How do you fake one with a TreeMap, and what goes wrong if you forget to remove zero counts?
5. **Choosing**: When is a PriorityQueue enough, and when do you need a TreeMap instead?
6. **Order statistics**: What single extra field per node turns a BST into one that answers "k-th smallest" in O(log n)?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Google**    | [Exam Room](https://leetcode.com/problems/exam-room/), [Stock Price Fluctuation](https://leetcode.com/problems/stock-price-fluctuation/), [Design Skiplist](https://leetcode.com/problems/design-skiplist/), [Sequentially Ordinal Rank Tracker](https://leetcode.com/problems/sequentially-ordinal-rank-tracker/)                                                                                                                         |
| **Amazon**    | [Find Servers That Handled Most Number of Requests](https://leetcode.com/problems/find-servers-that-handled-most-number-of-requests/), [Data Stream as Disjoint Intervals](https://leetcode.com/problems/data-stream-as-disjoint-intervals/), [Minimum Absolute Sum Difference](https://leetcode.com/problems/minimum-absolute-sum-difference/), [Minimum Absolute Difference](https://leetcode.com/problems/minimum-absolute-difference/) |
| **Meta**      | [All Elements in Two Binary Search Trees](https://leetcode.com/problems/all-elements-in-two-binary-search-trees/), [Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)                                                                                                                                                                                                                                 |
| **Bloomberg** | [Design a Food Rating System](https://leetcode.com/problems/design-a-food-rating-system/)                                                                                                                                                                                                                                                                                                                                                  |
| **Airbnb**    | [Contains Duplicate III](https://leetcode.com/problems/contains-duplicate-iii/)                                                                                                                                                                                                                                                                                                                                                            |
| **Twitter**   | [Tweet Counts Per Frequency](https://leetcode.com/problems/tweet-counts-per-frequency/)                                                                                                                                                                                                                                                                                                                                                    |

---

## ✅ Completion Checklist

- [ ] All 4 Easy problems solved
- [ ] All 9 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name the TreeMap method each problem needs before writing code
- [ ] I can draw a left and a right rotation from memory

---

**← [Lecture 40 · Advanced Graph Algorithms](../Lecture40/Assignment.md)** &nbsp;·&nbsp; **[Lecture 42 · Advanced Math & Game Theory](../Lecture42/Assignment.md) →**
