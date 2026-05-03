# ⛰️ Assignment 16 — Heaps & Priority Queues

> **Lecture:** Topic 16 — Heaps & Priority Queues
> **Phase:** 2 — Core Data Structures · **Topic:** 16 of 30
> **Estimated Time:** 5 Days · **Total Problems:** 20 (5 Easy · 10 Medium · 5 Hard)
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

## 🟢 Easy Tier (5 Problems)

---

### E1 · Kth Largest Element in a Stream

**🔗 [LC 703](https://leetcode.com/problems/kth-largest-element-in-a-stream/)**
**Pattern:** Single Min-Heap | **Companies:** Amazon, Google

**Hint:** Maintain a min-heap of size k. On each `add(val)`, offer val, poll if size > k. Return `heap.peek()`. Same as Kth Largest in Array but online.

---

### E2 · Last Stone Weight

**🔗 [LC 1046](https://leetcode.com/problems/last-stone-weight/)**
**Pattern:** Max-Heap | **Companies:** Amazon

**Hint:** Push all stones into a max-heap. Each round: poll two heaviest, push back `|y - x|` if not equal. Return remaining stone (or 0).

---

### E3 · Relative Ranks

**🔗 [LC 506](https://leetcode.com/problems/relative-ranks/)**
**Pattern:** Max-Heap | **Companies:** Google

**Hint:** Push `(score, index)` into a max-heap. Poll in order: first gets "Gold Medal", second "Silver Medal", third "Bronze Medal", rest get their rank number.

---

### E4 · Minimum Cost to Connect Sticks

**🔗 [LC 1167](https://leetcode.com/problems/minimum-cost-to-connect-sticks/)**
**Pattern:** Min-Heap (Greedy) | **Companies:** Amazon

**Hint:** Always combine the two smallest sticks (greedy). Use a min-heap. Each round: poll two, push their sum, add sum to total cost. Repeat until one stick remains.

---

### E5 · Sort Characters By Frequency

**🔗 [LC 451](https://leetcode.com/problems/sort-characters-by-frequency/)**
**Pattern:** Max-Heap | **Companies:** Amazon, Google

**Hint:** Count frequencies, push into max-heap. Poll in descending frequency order, append `freq` copies of the character to result.

---

## 🟡 Medium Tier — Core Interview Patterns (10 Problems)

---

### M1 · Kth Largest Element in an Array ⭐

**🔗 [LC 215](https://leetcode.com/problems/kth-largest-element-in-an-array/)**
**Pattern:** Single Min-Heap | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Size-K min-heap. Offer each element; if size > K, poll. Return peek. Alternative: QuickSelect O(n) average.

---

### M2 · Top K Frequent Elements ⭐

**🔗 [LC 347](https://leetcode.com/problems/top-k-frequent-elements/)**
**Pattern:** Top K | **Companies:** Amazon, Google, Facebook

**Hint:** HashMap for frequencies + size-K min-heap sorted by frequency. Alternative: bucket sort in O(n).

---

### M3 · K Closest Points to Origin ⭐

**🔗 [LC 973](https://leetcode.com/problems/k-closest-points-to-origin/)**
**Pattern:** Top K | **Companies:** Amazon, Google, Facebook, Uber

**Hint:** Max-heap of size K by squared distance. If new point is closer than farthest in heap, swap. Use squared distance (avoid sqrt). Return heap contents.

---

### M4 · Sort K Sorted Array

**🔗 [LC 1337 variant](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)**
**Pattern:** K-way Merge / Min-Heap | **Companies:** Amazon, Google

**Hint (Sort K-sorted array):** Elements are at most K positions from their sorted position. Use a min-heap of size K+1. Slide window: offer next element, poll minimum into result.

---

### M5 · Find K Pairs with Smallest Sums

**🔗 [LC 373](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)**
**Pattern:** K-way Merge | **Companies:** Google, Amazon

**Hint:** Push `(nums1[0]+nums2[j], 0, j)` for all j=0..k-1 into min-heap. Each poll: output pair, push `(nums1[i+1]+nums2[j], i+1, j)` to continue that "row".

---

### M6 · Reorganize String

**🔗 [LC 767](https://leetcode.com/problems/reorganize-string/)**
**Pattern:** Greedy Heap | **Companies:** Google, Amazon, Facebook

**Hint:** Max-heap by frequency. Each round: poll two most frequent chars, append both, decrement. If only one char left and its count > 1 → impossible (return "").

---

### M7 · Task Scheduler ⭐

**🔗 [LC 621](https://leetcode.com/problems/task-scheduler/)**
**Pattern:** Greedy Heap | **Companies:** Amazon, Facebook, Uber

**Hint:** Max-heap + wait queue `[(remaining, available_at)]`. At each tick: if heap non-empty do the most frequent task. Enqueue to wait with `time + n`. Recheck wait queue each tick.

**Math shortcut:** `max(tasks.length, (maxFreq-1)*(n+1) + countOfMaxFreq)`

---

### M8 · Ugly Number II

**🔗 [LC 264](https://leetcode.com/problems/ugly-number-ii/)**
**Pattern:** Min-Heap + Set (dedup) | **Companies:** Google, Amazon

**Hint:** Start with 1. Each round: poll min, multiply by 2, 3, 5 and push if not seen. Use HashSet to avoid duplicates. After n polls the answer is found.

---

### M9 · Maximum Subsequence Score

**🔗 [LC 2542](https://leetcode.com/problems/maximum-subsequence-score/)**
**Pattern:** Greedy + Min-Heap | **Companies:** Google

**Hint:** Sort pairs by nums2 descending. Maintain a min-heap of size k for nums1 values. At each step: track sum of top-k nums1 values. Score = sum \* nums2[i]. Update global max.

---

### M10 · Design Twitter

**🔗 [LC 355](https://leetcode.com/problems/design-twitter/)**
**Pattern:** K-way Merge | **Companies:** Amazon, Twitter

**Hint:** Each user has a tweet list. `getNewsFeed` merges the 10 most recent tweets from the user and all followees using a max-heap (by timestamp). Classic K-way merge with K = number of followees + 1.

---

## 🔴 Hard Tier — FAANG Mastery (5 Problems)

---

### H1 · Find Median from Data Stream ⭐

**🔗 [LC 295](https://leetcode.com/problems/find-median-from-data-stream/)**
**Pattern:** Two Heaps | **Companies:** Amazon, Google, Microsoft, Apple

**Hint:** maxH (lower half) + minH (upper half). Always push to maxH first, then shuttle max-of-lower to minH. Rebalance if minH grows larger. Median at root(s).

**Why Hard?** Maintaining the invariant `maxH.peek() ≤ minH.peek()` after every insert requires careful two-step push. Off-by-one on rebalancing is the classic bug.

---

### H2 · Sliding Window Median

**🔗 [LC 480](https://leetcode.com/problems/sliding-window-median/)**
**Pattern:** Two Heaps + Lazy Deletion | **Companies:** Google, Amazon

**Hint:** Same Two Heaps as LC 295 but must support removal of the element sliding out of the window. Use lazy deletion: a HashMap tracks "cancelled" elements; skip them when they reach the top of the heap during balance checks.

**Why Hard?** Lazy deletion with rebalancing while keeping `maxH.peek() ≤ minH.peek()` after both insert and delete is tricky.

---

### H3 · Merge K Sorted Lists ⭐

**🔗 [LC 23](https://leetcode.com/problems/merge-k-sorted-lists/)**
**Pattern:** K-way Merge | **Companies:** Amazon, Google, Microsoft, Facebook

**Hint:** Push all K heads. Poll minimum, add to result, push its next. O(N log K).

**Why Hard (conceptually):** The O(N log K) vs naive O(NK) distinction and handling null nodes cleanly is what interviewers focus on. Follow-up: what if K = 10^5?

---

### H4 · Smallest Range Covering Elements from K Lists

**🔗 [LC 632](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/)**
**Pattern:** K-way Merge + Sliding Window | **Companies:** Google, Amazon

**Hint:** Push `(val, listIdx, elemIdx)` for all `list[i][0]` into min-heap. Track current max across all heap elements. Range = `[minHeap.peek(), curMax]`. Slide: poll min, push next from same list. Update range if smaller. Stop when any list is exhausted.

---

### H5 · IPO (Maximize Capital)

**🔗 [LC 502](https://leetcode.com/problems/ipo/)**
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

## 🏢 Company Focus Table

| Company       | Must-Know Problems                                                                         |
| ------------- | ------------------------------------------------------------------------------------------ |
| **Amazon**    | Kth Largest (LC 215), Merge K Lists (LC 23), Task Scheduler (LC 621), Find Median (LC 295) |
| **Google**    | K Closest Points (LC 973), Find K Pairs (LC 373), Smallest Range (LC 632), IPO (LC 502)    |
| **Microsoft** | Find Median (LC 295), Merge K Lists (LC 23), Top K Frequent (LC 347)                       |
| **Facebook**  | K Closest (LC 973), Merge K Lists (LC 23), Reorganize String (LC 767)                      |

---

## ✅ Completion Checklist

- [ ] Completed all 5 Easy problems
- [ ] Completed all 10 Medium problems
- [ ] Attempted all 5 Hard problems
- [ ] Can answer all 5 Conceptual Check questions verbally
- [ ] Can write the Two Heaps `addNum`/`findMedian` from memory
- [ ] Can write K-way Merge for linked lists from memory
- [ ] Can implement a custom PriorityQueue comparator for any object type
- [ ] Know when to use min-heap vs max-heap for Top-K without hesitation

---

**← Topic 15: Trees & BST** &nbsp;&nbsp;|&nbsp;&nbsp; **Topic 17: Graphs →**
