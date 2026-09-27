# 📉 Assignment 20 — Monotonic Stack & Queue

> **Lecture:** 20 of 38 — Monotonic Stack & Queue
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 4 days · **Total Problems:** 20 (5 Easy · 11 Medium · 4 Hard)
> **Goal:** Write one template for all four variants, then use it for spans, contributions, budgets and sliding windows.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                         | Pattern                 | Move                                        |
| --------------------------------------------- | ----------------------- | ------------------------------------------- |
| "next greater", "days until warmer"           | Next Greater Element    | left → right, pop while `top < current`     |
| "nearest smaller", "largest rectangle"        | Next / Previous Smaller | same loop, flip the comparison              |
| "sum over all subarrays"                      | Contribution Technique  | count the spans each element rules          |
| "lexicographically smallest after removing k" | Stack with a Budget     | pop while worse, while budget remains       |
| "maximum of every window of size k"           | Monotone Deque          | front is the answer, back is pruned         |
| "how many elements to my left are smaller"    | **Not** a stack         | that is counting — Fenwick tree, Lecture 30 |

---

## 🟢 Easy Tier (5 Problems)

_Stack mechanics first: push, pop, and what the top means._

### E1 · Remove Outermost Parentheses

**🔗 [LC 1021 — Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)** · Easy
**Pattern:** Plain Stack | **Companies:** Amazon, Adobe

**Hint:** Track the depth with a counter (a stack of one number). A `(` at depth 0 and the `)` that closes it are the outermost pair — skip those and keep everything else.

---

### E2 · Backspace String Compare

**🔗 [LC 844 — Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)** · Easy
**Pattern:** Stack Simulation | **Companies:** Meta, Amazon, Google

**Hint:** Build each string on a stack, popping on `#`. Follow-up: compare from the back with two pointers and a skip counter for O(1) space.

---

### E3 · Minimum String Length After Removing Substrings

