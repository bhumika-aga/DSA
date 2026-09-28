# 🧱 Assignment 26 — Dynamic Programming II — Grids & Strings

> **Lecture:** 33 of 45 — Dynamic Programming II — Grids & Strings
> **Phase:** 4 — Dynamic Programming
> **Estimated Time:** 7 days · **Total Problems:** 30 (10 Easy · 15 Medium · 5 Hard)
> **Goal:** One table, two indices: say what dp`[i][j]` means, draw the arrows, and the loops write themselves.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                  | Pattern          | Move                                        |
| -------------------------------------- | ---------------- | ------------------------------------------- |
| "paths / minimum cost through a grid"  | Grid Path DP     | `dp[i][j]` from its top and left neighbours |
| "common between two sequences"         | Match / Mismatch | diagonal + 1, or the better of two drops    |
| "turn one string into another"         | Edit Distance    | three transitions, `min` of the neighbours  |
| "palindromic substring / subsequence"  | Substring DP     | iterate by length, ends inward              |
| the answer depends on what comes after | Fill Backwards   | start from the last cell                    |
| no fixed order — paths follow values   | Memoised DFS     | tabulation cannot order the states          |

---

## 🟢 Easy Tier (10 Problems)

_Grid and string warm-ups: scans, counts and rotations before the tables arrive._

### E1 · Longest Palindrome

