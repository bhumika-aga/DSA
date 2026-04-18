# 🧮 Assignment 14 — Matrix Problems

> **Lecture:** Topic 14 — Matrix Problems
> **Topic Count:** 14 of 30 — Phase 2 Core Data Structures
> **Duration:** 4 Days
> **Core Problems:** 24 (5 Easy · 14 Medium · 5 Hard)
> **Goal:** Master the 4 matrix patterns — Boundary Traversal, In-Place State Machine, Grid DFS/BFS, and 2D Binary Search — and apply them to the most frequently asked FAANG matrix problems.

---

## 📊 Topic Overview

Every matrix problem is ultimately one of four patterns. Before writing any code, identify which pattern applies:

| Signal Phrase                              | Pattern                        |
| ------------------------------------------ | ------------------------------ |
| "spiral order", "layer by layer"           | Boundary Traversal             |
| "in place", "O(1) space" + state changes   | In-Place State Machine         |
| "connected", "island", "reach", "distance" | Grid DFS or BFS                |
| "sorted rows and columns", "find target"   | 2D Binary Search / Corner Walk |

---

## 🟢 Easy Tier (Foundations)

_Build fluency with grid indexing, bounds checking, and basic traversal._

1. **[Flood Fill](https://leetcode.com/problems/flood-fill/) (LC 733)** — The simplest DFS on a grid. Foundation for all flood-fill variants. `[Pattern: Grid DFS]`
2. **[Island Perimeter](https://leetcode.com/problems/island-perimeter/) (LC 463)** — Count exposed edges of a single island without DFS. `[Pattern: Grid Counting]`
3. **[Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/) (LC 1572)** — Index arithmetic on diagonals. `[Pattern: Traversal]`
4. **[Search a 2D Matrix I](https://leetcode.com/problems/search-a-2d-matrix/) (LC 74)** — Fully sorted matrix → treat as 1D binary search. `[Pattern: 2D Binary Search]`
5. **[Count Negative Numbers in Sorted Matrix](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/) (LC 1351)** — Corner walk variant for counting. `[Pattern: Corner Walk]`

---

## 🟡 Medium Tier (Core Patterns)

_Each problem requires recognising and applying one of the four core patterns._

1. **[Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) (LC 54)** — Four-pointer boundary shrink. `[Company: Amazon · Google] [Pattern: Boundary Traversal]`
2. **[Rotate Image](https://leetcode.com/problems/rotate-image/) (LC 48)** — Transpose + reverse each row. `[Company: Microsoft · Amazon] [Pattern: In-Place]`
3. **[Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/) (LC 73)** — Use first row/col as sentinels. O(1) space. `[Company: Microsoft · Amazon] [Pattern: In-Place State Machine]`
4. **[Number of Islands](https://leetcode.com/problems/number-of-islands/) (LC 200)** — Flood-fill DFS to sink islands. `[Company: Amazon · Google · Meta] [Pattern: Grid DFS]`
5. **[01 Matrix](https://leetcode.com/problems/01-matrix/) (LC 542)** — Multi-source BFS from all 0-cells simultaneously. `[Company: Google · Amazon] [Pattern: Multi-Source BFS]`
6. **[Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) (LC 994)** — Multi-source BFS with minute-level tracking. `[Company: Amazon] [Pattern: Multi-Source BFS]`
7. **[Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/) (LC 240)** — Top-right corner walk O(m+n). `[Company: Google · Microsoft] [Pattern: 2D Binary Search]`
8. **[Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/) (LC 59)** — Fill a spiral (reverse of LC 54). `[Pattern: Boundary Traversal]`
9. **[Max Area of Island](https://leetcode.com/problems/max-area-of-island/) (LC 695)** — DFS counting cells per island, track maximum. `[Pattern: Grid DFS]`
10. **[Clone Graph](https://leetcode.com/problems/clone-graph/) (LC 133)** — BFS with HashMap tracking original → clone. `[Company: Meta] [Pattern: Graph BFS]`
11. **[Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/) (LC 417)** — Reverse BFS from both oceans; intersection = answer. `[Company: Google] [Pattern: Multi-Source BFS]`
12. **[Game of Life](https://leetcode.com/problems/game-of-life/) (LC 289)** — In-place state machine using sentinel encodings. `[Company: Amazon · LinkedIn] [Pattern: In-Place State Machine]`
13. **[Surrounded Regions](https://leetcode.com/problems/surrounded-regions/) (LC 130)** — DFS from boundary 'O' cells; everything else flips. `[Pattern: Grid DFS]`
14. **[Word Search](https://leetcode.com/problems/word-search/) (LC 79)** — DFS with backtracking + visited marking. `[Company: Amazon · Microsoft] [Pattern: Grid DFS + Backtrack]`

---

## 🔴 Challenge Zone (Mastery)

_Requires combining multiple patterns or advanced BFS state management._

1. **[Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/) (LC 1091)** — BFS shortest path allowing 8-directional movement. `[Pattern: Grid BFS]`
2. **[Walls and Gates](https://leetcode.com/problems/walls-and-gates/) (LC 286)** — Multi-source BFS from all gates (0-cells) to find distances. `[Company: Facebook/Meta] [Pattern: Multi-Source BFS]`
3. **[Jump Game III](https://leetcode.com/problems/jump-game-iii/) (LC 1306)** — BFS reachability on 1D array treated as graph. `[Pattern: Graph BFS]`
4. **[Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/) (LC 64)** — DP on grid (preview of L21 DP lecture). `[Company: Google] [Pattern: Grid DP]`
5. **[Trapping Rain Water II](https://leetcode.com/problems/trapping-rain-water-ii/) (LC 407)** — Min-heap BFS from boundary inward. `[Company: Google · Amazon] [Pattern: Heap + BFS]`

---

## 📊 Conceptual Check

Answer these without looking at code:

1. **Bounds checking:** Write the standard `if (r < 0 || r >= m || c < 0 || c >= n)` guard from memory. Why should this be the **first** check in any DFS function?
2. **DFS vs BFS on grids:** When must you use BFS instead of DFS? (Hint: what does BFS guarantee that DFS doesn't?)
3. **Multi-source BFS:** Why is multi-source BFS O(m×n) while doing a separate BFS from every source would be O((m×n)²)?
4. **In-place tricks:** In Set Matrix Zeroes, why do we need to handle the first row and column separately with boolean flags?
5. **Corner walk:** In Search 2D Matrix II, why does starting from the top-right corner work but the top-left or bottom-right corner does not?

---

## 🏢 Company Focus

| Company           | Key Problem(s)                                                                                                                                                                                                                |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**        | [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/), [Search 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/), [01 Matrix](https://leetcode.com/problems/01-matrix/) |
| **Amazon**        | [Number of Islands](https://leetcode.com/problems/number-of-islands/), [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/), [Word Search](https://leetcode.com/problems/word-search/)                           |
| **Meta/Facebook** | [Walls and Gates](https://leetcode.com/problems/walls-and-gates/), [Clone Graph](https://leetcode.com/problems/clone-graph/), [Number of Islands](https://leetcode.com/problems/number-of-islands/)                           |
| **Microsoft**     | [Rotate Image](https://leetcode.com/problems/rotate-image/), [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/), [Search 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)               |

---

**Next Topic**: Topic 15 — Trees (Binary Trees & BST) →
