# 📚 Assignment 12 — Stacks & Queues

> **Lecture:** 12 of 38 — Stacks & Queues
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 5 days · **Total Problems:** 25 (8 Easy · 12 Medium · 5 Hard)
> **Goal:** Master LIFO/FIFO fundamentals, the Monotonic Stack template, Deque-based sliding window, and stack-driven expression evaluation.

---

## 🗺️ Pattern Recognition — Read Before Starting

Stacks and Queues are the most universally applicable data structures in algorithm problem-solving. Every OS call stack is a stack. Every BFS is a queue. Every Next-Greater-Element variant is a Monotonic Stack. Mastering these structures means you can solve an entire class of interview problems by **recognising the pattern** rather than brute-forcing each problem.

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem            | Pattern                   | Move                                        |
| -------------------------------- | ------------------------- | ------------------------------------------- |
| "matching brackets", "undo"      | Plain Stack               | push opens, pop on close                    |
| "next greater / smaller element" | Monotonic Stack           | pop while the new value beats the top       |
| "largest rectangle", "span"      | Increasing Stack          | pop computes the area that just ended       |
| "max / min of every window"      | Monotonic Deque           | front is the answer, back is pruned         |
| "evaluate an expression"         | Operand / Operator Stacks | push numbers, apply on operators            |
| "process in arrival order"       | Queue                     | enqueue at the back, dequeue from the front |

---

## 🟢 Easy Tier (8 Problems)

_Focus on stack and queue mechanics — push, pop, LIFO/FIFO invariants, and basic design._

### E1 · Valid Parentheses

**🔗 [LC 20 — Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)** · Easy
**Pattern:** Stack | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Push every opening bracket. On a closing bracket, the stack must be non-empty and its top must be the matching opener, which you pop. At the end the stack must be empty.

---

### E2 · Implement Stack using Queues

**🔗 [LC 225 — Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)** · Easy
**Pattern:** OOP Design | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Push costs O(n): add the new element to the queue, then rotate the queue `size - 1` times so the new element is at the front. Pop and top are then O(1) — the front is the stack's top.

---

### E3 · Implement Queue using Stacks

**🔗 [LC 232 — Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)** · Easy
**Pattern:** OOP Design | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** Push onto `in`. For pop or peek, if `out` is empty, move everything from `in` to `out` (reversing the order), then use `out`'s top. Each element moves at most once, so operations are amortised O(1).

---

### E4 · Baseball Game

