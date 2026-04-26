# 🧮 Assignment 14 — Matrix Problems

> **Lecture:** Topic 14 — Matrix Problems
> **Phase:** 2 — Core Data Structures
> **Topic Count:** 14 of 30
> **Estimated Time:** 4 Days
> **Total Problems:** 24 (5 Easy · 14 Medium · 5 Hard)
> **Goal:** Master the 4 matrix patterns (Boundary Traversal, In-Place State Machine, Grid DFS/BFS, 2D Binary Search) and apply them to the most frequently asked FAANG matrix problems.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, identify which of the 4 patterns applies. Do this **within 30 seconds** of reading the problem:

| Signal Phrase in Problem                           | Pattern to Apply       | Core Algorithm       |
| -------------------------------------------------- | ---------------------- | -------------------- |
| "spiral order", "layer by layer", "peel"           | Boundary / Spiral Walk | 4-pointer shrink     |
| "in place", "O(1) space" + state changes           | In-Place State Machine | Sentinel encoding    |
| "connected cells", "island", "flood fill", "reach" | Grid DFS               | Recursive flood fill |
| "shortest distance", "nearest", "minimum time"     | Grid BFS               | Multi-source BFS     |
| "sorted rows and columns", "search in matrix"      | 2D Binary Search       | Corner walk O(m+n)   |

---

## 🟢 Easy Tier — Build Fluency (5 Problems)

_Goal: Get comfortable with grid indexing, bounds checking, and recognising the basic patterns._

---

### E1 · Flood Fill