**🔗 [LC 409 — Longest Palindrome](https://leetcode.com/problems/longest-palindrome/)** · Easy
**Pattern:** Character Counting | **Companies:** Amazon, Google

**Hint:** Every character with an even count contributes fully; odd counts contribute all but one, plus a single centre. No table needed — but note it is the greedy cousin of the palindrome DP.

---

### E2 · Maximum Number of Balloons

**🔗 [LC 1189 — Maximum Number of Balloons](https://leetcode.com/problems/maximum-number-of-balloons/)** · Easy
**Pattern:** Frequency Bottleneck | **Companies:** Amazon

**Hint:** Count the letters of "balloon", halving the counts of l and o. The answer is the smallest ratio — the same bottleneck reasoning knapsack problems use.

---

### E3 · Check If a Word Occurs As a Prefix of Any Word in a Sentence

**🔗 [LC 1455 — Check If a Word Occurs As a Prefix of Any Word in a Sentence](https://leetcode.com/problems/check-if-a-word-occurs-as-a-prefix-of-any-word-in-a-sentence/)** · Easy
**Pattern:** Prefix Check | **Companies:** Amazon

**Hint:** Split the sentence and test each word with a prefix comparison. Return the 1-based index of the first match.

---

### E4 · Largest 3-Same-Digit Number in String

**🔗 [LC 2264 — Largest 3-Same-Digit Number in String](https://leetcode.com/problems/largest-3-same-digit-number-in-string/)** · Easy
**Pattern:** Fixed Window Scan | **Companies:** Amazon

**Hint:** Check every window of three characters for equality and keep the largest such string. The simplest possible substring scan.

---

### E5 · Count Asterisks

**🔗 [LC 2315 — Count Asterisks](https://leetcode.com/problems/count-asterisks/)** · Easy
**Pattern:** Toggle a Flag | **Companies:** Amazon

**Hint:** Walk the string flipping a boolean at each `|`. Count asterisks only while outside a pair — a one-variable state machine.

---

### E6 · Lucky Numbers in a Matrix

**🔗 [LC 1380 — Lucky Numbers in a Matrix](https://leetcode.com/problems/lucky-numbers-in-a-matrix/)** · Easy
**Pattern:** Row Minimum, Column Maximum | **Companies:** Amazon

**Hint:** Collect the minimum of each row and the maximum of each column; a lucky number is in both sets. Two passes over the grid.

---

### E7 · Cells with Odd Values in a Matrix

**🔗 [LC 1252 — Cells with Odd Values in a Matrix](https://leetcode.com/problems/cells-with-odd-values-in-a-matrix/)** · Easy
**Pattern:** Row and Column Counts | **Companies:** Amazon

**Hint:** Do not build the matrix. Count how many increments hit each row and column; a cell is odd when exactly one of its two counts is odd.

---

### E8 · Flipping an Image

**🔗 [LC 832 — Flipping an Image](https://leetcode.com/problems/flipping-an-image/)** · Easy
**Pattern:** In-Place Two Pointers | **Companies:** Amazon, Google

**Hint:** Reverse each row with two pointers while inverting, so it is one pass per row. Watch the middle element on odd widths.

---

### E9 · Available Captures for Rook

**🔗 [LC 999 — Available Captures for Rook](https://leetcode.com/problems/available-captures-for-rook/)** · Easy
**Pattern:** Directional Scan | **Companies:** Amazon

**Hint:** Find the rook, then walk in each of the four directions until a piece or the edge stops you. The 4-direction template from Lecture 17.

---

### E10 · Determine Whether Matrix Can Be Obtained By Rotation

**🔗 [LC 1886 — Determine Whether Matrix Can Be Obtained By Rotation](https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation/)** · Easy
**Pattern:** Rotate and Compare | **Companies:** Amazon

**Hint:** Rotate the matrix 90° up to three times, comparing each time. Rotation is `result[j][n-1-i] = mat[i][j]`.

---

## 🟡 Medium Tier (15 Problems)

_The two workhorses — grid paths and the match/mismatch family — plus the palindrome table._

### M1 · Unique Paths II

**🔗 [LC 63 — Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)** · Medium
**Pattern:** Grid Path DP | **Companies:** Amazon, Google, Microsoft

**Hint:** Each cell is the sum of the cell above and the cell to the left; an obstacle is 0, which then blocks everything behind it. One rolling row suffices.

---

### M2 · Longest Common Subsequence

**🔗 [LC 1143 — Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)** · Medium
**Pattern:** Two-String DP | **Companies:** Amazon, Google, Meta

**Hint:** Match → `dp[i-1][j-1] + 1`; mismatch → the better of dropping one character from either string. Remember the index offset.

---

### M3 · Edit Distance

**🔗 [LC 72 — Edit Distance](https://leetcode.com/problems/edit-distance/)** · Medium
**Pattern:** Two-String DP | **Companies:** Google, Amazon, Meta

**Hint:** Same skeleton with `min`, plus real base cases: row 0 and column 0 count up. Diagonal is replace, up is delete, left is insert.

---

### M4 · Longest Palindromic Subsequence

**🔗 [LC 516 — Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/)** · Medium
**Pattern:** Substring DP | **Companies:** Amazon, Google, Meta

**Hint:** Equal ends add 2 to the inner substring's answer. Fill by increasing length so `dp[i+1][j-1]` already exists. (It is also the LCS of s with its reverse.)

---

### M5 · Palindromic Substrings

**🔗 [LC 647 — Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)** · Medium
**Pattern:** Substring DP or Expand | **Companies:** Amazon, Google

**Hint:** Either fill a boolean table by length and count the trues, or expand around all 2n−1 centres in O(1) space.

---

### M6 · Interleaving String

**🔗 [LC 97 — Interleaving String](https://leetcode.com/problems/interleaving-string/)** · Medium
**Pattern:** Two-String Grid | **Companies:** Google, Amazon

**Hint:** `dp[i][j]` asks whether the first `i + j` characters of s3 can be built from `i` of s1 and `j` of s2. Check the length sum first and reject early.

---

### M7 · Delete Operation for Two Strings

**🔗 [LC 583 — Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/)** · Medium
**Pattern:** LCS Identity | **Companies:** Amazon, Google

**Hint:** The answer is `n + m − 2 × LCS(a, b)`. Deriving that identity is the whole problem; the table is the one you already wrote.

---

### M8 · Maximum Length of Repeated Subarray

**🔗 [LC 718 — Maximum Length of Repeated Subarray](https://leetcode.com/problems/maximum-length-of-repeated-subarray/)** · Medium
**Pattern:** LCS with a Reset | **Companies:** Amazon, Google

**Hint:** Same table, but a mismatch resets the cell to 0 instead of taking a maximum — that is what turns subsequence into substring. Track the best cell, not the last.

---

### M9 · Uncrossed Lines

**🔗 [LC 1035 — Uncrossed Lines](https://leetcode.com/problems/uncrossed-lines/)** · Medium
**Pattern:** LCS in Disguise | **Companies:** Amazon, Google

**Hint:** Uncrossed lines cannot cross, so they are exactly a common subsequence. Run LCS on the two number arrays unchanged.

---

### M10 · Minimum Falling Path Sum

**🔗 [LC 931 — Minimum Falling Path Sum](https://leetcode.com/problems/minimum-falling-path-sum/)** · Medium
**Pattern:** Row Rolling | **Companies:** Amazon, Google

**Hint:** `dp[j]` is the best falling path ending in column `j`. Each new row takes the minimum of the three cells above, clamped at the edges.

---

### M11 · Triangle

**🔗 [LC 120 — Triangle](https://leetcode.com/problems/triangle/)** · Medium
**Pattern:** Bottom-Up Triangle | **Companies:** Amazon, Google, Meta

**Hint:** Fill from the bottom row upward: each cell adds the smaller of its two children. The top cell is the answer, in O(n) space.

---

### M12 · Count Square Submatrices with All Ones

**🔗 [LC 1277 — Count Square Submatrices with All Ones](https://leetcode.com/problems/count-square-submatrices-with-all-ones/)** · Medium
**Pattern:** Square Extension | **Companies:** Amazon, Google

**Hint:** `dp[i][j]` is the size of the largest square with its bottom-right corner here: `1 + min(top, left, diagonal)` when the cell is 1. Summing the table counts all squares.

---

### M13 · Maximal Square

**🔗 [LC 221 — Maximal Square](https://leetcode.com/problems/maximal-square/)** · Medium
**Pattern:** Square Extension | **Companies:** Amazon, Google, Meta

**Hint:** Same recurrence as counting squares, but track the maximum side and square it. The `min` of three neighbours is what forces a full square.

---

### M14 · Minimum Path Cost in a Grid

**🔗 [LC 2304 — Minimum Path Cost in a Grid](https://leetcode.com/problems/minimum-path-cost-in-a-grid/)** · Medium
**Pattern:** Grid Path with Move Costs | **Companies:** Amazon, Google

**Hint:** `dp[i][j]` is the cheapest way to reach this cell; each transition adds both the move cost and the destination's value. Rows depend only on the row above.

---

### M15 · Where Will the Ball Fall

**🔗 [LC 1706 — Where Will the Ball Fall](https://leetcode.com/problems/where-will-the-ball-fall/)** · Medium
**Pattern:** Simulate per Column | **Companies:** Amazon, Google

**Hint:** Each ball moves independently: follow it row by row, checking that the current board and its neighbour form a valid V. It is grid DP with one state per ball.

---

## 🔴 Hard Tier (5 Problems)

_Pattern matching, counting variants, reversed fills and memoised DFS._

### H1 · Regular Expression Matching

**🔗 [LC 10 — Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/)** · Hard
**Pattern:** Two-String DP with Star | **Companies:** Google, Amazon, Meta

**Hint:** Treat `x*` as one unit with two options: zero occurrences (skip two pattern characters) or one more (if the character matches). Seed row 0 for patterns like `a*b*`.

---

### H2 · Distinct Subsequences

**🔗 [LC 115 — Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/)** · Hard
**Pattern:** Count the Ways | **Companies:** Google, Amazon

**Hint:** `dp[i][j]` counts how many ways the first `i` characters of s contain the first `j` of t. On a match add both `dp[i-1][j-1]` and `dp[i-1][j]`; otherwise only the latter.

---

### H3 · Dungeon Game

**🔗 [LC 174 — Dungeon Game](https://leetcode.com/problems/dungeon-game/)** · Hard
**Pattern:** Reverse Grid DP | **Companies:** Google, Amazon, Microsoft

**Hint:** Fill from the bottom-right: the health needed here is `max(1, min(right, down) − value)`. A forward pass cannot know what lies ahead.

---

### H4 · Longest Increasing Path in a Matrix

**🔗 [LC 329 — Longest Increasing Path in a Matrix](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/)** · Hard
**Pattern:** Memoised DFS | **Companies:** Google, Amazon, Meta

**Hint:** There is no fixed fill order, because paths follow increasing values. Memoise a DFS from every cell; each cell is computed once.

---

### H5 · Minimum Insertion Steps to Make a String Palindrome

**🔗 [LC 1312 — Minimum Insertion Steps to Make a String Palindrome](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/)** · Hard
**Pattern:** Palindrome Identity | **Companies:** Google, Amazon

**Hint:** The answer is `n − longest palindromic subsequence`, which is the LCS of s with its reverse. Recognising the identity avoids inventing a new table.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — unique paths on an m × n grid

// Snippet 2 — the same, keeping only one row

// Snippet 3 — longest common subsequence of lengths n and m

// Snippet 4 — edit distance of lengths n and m

// Snippet 5 — longest palindromic substring by expanding around centres

// Snippet 6 — palindromic substrings table, iterated by length
```

**Complexity Answers:**

1. **O(m · n)** time and space.
2. **O(m · n)** time, **O(n)** space.
3. **O(n · m)**.
4. **O(n · m)**.
5. **O(n²)** time, O(1) space.
6. **O(n²)** time and space.

---

## 🔍 Self-Assessment — True / False

1. Grid DP cells can be filled row by row from the top-left. → **True** — each depends on the cell above and the one to the left
2. A 2D DP table can always be reduced to one row. → **False** — only when each row depends solely on the previous one
3. Edit distance takes the minimum of insert, delete and replace. → **True**
4. Longest common subsequence and longest common substring use the same recurrence. → **False** — a substring must be contiguous, so a mismatch resets it to 0
5. Palindrome DP should be filled in order of length. → **True** — each range needs its shorter inner range
6. The first row and column of a grid DP are base cases. → **True**

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Loop order:** For each of Unique Paths, Dungeon Game and Longest Palindromic Subsequence, say which cells `dp[i][j]` reads and what order that forces.
2. **Offsets:** Why does the two-string table have `n + 1` rows, and which characters does `dp[i][j]` compare?
3. **Edit transitions:** Name the edit each neighbour represents, and describe how to rebuild the edit sequence.
4. **Substring vs subsequence:** Longest Palindromic Substring and Subsequence need different methods. What is the difference, and which one expands around centres?
5. **Identities:** Express Delete Operation for Two Strings and Minimum Insertions to Make a Palindrome in terms of LCS.
6. **Rolling:** When can a 2D table be reduced to one row, and what do you give up by doing it?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Available Captures for Rook](https://leetcode.com/problems/available-captures-for-rook/), [Cells with Odd Values in a Matrix](https://leetcode.com/problems/cells-with-odd-values-in-a-matrix/), [Check If a Word Occurs As a Prefix of Any Word in a Sentence](https://leetcode.com/problems/check-if-a-word-occurs-as-a-prefix-of-any-word-in-a-sentence/), [Count Asterisks](https://leetcode.com/problems/count-asterisks/)               |
| **Google**    | [Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/), [Minimum Insertion Steps to Make a String Palindrome](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/), [Count Square Submatrices with All Ones](https://leetcode.com/problems/count-square-submatrices-with-all-ones/), [Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/) |
| **Meta**      | [Longest Increasing Path in a Matrix](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/), [Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/), [Edit Distance](https://leetcode.com/problems/edit-distance/), [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)                                                                                   |
| **Microsoft** | [Dungeon Game](https://leetcode.com/problems/dungeon-game/), [Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)                                                                                                                                                                                                                                                                                                                 |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can derive LCS, edit distance and the palindrome table from one skeleton
- [ ] I can choose the fill direction from the dependencies rather than by trial and error

---

**← [Lecture 32 · Dynamic Programming I — Foundations & 1D](../Lecture32/Assignment.md)** &nbsp;·&nbsp; **[Lecture 34 · Dynamic Programming III — Knapsack & Subsets](../Lecture34/Assignment.md) →**
