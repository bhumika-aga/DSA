# 🔁 Assignment 5 — Recursion & Backtracking

> **Lecture:** 5 of 38 — Recursion & Backtracking
> **Phase:** 1 — Foundations
> **Estimated Time:** 7 days · **Total Problems:** 35 (15 Easy · 15 Medium · 5 Hard)
> **Goal:** Master the "Divide & Conquer" thinking, recursive call-stack visualizing, and backtracking state-space
> pruning.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                      | Pattern           | Move                                     |
| ------------------------------------------ | ----------------- | ---------------------------------------- |
| "all subsets / subsequences"               | Include / Exclude | two branches per element                 |
| "all arrangements"                         | Permutations      | swap or use a `used[]` array, undo after |
| "choose k", "sum to target"                | Combinations      | start index + prune when over target     |
| "split the string into valid pieces"       | Partitioning      | try every cut, recurse on the rest       |
| "paths in a grid / maze"                   | Grid Backtracking | mark, recurse in 4 directions, unmark    |
| "solve a smaller copy of the same problem" | Divide & Conquer  | split, recurse, combine                  |

---

## 🟢 Easy Tier (15 Problems)

_Build the Recursion Tree._

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

**Task:** Implement `pow(x, n)` as `x * pow(x, n-1)`. Then look at Lecture 7 for how to do this in O(log n).

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

### E7 · Sort an Array

