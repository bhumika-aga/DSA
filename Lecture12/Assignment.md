# 📚 Assignment 12 — Stacks & Queues

> **Lecture:** Topic 12 — Stacks & Queues
> **Topic Count:** 12 of 30 — Phase 2 Core Data Structures
> **Duration:** 5 Days
> **Core Problems:** 25 (8 Easy · 12 Medium · 5 Hard)
> **Goal:** Master LIFO/FIFO fundamentals, the Monotonic Stack template, Deque-based sliding window, and stack-driven expression evaluation.

---

## 📊 Topic Overview

Stacks and Queues are the most universally applicable data structures in algorithm problem-solving. Every OS call stack is a stack. Every BFS is a queue. Every Next-Greater-Element variant is a Monotonic Stack. Mastering these structures means you can solve an entire class of interview problems by **recognising the pattern** rather than brute-forcing each problem.

- **Primary Patterns**: Plain Stack (bracket matching, undo), Monotonic Decreasing Stack (NGE/span), Monotonic Increasing Stack (histogram/area), Deque (sliding window), Two-Stack Design, Queue-as-BFS.
- **Key Focus**: Knowing _which_ stack/queue variant a problem needs — and applying it without hesitation.

---

## 🟢 Easy Tier (Foundations)

_Focus on stack and queue mechanics — push, pop, LIFO/FIFO invariants, and basic design._

1. **[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) (LC 20)** — The canonical stack problem: push open, match close. `[Pattern: Stack]`
2. **[Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/) (LC 225)** — Design insight: reverse order via two queues. `[Pattern: OOP Design]`
3. **[Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/) (LC 232)** — Amortised O(1) via inbox/outbox pattern. `[Pattern: OOP Design]`
4. **[Baseball Game](https://leetcode.com/problems/baseball-game/) (LC 682)** — Apply stack rules: +, D (double), C (cancel). `[Pattern: Stack Simulation]`
5. **[Remove All Adjacent Duplicates In String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/) (LC 1047)** — Stack pops on match, join the rest. `[Pattern: Stack]`
6. **[Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/) (LC 933)** — Sliding window of timestamps using a queue. `[Pattern: Queue]`
7. **[Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/) (LC 2073)** — Queue simulation with modulo trick available. `[Pattern: Queue Simulation]`
8. **[Make The String Great](https://leetcode.com/problems/make-the-string-great/) (LC 1544)** — Stack: pop if top and current are case-opposite same letter. `[Pattern: Stack]`

---

## 🟡 Medium Tier (Advanced Patterns)

_Focus on Monotonic Stack, Deque, Min-Stack design, and expression parsing._

1. **[Min Stack](https://leetcode.com/problems/min-stack/) (LC 155)** — Two parallel stacks: main + running-min. `[Pattern: Stack Design]`
2. **[Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) (LC 739)** — Distance to NGE: monotonic decreasing stack of indices. `[Pattern: Monotonic Stack]`
3. **[Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) (LC 496)** — Pre-compute NGE map, then query. `[Pattern: Mono Stack + HashMap]`
4. **[Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/) (LC 503)** — Circular array NGE: iterate 2× over nums with stack. `[Pattern: Monotonic Stack]`
5. **[Online Stock Span](https://leetcode.com/problems/online-stock-span/) (LC 901)** — Monotonic decreasing stack tracking span (days since price was higher). `[Company: Amazon]`
6. **[Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) (LC 150)** — Stack arithmetic: pop b, pop a, compute a op b. `[Pattern: Stack]`
7. **[Decode String](https://leetcode.com/problems/decode-string/) (LC 394)** — Two stacks: one for counts, one for string prefixes. `[Company: Google]`
8. **[Remove K Digits](https://leetcode.com/problems/remove-k-digits/) (LC 402)** — Monotonic stack building the smallest number. `[Pattern: Greedy + Stack]`
9. **[Design Circular Queue](https://leetcode.com/problems/design-circular-queue/) (LC 622)** — Ring buffer: array + head/tail/size + modulo wrap. `[Pattern: Design]`
10. **[Design Circular Deque](https://leetcode.com/problems/design-circular-deque/) (LC 641)** — Extension: add/remove from both ends. `[Pattern: Design]`
11. **[Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/) (LC 1004)** — Sliding window queue variant: max 1s with at most K flips. `[Pattern: Sliding Window]`
12. **[Jump Game VI](https://leetcode.com/problems/jump-game-vi/) (LC 1696)** — Deque-based DP max: sliding window of dp values. `[Pattern: Deque DP]`

---

## 🔴 Challenge Zone (Mastery)

_Focus on Hard monotonic problems and advanced stack-driven simulations._

1. **[Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) (LC 84)** — Monotonic increasing stack, sentinel flush. `[Company: Amazon · Google]`
2. **[Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) (LC 42)** — Stack approach: water = (min(left, right) − bottom) × width. `[Company: Meta · Amazon]`
3. **[Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/) (LC 239)** — Monotonic decreasing deque, O(N) solution. `[Company: Google · Bloomberg]`
4. **[Basic Calculator](https://leetcode.com/problems/basic-calculator/) (LC 224)** — Full recursive-free parser with sign stack and operand stack. `[Company: Amazon]`
5. **[Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/) (LC 85)** — Transform each row into a histogram, then LC 84. `[Company: Google · Microsoft]`

---

## 📊 Conceptual Check

Answer these without looking at code:

1. **LIFO vs FIFO**: Give two real-world examples of each (not from lectures).
2. **Monotonic Stack Invariant**: What exactly is violated when you pop from the stack during a Monotonic Decreasing Stack traversal?
3. **Amortised O(1)**: In the two-stack Queue design, a single `pop()` can be O(N). Why is the _amortised_ cost still O(1)?
4. **Deque vs Heap**: When would you use a Monotonic Deque instead of a Min/Max Heap for sliding window problems? What is the complexity advantage?
5. **Stack vs Recursion**: Every recursive algorithm uses an implicit call stack. When is it better to use an explicit stack instead?

---

## 🏢 Company Focus

| Company       | Key Problem(s)                                                                                                                                                                                                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Google**    | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/), [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/), [Decode String](https://leetcode.com/problems/decode-string/)                                |
| **Amazon**    | [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/), [Min Stack](https://leetcode.com/problems/min-stack/), [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/), [Basic Calculator](https://leetcode.com/problems/basic-calculator/) |
| **Meta**      | [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/), [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)                                                                                                                               |
| **Microsoft** | [Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/), [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)                                                                                                                           |
| **Bloomberg** | [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/), [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)                                                                                                             |

---

**Next Topic**: Topic 13 — HashMap & HashSet Deep Dive →
