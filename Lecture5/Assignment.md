# 📝 Assignment 05 — Recursion & Backtracking Masterclass

> **Lecture:** Topic 5 — Recursion & Backtracking
> **Topic Count:** 5 of 30 — Phase 1 Foundations
> **Duration:** 6 Days
> **Core Problems:** 40 (15 Easy · 15 Medium · 10 Hard) + 12 Challenge + 10 Complexity Exercises
> **Goal:** Master the "Divide & Conquer" thinking, recursive call-stack visualizing, and backtracking state-space pruning.

---

## 🗺️ Problem Map by Pattern

| Pattern / Topic             | Problems           |
| --------------------------- | ------------------ |
| Linear Recursion            | 01, 02, 03, 04, 05 |
| Divide & Conquer            | 06, 07, 08         |
| Include / Exclude (Subsets) | 09, 10, 11, 12     |
| Permutations (Swapping)     | 13, 14, 15         |
| Combinations (Math)         | 16, 17             |
| Backtracking (Grids)        | 18, 19, 20, 21, 22 |
| String Recursion            | 23, 24, 25         |
| Hard Constraints (Puzzles)  | 26, 27, 28, 29, 30 |
| Challenge Zone (FAANG)      | 31, 32, 33, 34, 35 |

---

## 🟢 Easy Tier — 15 Problems (Build the Recursion Tree)

### Problem 01 — Sum of First N Numbers

> 🔗 **Practice:** Write `sum(n)` recursively. Draw the call stack for `n=4`. Use `return n + sum(n-1)`. State the space complexity (O is NOT 1 here!).

### Problem 02 — Factorial & GCD

> 🔗 **Practice:** Implement `factorial(n)` and `gcd(a, b)` recursively. Why is recursion better than loops for Euclid's GCD?

### Problem 03 — Power Function (O(n))

> 🔗 **Practice:** Implement `pow(x, n)` as `x * pow(x, n-1)`. Then look at Topic 7 for how to do this in O(log n).

### Problem 04 — Reverse an Array (Two Pointers)

> 🔗 **Practice:** Use recursion to swap `arr[l]` and `arr[r]`, then call `reverse(l+1, r-1)`. Base case: `l >= r`.

### Problem 05 — Palindrome String check