**🔗 [LC 2696 — Minimum String Length After Removing Substrings](https://leetcode.com/problems/minimum-string-length-after-removing-substrings/)** · Easy
**Pattern:** Stack Matching | **Companies:** Amazon

**Hint:** Push characters; when the top and the current character form "AB" or "CD", pop instead of pushing. The stack's final size is the answer.

---

### E4 · Crawler Log Folder

**🔗 [LC 1598 — Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/)** · Easy
**Pattern:** Stack of Depth | **Companies:** Amazon, Microsoft

**Hint:** `"../"` pops, `"./"` does nothing, anything else pushes. Only the count matters, so a single integer works as the stack — never let it go below 0.

---

### E5 · Count Hills and Valleys in an Array

**🔗 [LC 2210 — Count Hills and Valleys in an Array](https://leetcode.com/problems/count-hills-and-valleys-in-an-array/)** · Easy
**Pattern:** Neighbour Comparison | **Companies:** Amazon

**Hint:** Collapse runs of equal values first (or skip them while scanning). Then a position is a hill or valley when it is strictly greater — or strictly smaller — than both surviving neighbours.

---

## 🟡 Medium Tier (11 Problems)

_The four variants, the contribution technique, and the budgeted stack._

### M1 · Next Greater Node In Linked List

**🔗 [LC 1019 — Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/)** · Medium
**Pattern:** Next Greater Element | **Companies:** Amazon, Google, Microsoft

**Hint:** Copy the list into an array, then run the standard template: a stack of indices, popped when a strictly greater value arrives. Whatever is left keeps the default 0.

---

### M2 · 132 Pattern

**🔗 [LC 456 — 132 Pattern](https://leetcode.com/problems/132-pattern/)** · Medium
**Pattern:** Monotonic Stack + Best Popped | **Companies:** Google, Amazon, Meta

**Hint:** Scan from the right with a decreasing stack. Popped values are valid middles, so keep the largest popped value; the pattern exists as soon as an element is smaller than it.

---

### M3 · Sum of Subarray Minimums

**🔗 [LC 907 — Sum of Subarray Minimums](https://leetcode.com/problems/sum-of-subarray-minimums/)** · Medium
**Pattern:** Contribution Technique | **Companies:** Amazon, Google, Meta

**Hint:** Find each element's previous smaller and next smaller. It is the minimum of `left × right` subarrays. Use `≥` on one side and `>` on the other so duplicates are not double-counted.

---

### M4 · Sum of Subarray Ranges

**🔗 [LC 2104 — Sum of Subarray Ranges](https://leetcode.com/problems/sum-of-subarray-ranges/)** · Medium
**Pattern:** Contribution, Twice | **Companies:** Amazon, Google

**Hint:** The answer is (sum of subarray maximums) − (sum of subarray minimums). Run the span-counting pass twice with the comparisons flipped. O(n) beats the O(n²) double loop.

---

### M5 · Maximum Width Ramp

**🔗 [LC 962 — Maximum Width Ramp](https://leetcode.com/problems/maximum-width-ramp/)** · Medium
**Pattern:** Decreasing Stack + Backward Scan | **Companies:** Amazon, Google

**Hint:** Build a decreasing stack of candidate left ends from the front. Then walk from the right, popping while `nums[stack.top()] <= nums[j]` and recording `j − stack.pop()`.

---

### M6 · Minimum Cost Tree From Leaf Values

**🔗 [LC 1130 — Minimum Cost Tree From Leaf Values](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/)** · Medium
**Pattern:** Monotonic Stack (Greedy Merge) | **Companies:** Amazon, Google

**Hint:** The cost of merging two neighbouring leaves is the product of their maxima, so repeatedly remove the smallest value between two larger ones. A decreasing stack does exactly that in one pass.

---

### M7 · Maximum Subarray Min-Product

**🔗 [LC 1856 — Maximum Subarray Min-Product](https://leetcode.com/problems/maximum-subarray-min-product/)** · Medium
**Pattern:** Contribution + Prefix Sums | **Companies:** Amazon, Google

**Hint:** For each element as the minimum, find its span with a monotonic stack, then get that span's sum from a prefix-sum array (Lecture 19). Track the best product in 64-bit.

---

### M8 · Remove Duplicate Letters

**🔗 [LC 316 — Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)** · Medium
**Pattern:** Lexicographic Stack | **Companies:** Google, Amazon, Meta

**Hint:** Count the remaining occurrences of each letter and keep an in-stack flag. Pop a bigger letter only while it still appears later, and never push a letter twice.

---

### M9 · Find the Most Competitive Subsequence

**🔗 [LC 1673 — Find the Most Competitive Subsequence](https://leetcode.com/problems/find-the-most-competitive-subsequence/)** · Medium
**Pattern:** Stack with a Budget | **Companies:** Amazon, Google, Microsoft

**Hint:** You may drop `n − k` elements. Pop while the top is larger than the current value and the budget allows, then push. Return the first `k` items.

---

### M10 · Shortest Unsorted Continuous Subarray

**🔗 [LC 581 — Shortest Unsorted Continuous Subarray](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)** · Medium
**Pattern:** Monotonic Stacks (Both Ends) | **Companies:** Amazon, Google, Meta

**Hint:** An increasing stack from the left finds the leftmost index out of order; a decreasing stack from the right finds the rightmost. Their gap is the answer. (Sorting a copy also works, in O(n log n).)

---

### M11 · Asteroid Collision

**🔗 [LC 735 — Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)** · Medium
**Pattern:** Stack Simulation | **Companies:** Amazon, Google, Meta

**Hint:** Only a right-moving asteroid followed by a left-moving one collides. Push, and while the top is positive and the current is negative, resolve: pop, destroy, or stop.

---

## 🔴 Hard Tier (4 Problems)

_Monotonic structures combined with DP, prefix sums, or a second scan._

### H1 · Number of Visible People in a Queue

**🔗 [LC 1944 — Number of Visible People in a Queue](https://leetcode.com/problems/number-of-visible-people-in-a-queue/)** · Hard
**Pattern:** Monotonic Stack (Count Pops) | **Companies:** Google, Amazon

**Hint:** Scan from the right with a decreasing stack. Each person sees everyone they pop, plus one more if the stack is not empty afterwards (the first taller person).

---

### H2 · Constrained Subsequence Sum

**🔗 [LC 1425 — Constrained Subsequence Sum](https://leetcode.com/problems/constrained-subsequence-sum/)** · Hard
**Pattern:** Monotone Deque over DP | **Companies:** Google, Amazon, Meta

**Hint:** `dp[i] = nums[i] + max(0, best dp in the previous k)`. Keep that window maximum in a deque keyed on `dp`, expiring by index. O(n) instead of O(n·k).

---

### H3 · Maximum Score of a Good Subarray

**🔗 [LC 1793 — Maximum Score of a Good Subarray](https://leetcode.com/problems/maximum-score-of-a-good-subarray/)** · Hard
**Pattern:** Two Pointers or Monotonic Stack | **Companies:** Google, Amazon

**Hint:** Start at `k` and expand greedily to whichever side has the larger neighbour, tracking the running minimum × width. The stack version computes each element's span and keeps the spans that cover `k`.

---

### H4 · Max Value of Equation

**🔗 [LC 1499 — Max Value of Equation](https://leetcode.com/problems/max-value-of-equation/)** · Hard
**Pattern:** Monotone Deque | **Companies:** Google, Amazon

**Hint:** For `i < j` the expression is `(y_i − x_i) + (x_j + y_j)`. Keep a deque of `y − x` that expires by x-distance, so each `j` reads its best partner in O(1).

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Amortised cost:** The template has a loop inside a loop. Explain why it still runs in O(n).
2. **Indices vs values:** Why does the stack hold indices? Give a problem that cannot be solved if it holds values.
3. **Direction:** You want the previous greater element but may only loop left to right. How do you get it?
4. **Duplicates:** In the contribution technique, what exactly goes wrong if both sides use `>`? Give a small input.
5. **The budget:** In Remove Duplicate Letters, what stops the stack from popping a letter it will need? What plays the same role in Remove K Digits?
6. **Deque vs heap:** Both can give a window maximum. State the cost of each and the condition that makes the deque valid.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Number of Visible People in a Queue](https://leetcode.com/problems/number-of-visible-people-in-a-queue/), [Constrained Subsequence Sum](https://leetcode.com/problems/constrained-subsequence-sum/), [Maximum Score of a Good Subarray](https://leetcode.com/problems/maximum-score-of-a-good-subarray/), [Max Value of Equation](https://leetcode.com/problems/max-value-of-equation/) |
| **Google**    | [Number of Visible People in a Queue](https://leetcode.com/problems/number-of-visible-people-in-a-queue/), [Constrained Subsequence Sum](https://leetcode.com/problems/constrained-subsequence-sum/), [Maximum Score of a Good Subarray](https://leetcode.com/problems/maximum-score-of-a-good-subarray/), [Max Value of Equation](https://leetcode.com/problems/max-value-of-equation/) |
| **Meta**      | [Constrained Subsequence Sum](https://leetcode.com/problems/constrained-subsequence-sum/), [132 Pattern](https://leetcode.com/problems/132-pattern/), [Sum of Subarray Minimums](https://leetcode.com/problems/sum-of-subarray-minimums/), [Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)                                                           |
| **Microsoft** | [Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/), [Find the Most Competitive Subsequence](https://leetcode.com/problems/find-the-most-competitive-subsequence/), [Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/)                                                                                              |
| **Adobe**     | [Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)                                                                                                                                                                                                                                                                                              |

---

## ✅ Completion Checklist

- [ ] All 5 Easy problems solved
- [ ] All 11 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write the four variants by changing only the loop direction and the comparison
- [ ] I can derive `left × right` for the contribution technique without looking it up

---

**← [Lecture 19 · Prefix Sums & Difference Arrays](../Lecture19/Assignment.md)** &nbsp;·&nbsp; **[Lecture 21 · Intervals & Sweep Line](../Lecture21/Assignment.md) →**
