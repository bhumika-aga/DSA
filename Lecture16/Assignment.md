# ⛰️ Assignment 16 — Heaps & Priority Queues

> **Lecture:** 16 of 38 — Heaps & Priority Queues
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 5 days · **Total Problems:** 20 (5 Easy · 10 Medium · 5 Hard)
> **Goal:** Master the 5 heap patterns — Single Heap, Top-K, Two Heaps, K-way Merge, Greedy Heap.

---

## 🗺️ Pattern Recognition — Read Before Starting

| Signal Phrase                              | Pattern        | Tool                         |
| ------------------------------------------ | -------------- | ---------------------------- |
| "Kth largest/smallest", "running max/min"  | Single Heap    | Min/max-heap of size K       |
| "top K frequent", "K closest", "K largest" | Top K Elements | Size-K min-heap              |
| "median", "sliding window median"          | Two Heaps      | maxH (lower) + minH (upper)  |
| "merge K sorted", "smallest from K lists"  | K-way Merge    | Min-heap with (val, listIdx) |
| "schedule", "cooldown", "reorganize"       | Greedy Heap    | Max-heap + wait queue        |

---

---

## 🟢 Easy Tier (5 Problems)

### E1 · Kth Largest Element in a Stream

**🔗 [LC 703 — Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/)** · Easy
**Pattern:** Single Min-Heap | **Companies:** Amazon, Google

**Hint:** Maintain a min-heap of size k. On each `add(val)`, offer val, poll if size > k. Return `heap.peek()`. Same as Kth Largest in Array but online.

---

### E2 · Last Stone Weight

**🔗 [LC 1046 — Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)** · Easy
**Pattern:** Max-Heap | **Companies:** Amazon

**Hint:** Push all stones into a max-heap. Each round: poll two heaviest, push back `|y - x|` if not equal. Return remaining stone (or 0).

---

### E3 · Relative Ranks

