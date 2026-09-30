# 📚 Assignment 15 — Stacks & Queues

> **Lecture:** 15 of 45 — Stacks & Queues
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 4 days · **Total Problems:** 16 (9 Easy · 6 Medium · 1 Hard)
> **Goal:** Master LIFO/FIFO fundamentals and stack-driven expression evaluation, and get a first look at the monotonic stack (taught fully in Lecture 27).

---

## 🗺️ Pattern Recognition — Read Before Starting

Stacks and Queues are the most universally applicable data structures in algorithm problem-solving. Every OS call stack is a stack. Every BFS is a queue. Every Next-Greater-Element variant is a Monotonic Stack. Mastering these structures means you can solve an entire class of interview problems by **recognising the pattern** rather than brute-forcing each problem.

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem            | Pattern                   | Move                                        |
| -------------------------------- | ------------------------- | ------------------------------------------- |
| "matching brackets", "undo"      | Plain Stack               | push opens, pop on close                    |
| "next greater / smaller element" | Monotonic Stack           | pop while the new value beats the top       |
| "evaluate an expression"         | Operand / Operator Stacks | push numbers, apply on operators            |
| "process in arrival order"       | Queue                     | enqueue at the back, dequeue from the front |

---

## 🟢 Easy Tier (9 Problems)

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

### E9 · Next Greater Element I

**🔗 [LC 496 — Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)** · Easy
**Pattern:** Mono Stack + HashMap | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Run a monotonic decreasing stack over `nums2`: when a value `x` pops smaller values, record `nge[popped] = x`. Then answer each `nums1` value with `nge.getOrDefault(v, -1)`.

---

## 🟡 Medium Tier (6 Problems)

_Stack design, expression parsing, circular buffers — and Daily Temperatures as a monotonic-stack preview._

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

### M3 · Evaluate Reverse Polish Notation

**🔗 [LC 150 — Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)** · Medium
**Pattern:** Stack | **Companies:** Amazon, LinkedIn, Meta

**Hint:** Push numbers. On an operator, pop `b` first, then `a`, and push `a op b` — order matters for `-` and `/`. Integer division truncates toward zero.

---

### M4 · Decode String

**🔗 [LC 394 — Decode String](https://leetcode.com/problems/decode-string/)** · Medium
**Pattern:** Stack of (count, string) | **Companies:** Google, Amazon, Meta, Bloomberg

**Hint:** Two stacks: counts and string builders. Digits build a number; `[` pushes the count and the current string and starts a new one; `]` pops them and appends the current string repeated `count` times to the popped string.

---

### M5 · Design Circular Queue

**🔗 [LC 622 — Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)** · Medium
**Pattern:** Design | **Companies:** Microsoft, Amazon, Google

**Hint:** An array of capacity `k` with `head`, `tail` and `size`. `enQueue` writes at `tail` and moves it with `(tail + 1) % k`; `deQueue` moves `head` the same way. `size` tells full from empty.

---

### M6 · Design Circular Deque

**🔗 [LC 641 — Design Circular Deque](https://leetcode.com/problems/design-circular-deque/)** · Medium
**Pattern:** Design | **Companies:** Amazon, Google

**Hint:** A ring buffer with `front` and `rear` moving both ways: insert at the front with `front = (front - 1 + k) % k`, and at the rear by writing then `rear = (rear + 1) % k`. Track `size`.

---

## 🔴 Hard Tier (1 Problem)

_One full expression parser. The Hard monotonic-stack problems live in Lecture 27._

### H1 · Basic Calculator

**🔗 [LC 224 — Basic Calculator](https://leetcode.com/problems/basic-calculator/)** · Hard
**Pattern:** Sign Stack + Operand Stack | **Companies:** Google, Amazon, Meta

**Hint:** Scan with `result`, `number` and `sign`. On `(`, push `result` and `sign`, then reset both. On `)`, finish the current number and set `result = popped result + popped sign × result`. Unary minus is handled because `sign` starts at +1.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — n pushes then n pops on an ArrayDeque

// Snippet 2 — queue made of two stacks, n operations in total

// Snippet 3
for i from 0 to n - 1:
    while stack not empty and stack.top < a[i]:
        stack.pop()
    stack.push(a[i])

// Snippet 4 — check balanced brackets in a string of length n

// Snippet 5 — stack made of two queues, n pushes (push is the costly one)

// Snippet 6 — evaluate a postfix (RPN) expression of n tokens
```

**Complexity Answers:**

1. **O(n)** total — O(1) each.
2. **O(n)** total — each item moves between stacks at most once (amortised O(1)).
3. **O(n)** — every item is pushed once and popped at most once, however the while loop looks.
4. **O(n)** time, **O(n)** space in the worst case.
5. **O(n²)** total — each push rotates the whole queue.
6. **O(n)** time, O(n) space.

---

## 🔍 Self-Assessment — True / False

1. A stack gives last-in, first-out order. → **True**
2. ArrayDeque is slower than java.util.Stack. → **False** — it is faster; Stack is synchronised legacy code
3. A queue built from two stacks has O(1) amortised operations. → **True** — each element is transferred at most once
4. Balanced-bracket checking needs recursion. → **False** — one stack is enough
5. A loop containing a while-pop loop is always O(n²). → **False** — if each item is pushed and popped once, the total is O(n)
6. peek() on an empty ArrayDeque returns null rather than throwing. → **True** — peek returns null; pop and element throw

---

## 🧠 Conceptual Check

Answer these without looking at code:

1. **LIFO vs FIFO**: Give two real-world examples of each (not from lectures).
2. **Monotonic Stack Invariant**: What exactly is violated when you pop from the stack during a Monotonic Decreasing Stack traversal?
3. **Amortised O(1)**: In the two-stack Queue design, a single `pop()` can be O(N). Why is the _amortised_ cost still O(1)?
4. **Deque vs stack vs queue**: What can a deque do that neither a stack nor a queue can, and why is `ArrayDeque` preferred over the legacy `Stack` class?
5. **Stack vs Recursion**: Every recursive algorithm uses an implicit call stack. When is it better to use an explicit stack instead?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                   |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Design Circular Deque](https://leetcode.com/problems/design-circular-deque/), [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/), [Min Stack](https://leetcode.com/problems/min-stack/), [Baseball Game](https://leetcode.com/problems/baseball-game/)                                                 |
| **Google**    | [Make The String Great](https://leetcode.com/problems/make-the-string-great/), [Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/), [Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/), [Design Circular Deque](https://leetcode.com/problems/design-circular-deque/)                   |
| **Meta**      | [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/), [Basic Calculator](https://leetcode.com/problems/basic-calculator/), [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/), [Decode String](https://leetcode.com/problems/decode-string/)                                         |
| **Microsoft** | [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/), [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/), [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/), [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) |
| **Adobe**     | [Baseball Game](https://leetcode.com/problems/baseball-game/), [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/), [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)                                                                                                              |

---

## ✅ Completion Checklist

- [ ] All 9 Easy problems solved
- [ ] All 6 Medium problems solved
- [ ] All 1 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can explain the invariant a monotonic stack keeps
- [ ] I can say why two-stack queue operations are amortised O(1)

---

**← [Lecture 14 · Linked Lists](../Lecture14/Assignment.md)** &nbsp;·&nbsp; **[Lecture 16 · HashMap & HashSet](../Lecture16/Assignment.md) →**
