# 🔁 Assignment 8 — Recursion & Backtracking

> **Lecture:** 8 of 45 — Recursion — The Mental Model
> **Phase:** 1 — Foundations
> **Estimated Time:** 4 days · **Total Problems:** 16 (12 Easy · 4 Medium · 0 Hard)
> **Goal:** Trust the recursive call, find the base case first, read the cost from the call tree, and remove repeated work with a memo.
> pruning.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                        | Pattern                   | Move                                |
| -------------------------------------------- | ------------------------- | ----------------------------------- |
| the answer for n uses the answer for n − 1   | Linear recursion          | one call, base case first           |
| carry a running total or path downward       | Parameterised recursion   | pass the accumulator as an argument |
| build the answer from what the calls return  | Functional recursion      | combine the returned values         |
| two or more calls, the same arguments repeat | Tree recursion + memo     | cache on the arguments              |
| halve the input every call                   | Divide by two             | O(log n) depth                      |
| solve a smaller copy of the same problem     | Divide & Conquer          | split, recurse, combine             |
| "all subsets", "all arrangements"            | Backtracking — Lecture 24 | preview only; taught in full later  |

---

## 🟢 Easy Tier (12 Problems)

_Warm-ups. Write the base case first, then trust the call. Every one of these is under ten lines._

### E1 · Sum of First N Numbers

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** Write `sum(n)` recursively. Draw the call stack for `n=4`. Use `return n + sum(n-1)`. State the space complexity (O is NOT 1 here!).

---

### E2 · Factorial & GCD

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** Implement `factorial(n)` and `gcd(a, b)` recursively. Why is recursion better than loops for Euclid's GCD?

---

### E3 · Power Function (O(n))

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** Implement `pow(x, n)` as `x * pow(x, n-1)`. Then look at Lecture 10 for how to do this in O(log n).

---

### E4 · Reverse an Array (Two Pointers)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** Use recursion to swap `arr[l]` and `arr[r]`, then call `reverse(l+1, r-1)`. Base case: `l >= r`.

---

### E5 · Valid Palindrome II

**🔗 [LC 680 — Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/)** · Easy
**Pattern:** Recursion — Branch Once | **Companies:** Meta, Amazon, Microsoft

**Hint:** Write `isPal(s, l, r)` recursively. At the first mismatch you get exactly one deletion, so return `isPal(l + 1, r) || isPal(l, r - 1)` with no deletions left.

---

### E6 · Kth Missing Positive Number

**🔗 [LC 1539 — Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)** · Easy
**Pattern:** Recursive Binary Search | **Companies:** Meta, Amazon, Microsoft

**Hint:** The count of missing numbers before index `i` is `arr[i] - (i + 1)`. Binary search — recursively — for the first index where that count is at least `k`; the answer is `lo + k`.

---

### E7 · Count Digits Recursively

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** `1 + countDigits(n/10)` if `n > 0`.

---

### E8 · Check if Array is Sorted

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** `return (arr[0] <= arr[1]) && isSorted(rest of array)`.

---

### E9 · Linear Search (Recursive)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** Search index 0, then recurse.

---

### E10 · Fibonacci Number

**🔗 [LC 509 — Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)** · Easy
**Pattern:** Multiple Recursion | **Companies:** Amazon, Google, Adobe

**Hint:** Implement `fib(n) = fib(n-1) + fib(n-2)` and draw the recursion tree for `n = 5`. Count the repeated calls, then add a memo array and count again.

---

### E11 · Sum of Digits in Base K

