# ↩️ Assignment 24 — Backtracking — Systematic Search

> **Lecture:** 24 of 45 — Backtracking — Systematic Search
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 4 days · **Total Problems:** 19 (1 Easy · 13 Medium · 5 Hard)
> **Goal:** Recognise the two decision trees behind every "return all" problem, write choose → explore → un-choose from memory, and prune before you explore.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                      | Pattern                 | Move                                     |
| ------------------------------------------ | ----------------------- | ---------------------------------------- |
| "return all subsets / subsequences"        | Include / Exclude       | two branches per element, 2ⁿ leaves      |
| "return all arrangements / orderings"      | Permutations            | used[] array or swap; n! leaves          |
| "choose k", "sum to target"                | Combinations            | start index; prune when over target      |
| the same element may be reused             | Combinations with reuse | recurse with i, not i + 1                |
| the input has duplicates, answers must not | Sort + skip             | skip when i > start and a[i] = a[i−1]    |
| "split the string into valid pieces"       | Partitioning            | try every cut, recurse on the rest       |
| "paths in a grid / maze / board"           | Grid backtracking       | mark, recurse in 4 directions, unmark    |
| a board with rules (queens, digits)        | Constraint backtracking | check the rule before placing, not after |

---

## 🟢 Easy Tier (1 Problem)

_The include/exclude shape with no LeetCode wrapper. Print every subsequence of a short array by hand before writing code._

### E1 · Print Subsequences ("Pick/Don't Pick")

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Include / Exclude (Subsets) | **Companies:** Amazon, Google, Adobe

**Task:** Given "abc", print all 2³ = 8 subsequences. This is the **most important pattern** for backtracking.

---

## 🟡 Medium Tier (13 Problems)

_The working set. For each one, name the shape first — include/exclude, arrange-all, or fill-the-slots — then decide what "un-choose" means._

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

**Hint:** Find if word exists in a 2D grid. Mark visited cell (e.g., set to '#'), search neighbours, then **unmark** (Backtrack).

---

### M9 · Letter Combinations of a Phone Number

**🔗 [LC 17 — Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)** · Medium
**Pattern:** Mapping + Recursion | **Companies:** Google, Amazon, Meta, Uber

**Hint:** E.g., 2="abc", 3="def". Return all strings "ad", "ae", "af"...

---

### M10 · Generate Parentheses

**🔗 [LC 22 — Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)** · Medium
**Pattern:** Count-based Backtracking | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Keep track of open and close counts. Only add `)` if `close < open`.

---

### M11 · Path with Maximum Gold