**🔗 [LC 912 — Sort an Array](https://leetcode.com/problems/sort-an-array/)** · Medium
**Pattern:** Merge Sort (Divide & Conquer) | **Companies:** Amazon, Microsoft, Google

**Hint:** Recursively sort the left and right halves, then merge with two pointers into a temporary array. Base case: size ≤ 1. Guaranteed O(n log n), which LeetCode requires here.

---

### E8 · Partition Array According to Given Pivot

**🔗 [LC 2161 — Partition Array According to Given Pivot](https://leetcode.com/problems/partition-array-according-to-given-pivot/)** · Medium
**Pattern:** Partition Logic | **Companies:** Amazon, Google

**Hint:** This is quicksort's partition step, done stably: collect elements `< pivot`, then `== pivot`, then `> pivot`. Then try it in one pass that writes smaller elements from the front and larger ones from the back.

---

### E9 · Print Subsequences ("Pick/Don't Pick")

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Include / Exclude (Subsets) | **Companies:** Amazon, Google, Adobe

**Task:** Given "abc", print all 2³ = 8 subsequences. This is the **most important pattern** for backtracking.

---

### E10 · Count Digits Recursively

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** `1 + countDigits(n/10)` if `n > 0`.

---

### E11 · Check if Array is Sorted

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** `return (arr[0] <= arr[1]) && isSorted(rest of array)`.

---

### E12 · Linear Search (Recursive)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Linear Recursion | **Companies:** Amazon, Google, Adobe

**Task:** Search index 0, then recurse.

---

### E13 · Fibonacci Number

**🔗 [LC 509 — Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)** · Easy
**Pattern:** Multiple Recursion | **Companies:** Amazon, Google, Adobe

**Hint:** Implement `fib(n) = fib(n-1) + fib(n-2)` and draw the recursion tree for `n = 5`. Count the repeated calls, then add a memo array and count again.

---

### E14 · Sum of Digits in Base K

**🔗 [LC 1837 — Sum of Digits in Base K](https://leetcode.com/problems/sum-of-digits-in-base-k/)** · Easy
**Pattern:** Linear Recursion on Digits | **Companies:** Amazon, Adobe

**Hint:** Recursive rule: `sumBase(n, k) = n % k + sumBase(n / k, k)`, with base case `n == 0`.

---

### E15 · Find the Winner of the Circular Game

**🔗 [LC 1823 — Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/)** · Medium
**Pattern:** Recurrence | **Companies:** Amazon, Google, Adobe

**Hint:** `n` people in a circle, every `k`-th is removed. Return the survivor. (Hint: 0-indexed, `f(1, k) = 0` and `f(n, k) = (f(n-1, k) + k) % n`; LeetCode numbers people from 1, so return `f(n, k) + 1`).

---

## 🟡 Medium Tier (15 Problems)

_The Backtracking Template._

### M1 · Subsets

**🔗 [LC 78 — Subsets](https://leetcode.com/problems/subsets/)** · Medium
**Pattern:** Include / Exclude | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Build all power sets. Use the template: `helper(index, currentList)`.

---

### M2 · Subsets II

**🔗 [LC 90 — Subsets II](https://leetcode.com/problems/subsets-ii/)** · Medium
**Pattern:** Sort + Skip Duplicates | **Companies:** Amazon, Google, Meta

**Hint:** Same as above, but with duplicate numbers. Sort first, then skip `nums[i]` if `nums[i] == nums[i-1]`.

---

### M3 · Permutations

**🔗 [LC 46 — Permutations](https://leetcode.com/problems/permutations/)** · Medium
**Pattern:** Swapping / Visited Array | **Companies:** Google, Amazon, Microsoft, Meta

**Hint:** Find all possible orderings of N distinct elements. O(n!).

---

### M4 · Combinations

**🔗 [LC 77 — Combinations](https://leetcode.com/problems/combinations/)** · Medium
**Pattern:** Range Recursion | **Companies:** Google, Amazon, Microsoft

**Hint:** Backtrack with a start index: at each level try numbers from `start` to `n`, add one, recurse with `start = i + 1`, then remove it. Prune when there aren't enough numbers left to reach size `k` (`i <= n - (k - path.size()) + 1`).

---

### M5 · Combination Sum

**🔗 [LC 39 — Combination Sum](https://leetcode.com/problems/combination-sum/)** · Medium
**Pattern:** Unlimited Reuse | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Find all unique combinations that sum to target. You can reuse the same element.

---

### M6 · Combination Sum II

**🔗 [LC 40 — Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)** · Medium
**Pattern:** Single Use + Duplicates | **Companies:** Amazon, Google, Meta

**Hint:** Each element used only once. Skip duplicates logic applied.

---

### M7 · Palindrome Partitioning

**🔗 [LC 131 — Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)** · Medium
**Pattern:** Cut / Validation | **Companies:** Google, Amazon, Meta

**Hint:** Partition string so every substring is a palindrome.

---

### M8 · Word Search

**🔗 [LC 79 — Word Search](https://leetcode.com/problems/word-search/)** · Medium
**Pattern:** Grid Backtracking (DFS) | **Companies:** Google, Amazon, Microsoft, Meta

**Hint:** Find if word exists in a 2D grid. Mark visited cell (e.g., set to '#'), search neighbors, then **unmark** (Backtrack).

---

### M9 · Letter Combinations of a Phone Number

**🔗 [LC 17 — Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)** · Medium
**Pattern:** Mapping + Recursion | **Companies:** Google, Amazon, Meta, Uber

**Hint:** E.g., 2="abc", 3="def". Return all strings "ad", "ae", "af"...

---

### M10 · Binary Tree Paths

**🔗 [LC 257 — Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)** · Easy
**Pattern:** Tree Traversal | **Companies:** Google, Amazon, Meta

**Hint:** Return all paths from root to leaf. Pre-order traversal with a path tracker.

---

### M11 · Target Sum

**🔗 [LC 494 — Target Sum](https://leetcode.com/problems/target-sum/)** · Medium
**Pattern:** +/- Choices | **Companies:** Meta, Amazon, Google

**Hint:** Every number gets a `+` or a `-`: recurse `(i + 1, sum ± nums[i])` and count paths that end at `target`. Then memoise on `(i, sum)`. The DP trick (a subset with sum `(total + target) / 2`) comes in Lecture 27.

---

### M12 · Generate Parentheses

**🔗 [LC 22 — Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)** · Medium
**Pattern:** Count-based Backtracking | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Keep track of open and close counts. Only add `)` if `close < open`.

---

### M13 · Path with Maximum Gold

**🔗 [LC 1219 — Path with Maximum Gold](https://leetcode.com/problems/path-with-maximum-gold/)** · Medium
**Pattern:** Grid DFS + Max result | **Companies:** Amazon, Google

**Hint:** From every cell with gold, DFS in 4 directions, temporarily setting the cell to 0 so a path can't revisit it and restoring it on the way back. Return `cell + best neighbour result` and take the maximum over all starts.

---

### M14 · All Paths From Source to Target

**🔗 [LC 797 — All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/)** · Medium
**Pattern:** Graph DFS | **Companies:** Amazon, Google

**Hint:** The graph is a DAG, so no visited set is needed. DFS from node 0 with a path list; when you reach `n - 1`, copy the path into the results. Add a node before recursing and remove it after.

---

### M15 · Restore IP Addresses

**🔗 [LC 93 — Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/)** · Medium
**Pattern:** String Segmenting | **Companies:** Amazon, Google, Meta

**Hint:** Place 3 dots with backtracking: at each step take the next 1–3 digits as a segment. A segment is valid if it's ≤ 255 and has no leading zero (unless it is exactly "0"). Stop when you have 4 segments and have used every digit.

---

## 🔴 Hard Tier (5 Problems)

_5 Advanced Problems._

### H1 · N-Queens

**🔗 [LC 51 — N-Queens](https://leetcode.com/problems/n-queens/)** · Hard
**Pattern:** Constraint Backtracking | **Companies:** Google, Amazon, Meta

**Hint:** The classic backtracking problem. Use sets for columns, row-sum, and row-diff diagonals.

---

### H2 · Sudoku Solver

**🔗 [LC 37 — Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)** · Hard
**Pattern:** Constraint Backtracking | **Companies:** Google, Amazon, Uber

**Hint:** Find the next empty cell, try digits 1–9 that don't clash with the row, column or 3×3 box (track these with boolean arrays for O(1) checks), recurse, and undo on failure. Return `true` as soon as the board is full so the solved state isn't undone.

---

### H3 · Word Break II

**🔗 [LC 140 — Word Break II](https://leetcode.com/problems/word-break-ii/)** · Hard
**Pattern:** Backtracking + Memoization | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Recurse on the suffix starting at `i`: for every dictionary word that is a prefix, combine it with each sentence of the rest. Memoise `i → list of sentences` so each suffix is solved once.

---

### H4 · Expression Add Operators

**🔗 [LC 282 — Expression Add Operators](https://leetcode.com/problems/expression-add-operators/)** · Hard
**Pattern:** Expression Backtracking | **Companies:** Google, Meta, Amazon

**Hint:** Backtrack over every split of the digit string, carrying `value` and `prev` (the last operand). For `*`, undo the last operand: `value - prev + prev * cur`. Skip operands with a leading zero and use `long` for the running value.

---

### H5 · Unique Paths III

**🔗 [LC 980 — Unique Paths III](https://leetcode.com/problems/unique-paths-iii/)** · Hard
**Pattern:** Grid Backtracking | **Companies:** Amazon, Google, Adobe

**Hint:** Count the empty cells first. DFS from the start, marking cells visited and unmarking on the way back. A path counts only if it reaches the end having visited every non-obstacle cell. The same template solves Rat in a Maze.

---

## 📊 Complexity Analysis Exercises

Trace the recursion tree and find Time & Space complexity.

```psuedocode
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
// N-Queens on an N×N board

// Snippet 7
// Sudoku Solver (worst case vs average case)

// Snippet 8
// Fibonacci with memoization

// Snippet 9
function work(n):
    if n ≤ 1: return
    for i from 0 to n - 1: work(n - 1)

// Snippet 10
// Traversing a perfectly balanced binary tree of height H
```

**Complexity Answers:**

1. **O(n)** Time (n + n/2 + n/4... = 2n), O(log n) Space (Stack depth).
2. **O(2ⁿ)** Time, O(n) Space.
3. **O(2ⁿ \* n)** Time. 2ⁿ subsets, n work per subset.
4. **O(n! \* n)** Time. n! permutations, n work per result.
5. **O(n)** Time, O(n) Space.
6. **O(n!)** Time. Each queen limits the column for the next.
7. **O(9^D)** where D is empty cells.
8. **O(n)** Time, O(n) Space.
9. **O(n!)** Time.
10. **O(2ᴴ)** Time, O(H) Space.

---

## 🔍 Self-Assessment — True / False

1. Base case is optional in recursion if the input is always positive. → **False** (leads to infinite recursion).
2. Recursion always uses more memory than iteration due to stack frames. → **True** (unless Tail Call Optimization
   exists).
3. Backtracking is essentially systematic "trial and error". → **True**.
4. Memoization converts a recursive problem to O(n) space always. → **False** (Depends on state variables).
5. In backtracking, "unvisiting" a node is the core step that makes it different from simple DFS. → **True**.
6. Recursion stack limit can be changed in JVM flags. → **True**.
7. Divide and Conquer and Dynamic Programming mean the same thing. → **False** (DP has overlapping subproblems).
8. Every recursive solution can be written iteratively. → **True** (Church-Turing thesis).

---

## 🧠 Conceptual Check

1. **State Space Tree**: What is a state space tree in the context of N-Queens? How does "pruning" change the number of
   visited nodes?
2. **Stack Overflow**: Why does `int[] a = new int[1000000]` inside a recursive method not cause `StackOverflowError`
   immediately, while nesting 1 million depth does? (Hint: Stack stores reference, Heap stores array).
3. **Memoization vs Tabulation**: Explain Top-Down vs Bottom-Up. Which one is closer to pure recursion?
4. **Permutation vs Subset**: What is the structural difference in the recursion tree between a Permutation generator
   (swapping) and a Subset generator (pick/don't pick)?
5. **Tail Recursion**: What is Tail Call Optimization (TCO)? Does Java support it natively?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                         |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [N-Queens](https://leetcode.com/problems/n-queens/), [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/), [Word Break II](https://leetcode.com/problems/word-break-ii/), [Expression Add Operators](https://leetcode.com/problems/expression-add-operators/)                                         |
| **Google**    | [N-Queens](https://leetcode.com/problems/n-queens/), [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/), [Word Break II](https://leetcode.com/problems/word-break-ii/), [Expression Add Operators](https://leetcode.com/problems/expression-add-operators/)                                         |
| **Meta**      | [N-Queens](https://leetcode.com/problems/n-queens/), [Word Break II](https://leetcode.com/problems/word-break-ii/), [Expression Add Operators](https://leetcode.com/problems/expression-add-operators/), [Subsets](https://leetcode.com/problems/subsets/)                                                     |
| **Microsoft** | [Subsets](https://leetcode.com/problems/subsets/), [Permutations](https://leetcode.com/problems/permutations/), [Combinations](https://leetcode.com/problems/combinations/), [Word Search](https://leetcode.com/problems/word-search/)                                                                         |
| **Uber**      | [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/), [Word Break II](https://leetcode.com/problems/word-break-ii/), [Combination Sum](https://leetcode.com/problems/combination-sum/), [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) |

---

## ✅ Completion Checklist

- [ ] All 15 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can draw the recursion tree for a small input before coding
- [ ] I can write the choose → explore → un-choose backtracking template from memory

---

**← [Lecture 4 · Java 8+ Modern Features](../Lecture4/Assignment.md)** &nbsp;·&nbsp; **[Lecture 6 · Bit Manipulation](../Lecture6/Assignment.md) →**