**🔗 [LC 682 — Baseball Game](https://leetcode.com/problems/baseball-game/)** · Easy
**Pattern:** Stack Simulation | **Companies:** Amazon, Adobe

**Hint:** Walk the operations with a stack of scores: a number is pushed, `+` pushes the sum of the top two, `D` pushes double the top, and `C` pops. Return the sum of the stack.

---

### E5 · Remove All Adjacent Duplicates In String

**🔗 [LC 1047 — Remove All Adjacent Duplicates In String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)** · Easy
**Pattern:** Stack | **Companies:** Amazon, Google, Meta

**Hint:** Use a `StringBuilder` as the stack. For each char, if it equals the last char, delete that char; otherwise append. What's left is the answer.

---

### E6 · Number of Recent Calls

**🔗 [LC 933 — Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)** · Easy
**Pattern:** Queue | **Companies:** Amazon, Google

**Hint:** Keep a queue of timestamps. On `ping(t)`, add `t`, then remove timestamps `< t - 3000` from the front. Return the queue's size.

---

### E7 · Time Needed to Buy Tickets

**🔗 [LC 2073 — Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/)** · Easy
**Pattern:** Queue Simulation | **Companies:** Amazon, Google

**Hint:** Simulate with a queue of indices, or use the O(n) formula: a person `i <= k` waits `min(tickets[i], tickets[k])` rounds, and a person `i > k` waits `min(tickets[i], tickets[k] - 1)`.

---

### E8 · Make The String Great

**🔗 [LC 1544 — Make The String Great](https://leetcode.com/problems/make-the-string-great/)** · Easy
**Pattern:** Stack | **Companies:** Amazon, Google

**Hint:** Stack of chars (a `StringBuilder` works): if the top and the current char are the same letter in opposite cases (`abs(a - b) == 32`), pop; otherwise push.

---

## 🟡 Medium Tier (12 Problems)

_Focus on Monotonic Stack, Deque, Min-Stack design, and expression parsing._

### M1 · Min Stack

**🔗 [LC 155 — Min Stack](https://leetcode.com/problems/min-stack/)** · Medium
**Pattern:** Stack Design | **Companies:** Amazon, Google, Bloomberg

**Hint:** Push `(value, min so far)` pairs — or keep a second stack of minimums. `getMin` reads the top's stored min in O(1), and popping restores the previous min automatically.

---

### M2 · Daily Temperatures

**🔗 [LC 739 — Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)** · Medium
**Pattern:** Monotonic Stack | **Companies:** Amazon, Google, Meta

**Hint:** Keep a stack of indices with decreasing temperatures. For each day, pop every index with a lower temperature and set `answer[popped] = i - popped`, then push `i`.

---

### M3 · Next Greater Element I

**🔗 [LC 496 — Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)** · Easy
**Pattern:** Mono Stack + HashMap | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Run a monotonic decreasing stack over `nums2`: when a value `x` pops smaller values, record `nge[popped] = x`. Then answer each `nums1` value with `nge.getOrDefault(v, -1)`.

---

### M4 · Next Greater Element II

**🔗 [LC 503 — Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)** · Medium
**Pattern:** Monotonic Stack | **Companies:** Amazon, Google, Meta

**Hint:** Loop over indices `0..2n-1`, using `nums[i % n]`, with a decreasing stack of indices. Pop and assign answers while the current value is larger; only push during the first pass.

---

### M5 · Online Stock Span

**🔗 [LC 901 — Online Stock Span](https://leetcode.com/problems/online-stock-span/)** · Medium
**Pattern:** Monotonic Decreasing Stack | **Companies:** Amazon, Google, Bloomberg

**Hint:** Keep a stack of `(price, span)`. For a new price, pop every entry with price `<=` it and add its span to the current span (starting at 1), then push. Amortised O(1).

---

### M6 · Evaluate Reverse Polish Notation

**🔗 [LC 150 — Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)** · Medium
**Pattern:** Stack | **Companies:** Amazon, LinkedIn, Meta

**Hint:** Push numbers. On an operator, pop `b` first, then `a`, and push `a op b` — order matters for `-` and `/`. Integer division truncates toward zero.

---

### M7 · Decode String

**🔗 [LC 394 — Decode String](https://leetcode.com/problems/decode-string/)** · Medium
**Pattern:** Stack of (count, string) | **Companies:** Google, Amazon, Meta, Bloomberg

**Hint:** Two stacks: counts and string builders. Digits build a number; `[` pushes the count and the current string and starts a new one; `]` pops them and appends the current string repeated `count` times to the popped string.

---

### M8 · Remove K Digits

**🔗 [LC 402 — Remove K Digits](https://leetcode.com/problems/remove-k-digits/)** · Medium
**Pattern:** Greedy + Stack | **Companies:** Google, Amazon, Meta

**Hint:** Build an increasing stack of digits: while `k > 0` and the top is greater than the current digit, pop and decrement `k`. Push the digit. Remove any remaining `k` from the end, strip leading zeros, and return "0" if nothing is left.

---

### M9 · Design Circular Queue

**🔗 [LC 622 — Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)** · Medium
**Pattern:** Design | **Companies:** Microsoft, Amazon, Google

**Hint:** An array of capacity `k` with `head`, `tail` and `size`. `enQueue` writes at `tail` and moves it with `(tail + 1) % k`; `deQueue` moves `head` the same way. `size` tells full from empty.

---

### M10 · Design Circular Deque

**🔗 [LC 641 — Design Circular Deque](https://leetcode.com/problems/design-circular-deque/)** · Medium
**Pattern:** Design | **Companies:** Amazon, Google

**Hint:** A ring buffer with `front` and `rear` moving both ways: insert at the front with `front = (front - 1 + k) % k`, and at the rear by writing then `rear = (rear + 1) % k`. Track `size`.

---

### M11 · Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit

**🔗 [LC 1438 — Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/)** · Medium
**Pattern:** Two Monotonic Deques | **Companies:** Google, Amazon, Uber

**Hint:** Keep a decreasing deque for the window max and an increasing deque for the window min. Expand right; while `max - min > limit`, move left and pop expired fronts. O(n).

---

### M12 · Jump Game VI

**🔗 [LC 1696 — Jump Game VI](https://leetcode.com/problems/jump-game-vi/)** · Medium
**Pattern:** Deque DP | **Companies:** Amazon, Google

**Hint:** `dp[i] = nums[i] + max(dp[i-k .. i-1])`. Keep a deque of indices with decreasing `dp` values; pop the front when it's out of the window, read the max from the front, and pop smaller values from the back before pushing `i`.

---

## 🔴 Hard Tier (5 Problems)

_Focus on Hard monotonic problems and advanced stack-driven simulations._

### H1 · Largest Rectangle in Histogram

**🔗 [LC 84 — Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)** · Hard
**Pattern:** Monotonic Increasing Stack | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Keep an increasing stack of indices. When a shorter bar arrives, pop: the popped bar's height times the width between the new top and `i` is a candidate area. Append a height-0 bar at the end to flush the stack.

---

### H2 · Car Fleet II

**🔗 [LC 1776 — Car Fleet II](https://leetcode.com/problems/car-fleet-ii/)** · Hard
**Pattern:** Monotonic Stack from the Right | **Companies:** Google

**Hint:** Process cars from right to left with a stack of cars ahead. Pop any car that is at least as fast (you never catch it), or that collides before you would reach it. The top is the car you hit; compute the time from the gap and speed difference.

---

### H3 · Sliding Window Maximum

**🔗 [LC 239 — Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)** · Hard
**Pattern:** Monotonic Deque | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Keep a deque of indices with decreasing values. Pop the front if it has left the window, pop smaller values from the back before pushing `i`, and read the front as the window max once `i >= k - 1`.

---

### H4 · Basic Calculator

**🔗 [LC 224 — Basic Calculator](https://leetcode.com/problems/basic-calculator/)** · Hard
**Pattern:** Sign Stack + Operand Stack | **Companies:** Google, Amazon, Meta

**Hint:** Scan with `result`, `number` and `sign`. On `(`, push `result` and `sign`, then reset both. On `)`, finish the current number and set `result = popped result + popped sign × result`. Unary minus is handled because `sign` starts at +1.

---

### H5 · Maximal Rectangle

**🔗 [LC 85 — Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)** · Hard
**Pattern:** Histogram per Row + Monotonic Stack | **Companies:** Google, Amazon, Meta

**Hint:** Turn each row into a histogram: `height[j] = matrix[i][j] == '1' ? height[j] + 1 : 0`. Run Largest Rectangle in Histogram (LC 84) on it and keep the best area over all rows.

---

## 🧠 Conceptual Check

Answer these without looking at code:

1. **LIFO vs FIFO**: Give two real-world examples of each (not from lectures).
2. **Monotonic Stack Invariant**: What exactly is violated when you pop from the stack during a Monotonic Decreasing Stack traversal?
3. **Amortised O(1)**: In the two-stack Queue design, a single `pop()` can be O(N). Why is the _amortised_ cost still O(1)?
4. **Deque vs Heap**: When would you use a Monotonic Deque instead of a Min/Max Heap for sliding window problems? What is the complexity advantage?
5. **Stack vs Recursion**: Every recursive algorithm uses an implicit call stack. When is it better to use an explicit stack instead?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                 |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/), [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/), [Basic Calculator](https://leetcode.com/problems/basic-calculator/), [Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)           |
| **Google**    | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/), [Car Fleet II](https://leetcode.com/problems/car-fleet-ii/), [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/), [Basic Calculator](https://leetcode.com/problems/basic-calculator/)                     |
| **Meta**      | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/), [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/), [Basic Calculator](https://leetcode.com/problems/basic-calculator/), [Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)           |
| **Microsoft** | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/), [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/), [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/), [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) |
| **Bloomberg** | [Min Stack](https://leetcode.com/problems/min-stack/), [Online Stock Span](https://leetcode.com/problems/online-stock-span/), [Decode String](https://leetcode.com/problems/decode-string/), [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)                                               |

---

## ✅ Completion Checklist

- [ ] All 8 Easy problems solved
- [ ] All 12 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] All 5 conceptual questions answered out loud
- [ ] I can explain the invariant a monotonic stack keeps
- [ ] I can say why two-stack queue operations are amortised O(1)

---

**← [Lecture 11 · Linked Lists](../Lecture11/Assignment.md)** &nbsp;·&nbsp; **[Lecture 13 · HashMap & HashSet](../Lecture13/Assignment.md) →**
