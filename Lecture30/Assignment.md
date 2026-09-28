# 🔍 Assignment 23 — Divide & Conquer

> **Lecture:** 30 of 45 — Divide & Conquer
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 4 days · **Total Problems:** 18 (4 Easy · 10 Medium · 4 Hard)
> **Goal:** Find the split point, keep the combine cheap, and read the running time straight off the recurrence.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                             | Pattern               | Move                                      |
| ------------------------------------------------- | --------------------- | ----------------------------------------- |
| "the answer for a range from its halves"          | Divide & Conquer      | split at the middle, combine the results  |
| "kth largest / smallest", no full order needed    | QuickSelect           | partition, recurse into one side only     |
| "count pairs i < j with a comparison"             | Merge Sort Counting   | count in bulk while the halves are sorted |
| "all possible ways to group / build"              | Split at Every Choice | recurse on both sides, combine every pair |
| a character or value that cannot be in the answer | Split at the Obstacle | solve the pieces between the obstacles    |
| subproblems that repeat                           | **Not** plain D&C     | memoise — that is DP, Phase 4             |

---

## 🟢 Easy Tier (4 Problems)

_Tree recursion, where the split is handed to you._

### E1 · Root Equals Sum of Children

**🔗 [LC 2236 — Root Equals Sum of Children](https://leetcode.com/problems/root-equals-sum-of-children/)** · Easy
**Pattern:** Divide on the Root | **Companies:** Amazon

**Hint:** One comparison, no recursion needed: the root's value against the sum of its two children. The smallest possible divide-and-conquer base case.

---

### E2 · Evaluate Boolean Binary Tree

**🔗 [LC 2331 — Evaluate Boolean Binary Tree](https://leetcode.com/problems/evaluate-boolean-binary-tree/)** · Easy
**Pattern:** Post-order Evaluation | **Companies:** Amazon, Google

**Hint:** Leaves return their own value; an internal node combines its two children with AND or OR. Children must be evaluated before the node — that is post-order.

---

### E3 · Sum of Left Leaves

**🔗 [LC 404 — Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/)** · Easy
**Pattern:** Divide on the Root | **Companies:** Amazon, Adobe

**Hint:** Recurse on both children, but a left child that is a leaf contributes its value instead of recursing. Pass down whether this node is a left child.

---

### E4 · Subtree of Another Tree

**🔗 [LC 572 — Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)** · Easy
**Pattern:** Two Recursions | **Companies:** Amazon, Google, Meta

**Hint:** Write `isSame(a, b)` first, then: this node matches, or the left subtree contains it, or the right one does.

---

## 🟡 Medium Tier (10 Problems)

_Splits you have to invent: operators, obstacles, parities and roots._

### M1 · Different Ways to Add Parentheses

**🔗 [LC 241 — Different Ways to Add Parentheses](https://leetcode.com/problems/different-ways-to-add-parentheses/)** · Medium
**Pattern:** Split the Expression | **Companies:** Google, Amazon, Meta

**Hint:** Each operator is the one applied last. Recurse on both sides, then combine every left result with every right result. Memoise on the substring.

---

### M2 · Longest Substring with At Least K Repeating Characters

**🔗 [LC 395 — Longest Substring with At Least K Repeating Characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)** · Medium
**Pattern:** Divide on the Impossible | **Companies:** Google, Amazon, Meta

**Hint:** Any character appearing fewer than k times in the whole string cannot be in the answer, so split there and solve each piece.

---

### M3 · Beautiful Array

**🔗 [LC 932 — Beautiful Array](https://leetcode.com/problems/beautiful-array/)** · Medium
**Pattern:** Construct by Parity | **Companies:** Google, Amazon

**Hint:** If A is beautiful, so are `2A − 1` and `2A`. Build the odd half and the even half recursively and concatenate — odd plus even is odd, so no middle element breaks it.

---

### M4 · Maximum Binary Tree

**🔗 [LC 654 — Maximum Binary Tree](https://leetcode.com/problems/maximum-binary-tree/)** · Medium
**Pattern:** Split at the Maximum | **Companies:** Amazon, Google

**Hint:** The largest value is the root; everything left of it forms the left subtree, everything right the right subtree. Recurse on both ranges.

---

### M5 · Balance a Binary Search Tree

**🔗 [LC 1382 — Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/)** · Medium
**Pattern:** Split at the Middle | **Companies:** Amazon, Google

**Hint:** In-order traversal gives sorted values. Rebuild by taking the middle as the root and recursing on both halves — the same construction as sorted-array-to-BST.

---

### M6 · Unique Binary Search Trees II

**🔗 [LC 95 — Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/)** · Medium
**Pattern:** Split by the Root | **Companies:** Google, Amazon, Meta

**Hint:** For each value as root, recursively build all left subtrees from the smaller values and all right subtrees from the larger, then pair every left with every right.

---

### M7 · All Possible Full Binary Trees

**🔗 [LC 894 — All Possible Full Binary Trees](https://leetcode.com/problems/all-possible-full-binary-trees/)** · Medium
**Pattern:** Split by Left Size | **Companies:** Google, Amazon

**Hint:** A full binary tree has an odd number of nodes. For each odd split of `n − 1` into left and right, combine every left tree with every right tree. Memoise on n.

---

### M8 · Distribute Coins in Binary Tree

**🔗 [LC 979 — Distribute Coins in Binary Tree](https://leetcode.com/problems/distribute-coins-in-binary-tree/)** · Medium
**Pattern:** Post-order with a Balance | **Companies:** Google, Amazon

**Hint:** Each subtree returns its surplus or deficit of coins. The moves along an edge equal the absolute value of what flows through it — sum those as you return.

---

### M9 · Construct Quad Tree

**🔗 [LC 427 — Construct Quad Tree](https://leetcode.com/problems/construct-quad-tree/)** · Medium
**Pattern:** Split into Four | **Companies:** Google, Amazon

**Hint:** If the square is uniform, it is a leaf. Otherwise split into four quadrants, recurse, and merge back into one leaf when all four children are identical leaves.

---

### M10 · Global and Local Inversions

**🔗 [LC 775 — Global and Local Inversions](https://leetcode.com/problems/global-and-local-inversions/)** · Medium
**Pattern:** Compare with the Sorted Order | **Companies:** Google, Amazon

**Hint:** Local inversions are a subset of global ones, so the answer is true exactly when every global inversion is local — check that no `nums[i]` exceeds the running minimum from two positions ahead.

---

## 🔴 Hard Tier (4 Problems)

_Divide and conquer carrying a counting argument._

### H1 · Number of Pairs Satisfying Inequality

**🔗 [LC 2426 — Number of Pairs Satisfying Inequality](https://leetcode.com/problems/number-of-pairs-satisfying-inequality/)** · Hard
**Pattern:** Merge Sort Counting | **Companies:** Google, Amazon

**Hint:** Rewrite as `d[i] = nums1[i] − nums2[i]`, so the condition becomes `d[i] ≤ d[j] + diff`. Count qualifying pairs during the merge with a forward pointer.

---

### H2 · Number of Ways to Reorder Array to Get Same BST

**🔗 [LC 1569 — Number of Ways to Reorder Array to Get Same BST](https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/)** · Hard
**Pattern:** Split by the Root | **Companies:** Google, Amazon

**Hint:** The first value is the root. Any interleaving of the two sides builds the same tree, so multiply `C(l + r, l)` by the ways for each side, and subtract one at the end.

---

### H3 · Count Good Triplets in an Array

**🔗 [LC 2179 — Count Good Triplets in an Array](https://leetcode.com/problems/count-good-triplets-in-an-array/)** · Hard
**Pattern:** Two Merge Passes (or a BIT) | **Companies:** Google, Amazon

**Hint:** Map values to their positions in `nums2`. For each middle element, count how many smaller values precede it and how many larger follow, then multiply. A Fenwick tree does the counting.

---

### H4 · Create Sorted Array through Instructions

**🔗 [LC 1649 — Create Sorted Array through Instructions](https://leetcode.com/problems/create-sorted-array-through-instructions/)** · Hard
**Pattern:** Counting Structure | **Companies:** Google, Amazon

**Hint:** For each instruction, count elements strictly smaller and strictly larger among those already inserted. A Fenwick tree over the value range gives both in O(log n) — the same counting a merge sort does offline.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — T(n) = 2T(n/2) + O(n)

// Snippet 2 — T(n) = T(n/2) + O(1)

// Snippet 3 — T(n) = 2T(n/2) + O(1)

// Snippet 4 — T(n) = T(n/2) + O(n)

// Snippet 5 — quickselect, average case

// Snippet 6 — counting inversions during merge sort
```

**Complexity Answers:**

1. **O(n log n)** — merge sort.
2. **O(log n)** — binary search.
3. **O(n)** — a tree traversal.
4. **O(n)** — n + n/2 + n/4 + … ≤ 2n.
5. **O(n)** average, O(n²) worst.
6. **O(n log n)**.

---

## 🔍 Self-Assessment — True / False

1. Divide and conquer always splits the input exactly in half. → **False** — it can split unevenly, or into more than two parts
2. Quickselect finds the k-th smallest in O(n) on average. → **True**
3. T(n) = 2T(n/2) + O(n) solves to O(n log n). → **True** — log n levels, O(n) work per level
4. Divide and conquer is the same as dynamic programming. → **False** — DP reuses overlapping subproblems; D&C subproblems are independent
5. Counting inversions with merge sort is O(n log n). → **True**
6. Every divide-and-conquer algorithm is faster than brute force. → **False** — it depends on the cost of dividing and combining

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Master Theorem:** Solve `T(n) = 2T(n/2) + O(n)` and `T(n) = T(n/2) + O(n)`. Why are the answers different?
2. **QuickSelect:** Why is the average case O(n) rather than O(n log n), and what makes the worst case O(n²)?
3. **Counting:** In inversion counting, why must the counting happen before the merge step rather than after?
4. **D&C vs DP:** Both split problems. State the property that decides which one applies.
5. **Base cases:** Give an example of a split that fails to shrink the problem, and say what happens when you run it.
6. **Combine cost:** If combining two halves took O(n²), would divide and conquer still help? Work it out with the Master Theorem.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon** | [Root Equals Sum of Children](https://leetcode.com/problems/root-equals-sum-of-children/), [Count Good Triplets in an Array](https://leetcode.com/problems/count-good-triplets-in-an-array/), [Create Sorted Array through Instructions](https://leetcode.com/problems/create-sorted-array-through-instructions/), [Number of Pairs Satisfying Inequality](https://leetcode.com/problems/number-of-pairs-satisfying-inequality/)         |
| **Google** | [Number of Ways to Reorder Array to Get Same BST](https://leetcode.com/problems/number-of-ways-to-reorder-array-to-get-same-bst/), [All Possible Full Binary Trees](https://leetcode.com/problems/all-possible-full-binary-trees/), [Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/), [Beautiful Array](https://leetcode.com/problems/beautiful-array/)                                       |
| **Meta**   | [Different Ways to Add Parentheses](https://leetcode.com/problems/different-ways-to-add-parentheses/), [Longest Substring with At Least K Repeating Characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/), [Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/), [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/) |
| **Adobe**  | [Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/)                                                                                                                                                                                                                                                                                                                                                                  |

---

## ✅ Completion Checklist

- [ ] All 4 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name the split point of any divide-and-conquer problem before coding it
- [ ] I can add a counting line to a merge sort without changing its complexity

---

**← [Lecture 29 · Greedy Algorithms](../Lecture29/Assignment.md)** &nbsp;·&nbsp; **[Lecture 31 · Union-Find (Disjoint Set Union)](../Lecture31/Assignment.md) →**