**🔗 [LC 733 — Flood Fill](https://leetcode.com/problems/flood-fill/)**
**Pattern:** Grid DFS | **Companies:** Amazon, Adobe

**Problem:** Given a 2D image, a starting cell `(sr, sc)`, and a new colour, flood-fill the connected region starting from `(sr, sc)` with the new colour.

**Hint:** This is the simplest grid DFS. From the start cell, recursively spread to all 4-directional neighbours that have the **same original colour**. Mark them with the new colour as you go. Watch out for the edge case where `image[sr][sc] == color` already — return early to avoid infinite recursion.

**Why Easy?** Single-source DFS, no counting, no special state encoding. Pure flood fill skeleton.

---

### E2 · Island Perimeter

**🔗 [LC 463 — Island Perimeter](https://leetcode.com/problems/island-perimeter/)**
**Pattern:** Grid Counting | **Companies:** Goldman Sachs, Microsoft

**Problem:** Given a grid with exactly one island (no lakes), return the perimeter of the island.

**Hint:** For every land cell (`grid[r][c] == 1`), start with 4 sides. Subtract 1 for each neighbour that is also land (shared edge = not a perimeter edge). No DFS needed — just a nested loop and neighbour check.

**Formula:** `perimeter += 4 - (number of land neighbours)`

**Why Easy?** No recursion, no state tracking. Pure arithmetic.

---

### E3 · Matrix Diagonal Sum

**🔗 [LC 1572 — Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/)**
**Pattern:** Index Arithmetic | **Companies:** Microsoft

**Problem:** Given a square matrix, return the sum of all elements on the primary diagonal plus the secondary diagonal, counting the centre cell once if n is odd.

**Hint:** Primary diagonal: `matrix[i][i]`. Secondary diagonal: `matrix[i][n-1-i]`. If `n` is odd, subtract `matrix[n/2][n/2]` once to avoid double-counting the centre.

**Why Easy?** O(n) solution using a single loop and index arithmetic.

---

### E4 · Search a 2D Matrix I

**🔗 [LC 74 — Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)**
**Pattern:** 2D Binary Search | **Companies:** Amazon, Microsoft

**Problem:** Matrix is row-major sorted (last of row < first of next row). Search for a target in O(log(m\*n)).

**Hint:** The entire matrix is a sorted 1D array if you "unwrap" it. Use classic binary search with `mid = lo + (hi - lo) / 2`. Convert `mid` to 2D: `row = mid / n`, `col = mid % n`. This gives O(log(m\*n)).

**Why Easy?** Standard binary search with a simple index mapping trick.

---

### E5 · Count Negative Numbers in Sorted Matrix

**🔗 [LC 1351 — Count Negative Numbers in a Sorted Matrix](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/)**
**Pattern:** Corner Walk | **Companies:** Google

**Problem:** Given a matrix sorted descending in each row and column, count negatives efficiently.

**Hint:** Start at the **bottom-left corner**. If current cell is negative, all cells to its right in this row are also negative → add `n - c` to count and go up (`r--`). If non-negative, move right (`c++`). This is the corner walk from the bottom-left, giving O(m+n).

**Why Easy?** Classic corner walk applied to counting instead of searching.

---

## 🟡 Medium Tier — Core Interview Patterns (14 Problems)

_Each problem requires identifying and correctly applying one of the 4 core patterns. These are the most commonly asked matrix problems at FAANG companies._

---

### M1 · Spiral Matrix

**🔗 [LC 54 — Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)**
**Pattern:** Boundary Walk | **Companies:** Amazon, Google, Microsoft, Facebook

**Problem:** Return all elements of an m×n matrix in spiral order.

**Hint:** Maintain 4 pointers: `top`, `bottom`, `left`, `right`. Each round: traverse top row (left→right), right column (top→bottom), bottom row (right→left, **guard**: `if top <= bottom`), left column (bottom→top, **guard**: `if left <= right`). Shrink bounds after each traversal.

**Common mistake:** Forgetting the two guards causes double-counting in non-square matrices.

---

### M2 · Rotate Image

**🔗 [LC 48 — Rotate Image](https://leetcode.com/problems/rotate-image/)**
**Pattern:** In-Place Transformation | **Companies:** Amazon, Microsoft, Apple

**Problem:** Rotate an n×n matrix 90° clockwise in place using O(1) extra space.

**Hint:** Two-step trick: (1) **Transpose** — swap `matrix[i][j]` with `matrix[j][i]` for all `j > i`. (2) **Reverse each row** — standard two-pointer reversal. This works because rotating 90° CW maps `(r, c)` → `(c, n-1-r)`. Transpose gives `(c, r)`, reversing each row turns `r` into `n-1-r`.

**Follow-up variants:** Counter-clockwise = Transpose + reverse each **column**. 180° = reverse all rows + reverse each row.

---

### M3 · Set Matrix Zeroes

**🔗 [LC 73 — Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)**
**Pattern:** In-Place State Machine | **Companies:** Amazon, Microsoft, Goldman Sachs

**Problem:** If any cell is 0, set its entire row and column to 0. Do it in place with O(1) extra space.

**Hint:** Use the **first row and first column as sentinel arrays**. Two boolean flags (`row0`, `col0`) remember if those sentinels originally contained zeros. 4-pass algorithm: check sentinels → mark inner cells → zero out inner cells from sentinels → zero out sentinels if flagged.

**Common mistake:** Not handling row 0 / col 0 separately. If you zero them out first, you corrupt your own sentinel data.

---

### M4 · Number of Islands

**🔗 [LC 200 — Number of Islands](https://leetcode.com/problems/number-of-islands/)**
**Pattern:** Grid DFS (Flood Fill) | **Companies:** Amazon, Google, Meta, Bloomberg

**Problem:** Count connected groups of adjacent '1' cells in a grid of '1' (land) and '0' (water).

**Hint:** Scan every cell. When you find an unvisited '1', increment count and DFS to sink the entire island (mark all connected '1's as '2'). After DFS, that island will never be counted again.

**Interview follow-up:** "What if the grid is enormous?" → convert to iterative BFS to avoid stack overflow.

---

### M5 · 01 Matrix

**🔗 [LC 542 — 01 Matrix](https://leetcode.com/problems/01-matrix/)**
**Pattern:** Multi-Source BFS | **Companies:** Google, Amazon, Uber

**Problem:** Return a matrix where each cell contains its distance to the nearest 0.

**Hint:** Wrong approach: BFS from every 1-cell = O((m\*n)²). Right approach: **seed queue with ALL 0-cells** and BFS outward. Each 1-cell gets its distance from the first 0-source that reaches it (guaranteed nearest). Use `dist = -1` as the "unvisited" sentinel.

---

### M6 · Rotting Oranges

**🔗 [LC 994 — Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)**
**Pattern:** Multi-Source BFS with Time Tracking | **Companies:** Amazon, Google, Uber

**Problem:** Rotten oranges (2) spread to fresh (1) neighbours every minute. Return minimum minutes to rot all, or -1 if impossible.

**Hint:** Same multi-source BFS as M5, but track **BFS levels as minutes**. Count fresh oranges before BFS. After BFS, if `fresh > 0` → unreachable cells exist → return -1. Process queue level by level (use `int size = q.size()` before each round).

---

### M7 · Search a 2D Matrix II

**🔗 [LC 240 — Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)**
**Pattern:** Corner Walk O(m+n) | **Companies:** Google, Microsoft

**Problem:** Matrix has sorted rows (left→right) and sorted columns (top→bottom) independently. Search for target.

**Hint:** Start at **top-right corner**. If `curr == target` → found. If `curr > target` → go left (eliminate column). If `curr < target` → go down (eliminate row). Each step eliminates one row or column → at most m+n steps.

**Key insight:** Top-right is the unique corner where left = smaller (let us go left if too big) and down = larger (let us go down if too small). No other corner has this property.

---

### M8 · Spiral Matrix II

**🔗 [LC 59 — Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)**
**Pattern:** Boundary Walk (fill) | **Companies:** Amazon

**Problem:** Given n, construct an n×n matrix filled with numbers 1 to n² in spiral order.

**Hint:** Same 4-pointer logic as LC 54, but instead of reading cells you write into them. Use a counter that increments from 1 to n². Same two guards apply.

---

### M9 · Max Area of Island

**🔗 [LC 695 — Max Area of Island](https://leetcode.com/problems/max-area-of-island/)**
**Pattern:** Grid DFS with size tracking | **Companies:** Amazon, Google, DoorDash

**Problem:** Find the maximum area (cell count) of any island in the grid.

**Hint:** Same DFS flood fill as Number of Islands, but the DFS returns the **size** of the island it sinks. Track the maximum across all islands.

```java
int dfs(int r, int c) {
    if (out of bounds or not '1') return 0;
    mark visited;
    return 1 + dfs(r-1,c) + dfs(r+1,c) + dfs(r,c-1) + dfs(r,c+1);
}
```

---

### M10 · Pacific Atlantic Water Flow

**🔗 [LC 417 — Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/)**
**Pattern:** Reverse Multi-Source BFS/DFS | **Companies:** Google, Amazon

**Problem:** Water flows from higher-or-equal to lower cells. Find all cells that can drain to both Pacific (top/left edges) and Atlantic (bottom/right edges).

**Hint:** Reverse the flow. BFS/DFS from Pacific borders **going uphill** (visit only cells ≥ current height). Do the same from Atlantic borders. Cells reachable from **both** are the answer.

**Common mistake:** Flowing downhill from every cell = O((m\*n)²). Always reverse direction and BFS from boundaries.

---

### M11 · Game of Life

**🔗 [LC 289 — Game of Life](https://leetcode.com/problems/game-of-life/)**
**Pattern:** In-Place State Machine | **Companies:** Amazon, LinkedIn, Snapchat

**Problem:** Apply Conway's Game of Life rules to a binary grid in place. Cells live or die based on neighbour counts.

**Hint:** Encode intermediate states: use `2` for "was alive, now dead" and `-1` for "was dead, now alive". Apply rules using original values (treat 2 as 1 and -1 as 0 when counting neighbours). Second pass: convert 2→0 and -1→1.

**8-directional movement:** Use `int[][] dirs = {{-1,-1},{-1,0},{-1,1},{0,-1},{0,1},{1,-1},{1,0},{1,1}};`

---

### M12 · Surrounded Regions

**🔗 [LC 130 — Surrounded Regions](https://leetcode.com/problems/surrounded-regions/)**
**Pattern:** Grid DFS from boundary | **Companies:** Amazon, Microsoft

**Problem:** Capture all 'O' regions not connected to any border. Replace captured 'O's with 'X'.

**Hint:** Reverse thinking: any 'O' connected to the border **cannot** be captured. DFS from all border 'O' cells and mark them as safe (e.g., 'S'). Then flip all remaining 'O' → 'X' and all 'S' → 'O'.

---

### M13 · Word Search

**🔗 [LC 79 — Word Search](https://leetcode.com/problems/word-search/)**
**Pattern:** Grid DFS + Backtracking | **Companies:** Amazon, Microsoft, Google, Bloomberg

**Problem:** Given a grid and a word, return true if the word exists as a sequence of adjacent cells (4-directional, no reuse).

**Hint:** For each cell matching `word[0]`, DFS to match the rest of the word. Temporarily mark visited cells (e.g., `grid[r][c] = '#'`) before recursing, restore afterwards (backtracking). Return true as soon as the word is found.

**Optimisation:** If the last letter is rarer than the first, search the word backwards.

---

### M14 · Clone Graph

**🔗 [LC 133 — Clone Graph](https://leetcode.com/problems/clone-graph/)**
**Pattern:** BFS + HashMap | **Companies:** Meta, Amazon, Bloomberg

**Problem:** Given a reference to a node in a connected undirected graph, return a deep copy.

**Hint:** BFS from the start node. Use a `HashMap<Node, Node>` mapping original → clone. For each original node, create its clone if not already done, then connect all neighbour clones.

---

## 🔴 Hard Tier — FAANG Mastery (5 Problems)

_Combines multiple patterns or requires advanced BFS state management. These appear in on-site rounds at Google, Meta, and Amazon._

---

### H1 · Shortest Path in Binary Matrix

**🔗 [LC 1091 — Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)**
**Pattern:** BFS Shortest Path (8-directional) | **Companies:** Google, Amazon

**Problem:** Find the shortest clear path from top-left to bottom-right in a binary matrix (0=clear, 1=blocked). Movement is 8-directional.

**Hint:** BFS from `(0,0)` if it is 0. Expand to all 8 neighbours. Track path length via BFS levels. Return -1 if no path. Remember to check if `(0,0)` or `(n-1,n-1)` is blocked first.

**Why Hard?** 8-directional movement (expand `dirs` to include diagonals), careful start/end checks.

---

### H2 · Walls and Gates

**🔗 [LC 286 — Walls and Gates](https://leetcode.com/problems/walls-and-gates/)**
**Pattern:** Multi-Source BFS | **Companies:** Meta, Lyft, Airbnb

**Problem:** Fill each empty room with its distance to the nearest gate. `-1` = wall, `0` = gate, `INF` = empty room.

**Hint:** Seed BFS with ALL gate cells (0-cells) simultaneously. BFS outward, updating empty rooms with increasing distances. Multi-source BFS is essential — single-source from each gate would be O((m\*n)²).

---

### H3 · Minimum Path Sum

**🔗 [LC 64 — Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/)**
**Pattern:** Grid DP (preview of Lecture 21) | **Companies:** Google, Amazon, Adobe

**Problem:** Given a grid of non-negative integers, find the minimum sum path from top-left to bottom-right (can only move right or down).

**Hint:** Classic DP. `dp[r][c] = grid[r][c] + min(dp[r-1][c], dp[r][c-1])`. Handle first row (can only come from left) and first column (can only come from above) separately. Can be done in-place on the grid.

**Why Hard?** It's your first grid DP problem. The recurrence must be set up correctly before coding.

---

### H4 · Trapping Rain Water II

**🔗 [LC 407 — Trapping Rain Water II](https://leetcode.com/problems/trapping-rain-water-ii/)**
**Pattern:** Min-Heap (Priority Queue) + BFS from boundary | **Companies:** Google, Amazon

**Problem:** Given an m×n height map, compute how much water it can trap after raining.

**Hint:** The 2D extension of the classic 1D trapping rain water. Use a **min-heap seeded with all boundary cells**. BFS inward: each internal cell can hold `max(0, min_border_height - cell_height)` units. Use the min-heap to always process the lowest boundary cell first.

**Why Hard?** Combines PriorityQueue, BFS traversal, and non-trivial water accumulation logic.

---

### H5 · Word Search II

**🔗 [LC 212 — Word Search II](https://leetcode.com/problems/word-search-ii/)**
**Pattern:** Grid DFS + Trie | **Companies:** Google, Airbnb, Uber

**Problem:** Given a board and a list of words, return all words that exist in the board.

**Hint:** Build a Trie from all words. DFS from every cell, navigating the Trie character by character. When you reach a Trie node that marks a complete word, add it to results. Prune Trie nodes after a word is found to avoid duplicates. This reduces the complexity from O(words × m × n × 4^L) to near-linear in practice.

**Why Hard?** Requires implementing a Trie, integrating it with DFS backtracking, and pruning correctly.

---

## 🧠 Conceptual Check — Answer Without Looking at Code

These are the kind of questions interviewers ask verbally after you solve the coding problem:

1. **Bounds checking:** Write the standard `if (r < 0 || r >= m || c < 0 || c >= n)` guard from memory. Why must this be the **first** check in every DFS function — not the second or third?

2. **DFS vs BFS on grids:** For what specific class of problems must you use BFS instead of DFS? What property does BFS guarantee that DFS cannot?

3. **Multi-source BFS:** Why is seeding ALL source cells simultaneously O(m*n) total, while doing one BFS per source would be O((m*n)²)?

4. **In-place tricks:** In Set Matrix Zeroes, why do we need two separate boolean flags for `row0` and `col0` instead of just checking `matrix[0][0]`?

5. **Corner walk:** In LC 240, why does starting from the **top-right** corner work but the **top-left** or **bottom-right** does not? Give a one-sentence answer.

6. **Game of Life:** What does the sentinel value `2` represent and why is it necessary to use a sentinel instead of just writing `0` immediately?

---

## 🏢 Company Focus Table

| Company       | Must-Know Problems                                                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | Pacific Atlantic (LC 417), Search 2D Matrix II (LC 240), 01 Matrix (LC 542), Trapping Rain Water II (LC 407), Word Search II (LC 212) |
| **Amazon**    | Number of Islands (LC 200), Rotting Oranges (LC 994), Word Search (LC 79), Spiral Matrix (LC 54), 01 Matrix (LC 542)                  |
| **Meta**      | Walls and Gates (LC 286), Clone Graph (LC 133), Number of Islands (LC 200)                                                            |
| **Microsoft** | Rotate Image (LC 48), Set Matrix Zeroes (LC 73), Search 2D Matrix II (LC 240), Word Search (LC 79)                                    |
| **Goldman**   | Island Perimeter (LC 463), Set Matrix Zeroes (LC 73)                                                                                  |
| **Airbnb**    | Word Search II (LC 212), Walls and Gates (LC 286)                                                                                     |

---

## ✅ Completion Checklist

- [ ] Completed all 5 Easy problems
- [ ] Completed all 14 Medium problems
- [ ] Attempted all 5 Hard problems
- [ ] Can answer all 6 Conceptual Check questions verbally
- [ ] Can write the 4-direction `dirs` array and `inBounds` check from memory
- [ ] Can identify the correct pattern within 30 seconds for any matrix problem

---

**← Topic 13: HashMap & HashSet** &nbsp;&nbsp;|&nbsp;&nbsp; **Topic 15: Trees (Binary Trees & BST) →**