**🔗 [LC 1837 — Sum of Digits in Base K](https://leetcode.com/problems/sum-of-digits-in-base-k/)** · Easy
**Pattern:** Linear Recursion on Digits | **Companies:** Amazon, Adobe

**Hint:** Recursive rule: `sumBase(n, k) = n % k + sumBase(n / k, k)`, with base case `n == 0`.

---

### E12 · Binary Tree Paths

**🔗 [LC 257 — Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)** · Easy
**Pattern:** Tree Traversal | **Companies:** Google, Amazon, Meta

**Hint:** Return all paths from root to leaf. Pre-order traversal with a path tracker.

---

## 🟡 Medium Tier (4 Problems)

_Recursion that sorts, partitions, simulates, and — in Target Sum — needs a memo to finish in time._

### M1 · Sort an Array

**🔗 [LC 912 — Sort an Array](https://leetcode.com/problems/sort-an-array/)** · Medium
**Pattern:** Merge Sort (Divide & Conquer) | **Companies:** Amazon, Microsoft, Google

**Hint:** Recursively sort the left and right halves, then merge with two pointers into a temporary array. Base case: size ≤ 1. Guaranteed O(n log n), which LeetCode requires here.

---

### M2 · Partition Array According to Given Pivot

**🔗 [LC 2161 — Partition Array According to Given Pivot](https://leetcode.com/problems/partition-array-according-to-given-pivot/)** · Medium
**Pattern:** Partition Logic | **Companies:** Amazon, Google

**Hint:** This is quicksort's partition step, done stably: collect elements `< pivot`, then `== pivot`, then `> pivot`. Then try it in one pass that writes smaller elements from the front and larger ones from the back.

---

### M3 · Find the Winner of the Circular Game

**🔗 [LC 1823 — Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/)** · Medium
**Pattern:** Recurrence | **Companies:** Amazon, Google, Adobe

**Hint:** `n` people in a circle, every `k`-th is removed. Return the survivor. (Hint: 0-indexed, `f(1, k) = 0` and `f(n, k) = (f(n-1, k) + k) % n`; LeetCode numbers people from 1, so return `f(n, k) + 1`).

---

### M4 · Target Sum

**🔗 [LC 494 — Target Sum](https://leetcode.com/problems/target-sum/)** · Medium
**Pattern:** +/- Choices | **Companies:** Meta, Amazon, Google

**Hint:** Every number gets a `+` or a `-`: recurse `(i + 1, sum ± nums[i])` and count paths that end at `target`. Then memoise on `(i, sum)`. The DP trick (a subset with sum `(total + target) / 2`) comes in Lecture 34.

---

## 🔴 Hard Tier (0 Problems)

_No Hard problems here — the hard recursion problems are backtracking, which has its own lecture (24)._

## 📊 Complexity Analysis Exercises

Trace the recursion tree and find Time & Space complexity.

```pseudocode
// Snippet 1
function recur(n):
    if n ≤ 1: return
    for i from 0 to n - 1: print(i)
    recur(n ÷ 2)

// Snippet 2
function solve(n):
    if n ≤ 0: return
    solve(n - 1)
    solve(n - 1)

// Snippet 3
// Generating all subsets of an array of size N

// Snippet 4
// Generating all permutations of an array of size N

// Snippet 5
function factorial(n):
    if n = 0: return 1
    return n × factorial(n - 1)

// Snippet 6
// Fibonacci with memoisation

// Snippet 7
function work(n):
    if n ≤ 1: return
    for i from 0 to n - 1: work(n - 1)

// Snippet 8
// Traversing a perfectly balanced binary tree of height H
```

**Complexity Answers:**

1. **O(n)** Time (n + n/2 + n/4... = 2n), O(log n) Space (Stack depth).
2. **O(2ⁿ)** Time, O(n) Space.
3. **O(2ⁿ \* n)** Time. 2ⁿ subsets, n work per subset.
4. **O(n! \* n)** Time. n! permutations, n work per result.
5. **O(n)** Time, O(n) Space.
6. **O(n)** Time, O(n) Space.
7. **O(n!)** Time.
8. **O(2ᴴ)** Time, O(H) Space.

---

## 🔍 Self-Assessment — True / False

1. Base case is optional in recursion if the input is always positive. → **False** (leads to infinite recursion).
2. A recursive function uses stack memory in proportion to its depth, which a simple loop avoids. → **True** (Java
   never removes those frames — it has no tail-call optimisation).
3. A recursive call with a smaller argument always terminates. → **False** (only if every path reaches a base case).
4. Memoisation converts a recursive problem to O(n) space always. → **False** (Depends on state variables).
5. Tail recursion can be turned into a loop without any extra stack. → **True** (the call is the last thing, so no frame needs to survive it).
6. Recursion stack limit can be changed in JVM flags. → **True**.
7. Divide and Conquer and Dynamic Programming mean the same thing. → **False** (DP has overlapping subproblems).
8. Every recursive solution can be written iteratively. → **True** (replace the call stack with an explicit stack).

---

## 🧠 Conceptual Check

1. **Leap of faith**: In your own words, what are you allowed to assume about the recursive call, and why is that not circular reasoning?
2. **Stack Overflow**: Why does `int[] a = new int[1000000]` inside a recursive method not cause `StackOverflowError`
   immediately, while nesting 1 million depth does? (Hint: Stack stores reference, Heap stores array).
3. **Memoisation vs Tabulation**: Explain Top-Down vs Bottom-Up. Which one is closer to pure recursion?
4. **Call-tree cost**: Draw the call tree for `fib(5)`. Count the calls, then count them again with a memo. Where does the saving come from?
5. **Tail Recursion**: What is Tail Call Optimisation (TCO)? Does Java support it natively?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                             |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Partition Array According to Given Pivot](https://leetcode.com/problems/partition-array-according-to-given-pivot/), [Sum of Digits in Base K](https://leetcode.com/problems/sum-of-digits-in-base-k/), [Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/), [Sort an Array](https://leetcode.com/problems/sort-an-array/) |
| **Google**    | [Partition Array According to Given Pivot](https://leetcode.com/problems/partition-array-according-to-given-pivot/), [Target Sum](https://leetcode.com/problems/target-sum/), [Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/), [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)                                                           |
| **Meta**      | [Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/), [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/), [Target Sum](https://leetcode.com/problems/target-sum/), [Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)                                                                               |
| **Adobe**     | [Sum of Digits in Base K](https://leetcode.com/problems/sum-of-digits-in-base-k/), [Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/), [Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)                                                                                                                |
| **Microsoft** | [Sort an Array](https://leetcode.com/problems/sort-an-array/), [Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/), [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/)                                                                                                                                                |

---

## ✅ Completion Checklist

- [ ] All 12 Easy problems solved
- [ ] All 4 Medium problems solved
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can draw the recursion tree for a small input before coding
- [ ] I can add a memo to a recursion and say what the cache key is

---

**← [Lecture 7 · Java 8+ Modern Features](../Lecture7/Assignment.md)** &nbsp;·&nbsp; **[Lecture 9 · Bit Manipulation](../Lecture9/Assignment.md) →**