**🔗 [LC 1219 — Path with Maximum Gold](https://leetcode.com/problems/path-with-maximum-gold/)** · Medium
**Pattern:** Grid DFS + Max result | **Companies:** Amazon, Google

**Hint:** From every cell with gold, DFS in 4 directions, temporarily setting the cell to 0 so a path can't revisit it and restoring it on the way back. Return `cell + best neighbour result` and take the maximum over all starts.

---

### M12 · All Paths From Source to Target

**🔗 [LC 797 — All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/)** · Medium
**Pattern:** Graph DFS | **Companies:** Amazon, Google

**Hint:** The graph is a DAG, so no visited set is needed. DFS from node 0 with a path list; when you reach `n - 1`, copy the path into the results. Add a node before recursing and remove it after.

---

### M13 · Restore IP Addresses

**🔗 [LC 93 — Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/)** · Medium
**Pattern:** String Segmenting | **Companies:** Amazon, Google, Meta

**Hint:** Place 3 dots with backtracking: at each step take the next 1–3 digits as a segment. A segment is valid if it's ≤ 255 and has no leading zero (unless it is exactly "0"). Stop when you have 4 segments and have used every digit.

---

## 🔴 Hard Tier (5 Problems)

_Real constraints to prune against: a board, a grid you must fully cover, a dictionary, an arithmetic target._

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
**Pattern:** Backtracking + Memoisation | **Companies:** Google, Amazon, Meta, Uber

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

Draw the decision tree first, count its leaves, then multiply by the work done at each leaf.

```pseudocode
// Snippet 1
// All subsets of an array of size n, each copied into the result

// Snippet 2
// All permutations of an array of size n, each copied into the result

// Snippet 3
// All combinations of size k chosen from n elements

// Snippet 4
// N-Queens on an n × n board

// Snippet 5
// Sudoku Solver (worst case vs average case)

// Snippet 6
// Word Search: a word of length L on an m × n board

// Snippet 7
function gen(open, close, n):          // Generate Parentheses
    if open = n and close = n: record; return
    if open < n: gen(open + 1, close, n)
    if close < open: gen(open, close + 1, n)
```

**Complexity Answers:**

1. **O(n · 2ⁿ)** Time — 2ⁿ subsets, O(n) to copy each. O(n) stack.
2. **O(n · n!)** Time — n! permutations, O(n) to copy each. O(n) stack.
3. **O(k · C(n, k))** Time — C(n, k) results, O(k) to copy each.
4. **O(n!)** Time before pruning — each queen removes at least one column for the next row. O(n) stack.
5. **O(9ᴰ)** worst case, where D is the number of empty cells; constraint checks make the real tree tiny.
6. **O(m · n · 3ᴸ)** — start anywhere, then at most 3 new directions per step (you never go straight back).
7. **O(4ⁿ / √n)** — the n-th Catalan number of valid strings, each of length 2n. Not needed by heart; the point is that the constraint `close < open` keeps the tree far smaller than 2²ⁿ.

---

## 🔍 Self-Assessment — True / False

1. Backtracking is systematic trial and error. → **True** — it tries every candidate, but in an order that lets it abandon hopeless ones early.
2. In backtracking, un-choosing is what makes it different from a plain DFS. → **True** — DFS marks a node once; backtracking undoes the mark so another path can use it.
3. Pruning changes the worst-case complexity of backtracking. → **False** — it usually leaves the worst case alone and shrinks the typical case enormously.
4. Adding `path` directly to the result list is fine as long as you copy it at the end. → **False** — every entry is the same object, so they all change when `path` does.
5. Subsets and permutations of the same array produce the same number of results. → **False** — 2ⁿ versus n!; for n = 10 that is 1,024 versus 3,628,800.
6. If a problem asks only for the _number_ of valid arrangements, backtracking is the only option. → **False** — overlapping subproblems often make it dynamic programming.

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **State space tree**: What is the state space tree for N-Queens on a 4×4 board? How does pruning change the number of nodes you actually visit?
2. **Two shapes**: What is the structural difference between the recursion tree of a subset generator (pick / don't pick) and a permutation generator (fill each position)? Count the leaves of each for n = 3.
3. **The copy**: Why must you add a _copy_ of the current path to the results rather than the path itself? What does the result look like if you forget?
4. **Reuse**: In Combination Sum you recurse with `i`; in Combination Sum II you recurse with `i + 1`. Explain what each allows, using [2, 3] and target 4.
5. **Duplicates**: Why must the input be sorted before the "skip if equal to the previous element" rule works? Give an input where skipping without sorting fails.
6. **Backtracking or DP?**: Word Break asks _whether_ a split exists; Word Break II asks for _every_ split. Which one is dynamic programming and which is backtracking, and why?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                       |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Unique Paths III](https://leetcode.com/problems/unique-paths-iii/), [All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/), [Path with Maximum Gold](https://leetcode.com/problems/path-with-maximum-gold/), [Expression Add Operators](https://leetcode.com/problems/expression-add-operators/) |
| **Google**    | [Unique Paths III](https://leetcode.com/problems/unique-paths-iii/), [All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/), [Path with Maximum Gold](https://leetcode.com/problems/path-with-maximum-gold/), [N-Queens](https://leetcode.com/problems/n-queens/)                                 |
| **Meta**      | [Combination Sum II](https://leetcode.com/problems/combination-sum-ii/), [Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/), [Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/), [Subsets II](https://leetcode.com/problems/subsets-ii/)                                             |
| **Uber**      | [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/), [Word Break II](https://leetcode.com/problems/word-break-ii/), [Combination Sum](https://leetcode.com/problems/combination-sum/), [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)                                                                 |
| **Microsoft** | [Combinations](https://leetcode.com/problems/combinations/), [Permutations](https://leetcode.com/problems/permutations/), [Subsets](https://leetcode.com/problems/subsets/), [Word Search](https://leetcode.com/problems/word-search/)                                                                                                       |

---

## ✅ Completion Checklist

- [ ] All 1 Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name the shape of a backtracking problem before writing code
- [ ] I can write choose → explore → un-choose from memory
- [ ] I always add a copy of the path, and can explain why
- [ ] I can prune before recursing and estimate how much it saves

---

**← [Lecture 23 · Graphs III — MST, Bipartite & Bridges](../Lecture23/Assignment.md)** &nbsp;·&nbsp; **[Lecture 25 · Two Pointers & Sliding Window](../Lecture25/Assignment.md) →**
