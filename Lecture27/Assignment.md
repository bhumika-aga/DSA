# 📉 Assignment 27 — Monotonic Stack & Queue

> **Lecture:** 27 of 45 — Monotonic Stack & Queue
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 5 days · **Total Problems:** 29 (5 Easy · 16 Medium · 8 Hard)
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
| "how many elements to my left are smaller"    | **Not** a stack         | that is counting — Fenwick tree, Lecture 37 |

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

## 🟡 Medium Tier (16 Problems)

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

**Hint:** For each element as the minimum, find its span with a monotonic stack, then get that span's sum from a prefix-sum array (Lecture 26). Track the best product in 64-bit.

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

### M12 · Next Greater Element II

**🔗 [LC 503 — Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)** · Medium
**Pattern:** Monotonic Stack | **Companies:** Amazon, Google, Meta

**Hint:** Loop over indices `0..2n-1`, using `nums[i % n]`, with a decreasing stack of indices. Pop and assign answers while the current value is larger; only push during the first pass.

---

### M13 · Online Stock Span

**🔗 [LC 901 — Online Stock Span](https://leetcode.com/problems/online-stock-span/)** · Medium
**Pattern:** Monotonic Decreasing Stack | **Companies:** Amazon, Google, Bloomberg

**Hint:** Keep a stack of `(price, span)`. For a new price, pop every entry with price `<=` it and add its span to the current span (starting at 1), then push. Amortised O(1).

---

### M14 · Remove K Digits

**🔗 [LC 402 — Remove K Digits](https://leetcode.com/problems/remove-k-digits/)** · Medium
**Pattern:** Greedy + Stack | **Companies:** Google, Amazon, Meta

**Hint:** Build an increasing stack of digits: while `k > 0` and the top is greater than the current digit, pop and decrement `k`. Push the digit. Remove any remaining `k` from the end, strip leading zeros, and return "0" if nothing is left.

---

### M15 · Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit

**🔗 [LC 1438 — Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/)** · Medium
**Pattern:** Two Monotonic Deques | **Companies:** Google, Amazon, Uber

**Hint:** Keep a decreasing deque for the window max and an increasing deque for the window min. Expand right; while `max - min > limit`, move left and pop expired fronts. O(n).

---

### M16 · Jump Game VI

**🔗 [LC 1696 — Jump Game VI](https://leetcode.com/problems/jump-game-vi/)** · Medium
**Pattern:** Deque DP | **Companies:** Amazon, Google

**Hint:** `dp[i] = nums[i] + max(dp[i-k .. i-1])`. Keep a deque of indices with decreasing `dp` values; pop the front when it's out of the window, read the max from the front, and pop smaller values from the back before pushing `i`.

---

## 🔴 Hard Tier (8 Problems)

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

### H5 · Largest Rectangle in Histogram

**🔗 [LC 84 — Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)** · Hard
**Pattern:** Monotonic Increasing Stack | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Keep an increasing stack of indices. When a shorter bar arrives, pop: the popped bar's height times the width between the new top and `i` is a candidate area. Append a height-0 bar at the end to flush the stack.

---

### H6 · Car Fleet II

**🔗 [LC 1776 — Car Fleet II](https://leetcode.com/problems/car-fleet-ii/)** · Hard
**Pattern:** Monotonic Stack from the Right | **Companies:** Google

**Hint:** Process cars from right to left with a stack of cars ahead. Pop any car that is at least as fast (you never catch it), or that collides before you would reach it. The top is the car you hit; compute the time from the gap and speed difference.

---

### H7 · Sliding Window Maximum

**🔗 [LC 239 — Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)** · Hard
**Pattern:** Monotonic Deque | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Keep a deque of indices with decreasing values. Pop the front if it has left the window, pop smaller values from the back before pushing `i`, and read the front as the window max once `i >= k - 1`.

---

### H8 · Maximal Rectangle

**🔗 [LC 85 — Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)** · Hard
**Pattern:** Histogram per Row + Monotonic Stack | **Companies:** Google, Amazon, Meta

**Hint:** Turn each row into a histogram: `height[j] = matrix[i][j] == '1' ? height[j] + 1 : 0`. Run Largest Rectangle in Histogram (LC 84) on it and keep the best area over all rows.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — next greater element for every item, with a stack

// Snippet 2 — the same, by scanning right from every item

// Snippet 3 — largest rectangle in a histogram with a stack

// Snippet 4 — sliding window maximum with a monotonic deque

// Snippet 5 — sliding window maximum with a heap

// Snippet 6 — sum of subarray minimums using the contribution technique
```

**Complexity Answers:**

1. **O(n)** — each index pushed and popped once.
2. **O(n²)**.
3. **O(n)**.
4. **O(n)**.
5. **O(n log n)**.
6. **O(n)** — two monotonic passes.

---

## 🔍 Self-Assessment — True / False

1. A monotonic stack solution with a while loop inside a for loop is O(n²). → **False** — each item is pushed once and popped at most once
2. A monotonic stack usually stores indices, not values. → **True** — indices let you compute distances and widths
3. A monotonic deque removes items from both ends. → **True** — the front when they leave the window, the back when beaten
4. A heap is faster than a monotonic deque for sliding window maximum. → **False** — O(n log n) versus O(n)
5. Next smaller element needs a different algorithm from next greater element. → **False** — flip the comparison
6. The contribution technique counts how many subarrays each element is the minimum of. → **True**

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

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Count Hills and Valleys in an Array](https://leetcode.com/problems/count-hills-and-valleys-in-an-array/), [Minimum String Length After Removing Substrings](https://leetcode.com/problems/minimum-string-length-after-removing-substrings/), [Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/), [Max Value of Equation](https://leetcode.com/problems/max-value-of-equation/) |
| **Google**    | [Car Fleet II](https://leetcode.com/problems/car-fleet-ii/), [Maximum Score of a Good Subarray](https://leetcode.com/problems/maximum-score-of-a-good-subarray/), [Number of Visible People in a Queue](https://leetcode.com/problems/number-of-visible-people-in-a-queue/), [Jump Game VI](https://leetcode.com/problems/jump-game-vi/)                                                                                 |
| **Meta**      | [Constrained Subsequence Sum](https://leetcode.com/problems/constrained-subsequence-sum/), [Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/), [132 Pattern](https://leetcode.com/problems/132-pattern/), [Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)                                                                                                                     |
| **Microsoft** | [Crawler Log Folder](https://leetcode.com/problems/crawler-log-folder/), [Find the Most Competitive Subsequence](https://leetcode.com/problems/find-the-most-competitive-subsequence/), [Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/), [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)                             |
| **Uber**      | [Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/), [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)                                                                                                                                                 |

---

## ✅ Completion Checklist

- [ ] All 5 Easy problems solved
- [ ] All 16 Medium problems solved
- [ ] All 8 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write the four variants by changing only the loop direction and the comparison
- [ ] I can derive `left × right` for the contribution technique without looking it up

---

**← [Lecture 26 · Prefix Sums & Difference Arrays](../Lecture26/Assignment.md)** &nbsp;·&nbsp; **[Lecture 28 · Intervals & Sweep Line](../Lecture28/Assignment.md) →**