> 🔗 **LeetCode:** [Check Palindrome (Recursively)](https://leetcode.com/problems/valid-palindrome/)
> **`[Pattern: Symmetrical Recursion]` `[Easy]`**
> Compare `s[0]` and `s[last]`, then recurse on the inner string.

### Problem 06 — Binary Search (Recursive)

> 🔗 **Practice:** Write the recursive version of Binary Search. What is the Space Complexity due to the call stack?

### Problem 07 — Merge Sort (Divide & Conquer)

> 🔗 **Practice:** Implement Merge Sort. Focus on the `merge()` step. Why does Merge Sort take O(n log n) time?

### Problem 08 — Quicksort (Partition Logic)

> 🔗 **Practice:** Implement Quicksort. Use the **Lomuto partition** or **Hoare partition**. Try to understand why the pivot choice determines the O(n²) worst case.

### Problem 09 — Print Subsequences ("Pick/Don't Pick")

> 🔗 **Practice:** Given "abc", print all 2³ = 8 subsequences. This is the **most important pattern** for backtracking.

### Problem 10 — Count Digits Recursively

> 🔗 **Practice:** `1 + countDigits(n/10)` if `n > 0`.

### Problem 11 — Check if Array is Sorted

> 🔗 **Practice:** `return (arr[0] <= arr[1]) && isSorted(rest of array)`.

### Problem 12 — Linear Search (Recursive)

> 🔗 **Practice:** Search index 0, then recurse.

### Problem 13 — Fibonacci (Naïve)

> 🔗 **Practice:** Implement `fib(n) = fib(n-1) + fib(n-2)`. Draw the recursion tree for `n=4`. Why are there 15 nodes for such a small input?

### Problem 14 — Sum of Digits

> 🔗 **Practice:** Extract `n % 10`, then recurse `n / 10`.

### Problem 15 — Josephus Problem (Easy Version)

> 🔗 **Practice:** `n` people in a circle, every `k`-th killed. Return survivors index. (Hint: `f(n, k) = (f(n-1, k) + k) % n`).

---

## 🟡 Medium Tier — 15 Problems (The Backtracking Template)

### Problem 16 — Subsets I (The Foundation)

> 🔗 **LeetCode:** [78. Subsets](https://leetcode.com/problems/subsets/)
> **`[Pattern: Include / Exclude]` `[Amazon] [Google]` `[Medium]`**
> Build all power sets. Use the template: `helper(index, currentList)`.

### Problem 17 — Subsets II (Duplicates)

> 🔗 **LeetCode:** [90. Subsets II](https://leetcode.com/problems/subsets-ii/)
> **`[Pattern: Sort + Skip Duplicates]` `[Medium]`**
> Same as above, but with duplicate numbers. Sort first, then skip `nums[i]` if `nums[i] == nums[i-1]`.

### Problem 18 — Permutations I

> 🔗 **LeetCode:** [46. Permutations](https://leetcode.com/problems/permutations/)
> **`[Pattern: Swapping / Visited Array]` `[Facebook/Meta]` `[Medium]`**
> Find all possible orderings of N distinct elements. O(n!).

### Problem 19 — Combinations (K from N)

> 🔗 **LeetCode:** [77. Combinations](https://leetcode.com/problems/combinations/)
> **`[Pattern: Range Recursion]` `[Medium]`**
> Return all combinations of k numbers from n.

### Problem 20 — Combination Sum I

> 🔗 **LeetCode:** [39. Combination Sum](https://leetcode.com/problems/combination-sum/)
> **`[Pattern: Unlimited Reuse]` `[Medium]`**
> Find all unique combinations that sum to target. You can reuse the same element.

### Problem 21 — Combination Sum II

> 🔗 **LeetCode:** [40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
> **`[Pattern: Single Use + Duplicates]` `[Medium]`**
> Each element used only once. Skip duplicates logic applied.

### Problem 22 — Palindrome Partitioning

> 🔗 **LeetCode:** [131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)
> **`[Pattern: Cut / Validation]` `[Amazon] [Netflix]` `[Medium]`**
> Partition string so every substring is a palindrome.

### Problem 23 — Word Search

> 🔗 **LeetCode:** [79. Word Search](https://leetcode.com/problems/word-search/)
> **`[Pattern: Grid Backtracking (DFS)]` `[Medium]`**
> Find if word exists in a 2D grid. Mark visited cell (e.g., set to '#'), search neighbors, then **unmark** (Backtrack).

### Problem 24 — Letter Combinations of a Phone Number

> 🔗 **LeetCode:** [17. Phone Number Combinations](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
> **`[Pattern: Mapping + Recursion]` `[Medium]`**
> E.g., 2="abc", 3="def". Return all strings "ad", "ae", "af"...

### Problem 25 — Binary Tree Paths

> 🔗 **LeetCode:** [257. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)
> **`[Pattern: Tree Traversal]` `[Medium]`**
> Return all paths from root to leaf. Pre-order traversal with a path tracker.

### Problem 26 — Target Sum

> 🔗 **LeetCode:** [494. Target Sum](https://leetcode.com/problems/target-sum/)
> **`[Pattern: +/- Choices]` `[Medium]`**
> Use `+` or `-` for each number to reach target.

### Problem 27 — Generate Parentheses

> 🔗 **LeetCode:** [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)
> **`[Pattern: Count-based Backtracking]` `[Medium]`**
> Keep track of open and close counts. Only add `)` if `close < open`.

### Problem 28 — Path with Maximum Gold

> 🔗 **LeetCode:** [1219. Path with Maximum Gold](https://leetcode.com/problems/path-with-maximum-gold/)
> **`[Pattern: Grid DFS + Max result]` `[Medium]`**
> Similar to Word Search, but track the running sum.

### Problem 29 — All Paths Source to Target

> 🔗 **LeetCode:** [797. All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/)
> **`[Pattern: Graph DFS]` `[Medium]`**
> Find all paths from node 0 to node n-1.

### Problem 30 — Restore IP Addresses

> 🔗 **LeetCode:** [93. Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/)
> **`[Pattern: String Segmenting]` `[Medium]`**

---

## 🔴 Challenge Zone — 10 Advanced Problems

### P31-40: The Expert Tier

- **P31: N-Queens** ([LC 51](https://leetcode.com/problems/n-queens/)) - The classic backtracking problem. Use sets for columns, row-sum, and row-diff diagonals.
- **P32: Sudoku Solver** ([LC 37](https://leetcode.com/problems/sudoku-solver/)) - Hard constraints. Return boolean to stop recursion immediately.
- **P33: Word Break II** ([LC 140](https://leetcode.com/problems/word-break-ii/)) - Backtracking + Memoization.
- **P34: Expression Add Operators** ([LC 282](https://leetcode.com/problems/expression-add-operators/)) - Complexity intensive.
- **P35: Rat in a Maze** ([GFG](https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)) - Standard FAANG interview question.

---

## 📊 Complexity Analysis Exercises — 10 Snippets

Trace the recursion tree and find Time & Space complexity.

```java
// Snippet 1
void recur(int n) {
    if (n <= 1) return;
    for (int i = 0; i < n; i++) System.out.println(i);
    recur(n / 2);
}

// Snippet 2
void solve(int n) {
    if (n <= 0) return;
    solve(n - 1);
    solve(n - 1);
}

// Snippet 3
// Generating all subsets of an array of size N

// Snippet 4
// Generating all permutations of an array of size N

// Snippet 5
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}

// Snippet 6
// N-Queens on an N*N board

// Snippet 7
// Sudoku Solver (Worst case vs Average case)

// Snippet 8
// Fibonacci with Memoization

// Snippet 9
void work(int n) {
    if (n <= 1) return;
    for (int i = 0; i < n; i++) work(n - 1);
}

// Snippet 10
// Traversing a perfectly balanced Binary Tree of height H
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

## ✅ Self-Assessment — True / False

1. Base case is optional in recursion if the input is always positive. → **False** (leads to infinite recursion).
2. Recursion always uses more memory than iteration due to stack frames. → **True** (unless Tail Call Optimization exists).
3. Backtracking is essentially systematic "trial and error". → **True**.
4. Memoization converts a recursive problem to O(n) space always. → **False** (Depends on state variables).
5. In backtracking, "unvisiting" a node is the core step that makes it different from simple DFS. → **True**.
6. Recursion stack limit can be changed in JVM flags. → **True**.
7. Divide and Conquer and Dynamic Programming mean the same thing. → **False** (DP has overlapping subproblems).
8. Every recursive solution can be written iteratively. → **True** (Church-Turing thesis).

---

## 🧠 Conceptual Mastery Questions

1. **State Space Tree**: What is a state space tree in the context of N-Queens? How does "pruning" change the number of visited nodes?
2. **Stack Overflow**: Why does `int[] a = new int[1000000]` inside a recursive method not cause `StackOverflowError` immediately, while nesting 1 million depth does? (Hint: Stack stores reference, Heap stores array).
3. **Memoization vs Tabulation**: Explain Top-Down vs Bottom-Up. Which one is closer to pure recursion?
4. **Permutation vs Subset**: What is the structural difference in the recursion tree between a Permutation generator (swapping) and a Subset generator (pick/don't pick)?
5. **Tail Recursion**: What is Tail Call Optimization (TCO)? Does Java support it natively?

---

Next: [Topic 6 — Bit Manipulation](../Lecture6/Assignment.md)