**🔗 [LC 506 — Relative Ranks](https://leetcode.com/problems/relative-ranks/)** · Easy
**Pattern:** Max-Heap | **Companies:** Google

**Hint:** Push `(score, index)` into a max-heap. Poll in order: first gets "Gold Medal", second "Silver Medal", third "Bronze Medal", rest get their rank number.

---

### E4 · Take Gifts From the Richest Pile

**🔗 [LC 2558 — Take Gifts From the Richest Pile](https://leetcode.com/problems/take-gifts-from-the-richest-pile/)** · Easy
**Pattern:** Max-Heap Simulation | **Companies:** Amazon

**Hint:** Put every pile in a max-heap. `k` times: pop the largest, push back `floor(sqrt(x))`. Sum what's left (as `long`). O((n + k) log n).

---

### E5 · Sort Characters By Frequency

**🔗 [LC 451 — Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)** · Medium
**Pattern:** Max-Heap | **Companies:** Amazon, Google

**Hint:** Count frequencies, push into max-heap. Poll in descending frequency order, append `freq` copies of the character to result.

---

## 🟡 Medium Tier (10 Problems)

_Core Interview Patterns._

### M1 · Kth Largest Element in an Array

**🔗 [LC 215 — Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)** · Medium
**Pattern:** Single Min-Heap | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Size-K min-heap. Offer each element; if size > K, poll. Return peek. Alternative: QuickSelect O(n) average.

---

### M2 · Top K Frequent Elements

**🔗 [LC 347 — Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)** · Medium
**Pattern:** Top K | **Companies:** Amazon, Google, Facebook

**Hint:** HashMap for frequencies + size-K min-heap sorted by frequency. Alternative: bucket sort in O(n).

---

### M3 · K Closest Points to Origin

**🔗 [LC 973 — K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)** · Medium
**Pattern:** Top K | **Companies:** Amazon, Google, Facebook, Uber

**Hint:** Max-heap of size K by squared distance. If new point is closer than farthest in heap, swap. Use squared distance (avoid sqrt). Return heap contents.

---

### M4 · The K Weakest Rows in a Matrix

**🔗 [LC 1337 — The K Weakest Rows in a Matrix](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)** · Easy
**Pattern:** K-way Merge / Min-Heap | **Companies:** Amazon, Google

**Hint (Sort K-sorted array):** Elements are at most K positions from their sorted position. Use a min-heap of size K+1. Slide window: offer next element, poll minimum into result.

---

### M5 · Find K Pairs with Smallest Sums

**🔗 [LC 373 — Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)** · Medium
**Pattern:** K-way Merge | **Companies:** Google, Amazon

**Hint:** Push `(nums1[0]+nums2[j], 0, j)` for all j=0..k-1 into min-heap. Each poll: output pair, push `(nums1[i+1]+nums2[j], i+1, j)` to continue that "row".

---

### M6 · Reorganize String

**🔗 [LC 767 — Reorganize String](https://leetcode.com/problems/reorganize-string/)** · Medium
**Pattern:** Greedy Heap | **Companies:** Google, Amazon, Facebook

**Hint:** Max-heap by frequency. Each round: poll two most frequent chars, append both, decrement. If only one char left and its count > 1 → impossible (return "").

---

### M7 · Task Scheduler

**🔗 [LC 621 — Task Scheduler](https://leetcode.com/problems/task-scheduler/)** · Medium
**Pattern:** Greedy Heap | **Companies:** Amazon, Facebook, Uber

**Hint:** Max-heap + wait queue `[(remaining, available_at)]`. At each tick: if heap non-empty do the most frequent task. Enqueue to wait with `time + n`. Recheck wait queue each tick.

**Math shortcut:** `max(tasks.length, (maxFreq-1)*(n+1) + countOfMaxFreq)`

---

### M8 · Super Ugly Number

**🔗 [LC 313 — Super Ugly Number](https://leetcode.com/problems/super-ugly-number/)** · Medium
**Pattern:** K-Way Merge with a Heap | **Companies:** Google, Amazon

**Hint:** Same idea as Ugly Number II with k pointers. Push `(primes[j], j, index 0)` into a min-heap; pop the smallest, append it if it's new, and push `primes[j] × ugly[index + 1]`. Skip duplicates when popping.

---

### M9 · Maximum Subsequence Score

**🔗 [LC 2542 — Maximum Subsequence Score](https://leetcode.com/problems/maximum-subsequence-score/)** · Medium
**Pattern:** Greedy + Min-Heap | **Companies:** Google

**Hint:** Sort pairs by nums2 descending. Maintain a min-heap of size k for nums1 values. At each step: track sum of top-k nums1 values. Score = sum \* nums2[i]. Update global max.

---

### M10 · Design Twitter

**🔗 [LC 355 — Design Twitter](https://leetcode.com/problems/design-twitter/)** · Medium
**Pattern:** K-way Merge | **Companies:** Amazon, Twitter

**Hint:** Each user has a tweet list. `getNewsFeed` merges the 10 most recent tweets from the user and all followees using a max-heap (by timestamp). Classic K-way merge with K = number of followees + 1.

---

## 🔴 Hard Tier (5 Problems)

_FAANG Mastery._

### H1 · Find Median from Data Stream

**🔗 [LC 295 — Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)** · Hard
**Pattern:** Two Heaps | **Companies:** Amazon, Google, Microsoft, Apple

**Hint:** maxH (lower half) + minH (upper half). Always push to maxH first, then shuttle max-of-lower to minH. Rebalance if minH grows larger. Median at root(s).

**Why Hard?** Maintaining the invariant `maxH.peek() ≤ minH.peek()` after every insert requires careful two-step push. Off-by-one on rebalancing is the classic bug.

---

### H2 · Sliding Window Median

**🔗 [LC 480 — Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)** · Hard
**Pattern:** Two Heaps + Lazy Deletion | **Companies:** Google, Amazon

**Hint:** Same Two Heaps as LC 295 but must support removal of the element sliding out of the window. Use lazy deletion: a HashMap tracks "cancelled" elements; skip them when they reach the top of the heap during balance checks.

**Why Hard?** Lazy deletion with rebalancing while keeping `maxH.peek() ≤ minH.peek()` after both insert and delete is tricky.

---

### H3 · Merge k Sorted Lists

**🔗 [LC 23 — Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)** · Hard
**Pattern:** K-way Merge | **Companies:** Amazon, Google, Microsoft, Facebook

**Hint:** Push all K heads. Poll minimum, add to result, push its next. O(N log K).

**Why Hard (conceptually):** The O(N log K) vs naive O(NK) distinction and handling null nodes cleanly is what interviewers focus on. Follow-up: what if K = 10^5?

---

### H4 · Smallest Range Covering Elements from K Lists

**🔗 [LC 632 — Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/)** · Hard
**Pattern:** K-way Merge + Sliding Window | **Companies:** Google, Amazon

**Hint:** Push `(val, listIdx, elemIdx)` for all `list[i][0]` into min-heap. Track current max across all heap elements. Range = `[minHeap.peek(), curMax]`. Slide: poll min, push next from same list. Update range if smaller. Stop when any list is exhausted.

---

### H5 · IPO

**🔗 [LC 502 — IPO](https://leetcode.com/problems/ipo/)** · Hard
**Pattern:** Two Heaps (Greedy) | **Companies:** Google, Amazon, Microsoft

**Hint:** Sort projects by capital required. Min-heap of `(capital, profit)` for available projects. Max-heap of `profit` for projects you can afford. At each of k rounds: unlock all projects with `capital ≤ w` into profit max-heap. Pick the most profitable one, add profit to `w`.

**Why Hard?** Combining sorted order, two different heaps, and greedy reasoning in one problem.

---

## 🧠 Conceptual Check

1. **Build heap:** Why is `buildHeap` O(n) when inserting n elements one-by-one is O(n log n)? Where does the O(n) proof break the intuition?

2. **Top-K counterintuitive:** You want the K _largest_ elements but you use a _min_-heap. Explain why. What happens if you use a max-heap instead?

3. **Two Heaps invariant:** In `addNum`, why do we always push to maxH first (even if the number is larger than minH.peek())? What does the cross-push enforce?

4. **K-way merge complexity:** Merging K lists with N total elements takes O(N log K). Why K in the log and not N? What is the heap size at any point?

5. **Lazy deletion:** In Sliding Window Median, when an element slides out, you can't remove it from the middle of a heap in O(log n) without a custom structure. What does lazy deletion do instead?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                 |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/), [Sliding Window Median](https://leetcode.com/problems/sliding-window-median/), [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/), [Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/) |
| **Google**    | [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/), [Sliding Window Median](https://leetcode.com/problems/sliding-window-median/), [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/), [Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/) |
| **Facebook**  | [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/), [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/), [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/), [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)                             |
| **Microsoft** | [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/), [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/), [IPO](https://leetcode.com/problems/ipo/), [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)                                                                 |
| **Uber**      | [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/), [Task Scheduler](https://leetcode.com/problems/task-scheduler/)                                                                                                                                                                                                                               |

---

## ✅ Completion Checklist

- [ ] All 5 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] All 5 conceptual questions answered out loud
- [ ] Can write the Two Heaps `addNum`/`findMedian` from memory
- [ ] Can write K-way Merge for linked lists from memory
- [ ] Can implement a custom PriorityQueue comparator for any object type
- [ ] Know when to use min-heap vs max-heap for Top-K without hesitation

---

**← [Lecture 15 · Trees (Binary Trees & BST)](../Lecture15/Assignment.md)** &nbsp;·&nbsp; **[Lecture 17 · Graphs](../Lecture17/Assignment.md) →**
