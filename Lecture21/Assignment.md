# 🛡️ Assignment 21 — Graphs I — Representation, BFS & DFS

> **Lecture:** 21 of 45 — Graphs I — Representation, BFS & DFS
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 5 days · **Total Problems:** 16 (4 Easy · 8 Medium · 4 Hard)
> **Goal:** Build a graph from any input, walk it two ways, and recognise a graph problem that never says the word.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                         | Pattern                 | Move                                              |
| --------------------------------------------- | ----------------------- | ------------------------------------------------- |
| "Are these two connected?" / count the groups | DFS or BFS flood fill   | Loop every node, traverse from each unvisited one |
| Shortest path, every edge costs the same      | BFS                     | Level by level; the first arrival is the shortest |
| Explore as deep as possible, or find any path | DFS                     | Recursion or an explicit stack                    |
| States one move apart, no graph given         | Implicit graph + BFS    | Nodes are states, edges are legal moves           |
| Does this undirected graph contain a cycle?   | DFS with a parent check | A visited neighbour that is not your parent       |
| Does this directed graph contain a cycle?     | DFS with three colours  | A grey node means you are back on your own path   |

---

## 🟢 Easy Tier (4 Problems)

_Graphs handed to you directly. Build the adjacency list first, every time — most of these are one traversal after that._

### E1 · Find if Path Exists in Graph

**🔗 [LC 1971 — Find if Path Exists in Graph](https://leetcode.com/problems/find-if-path-exists-in-graph/)** · Easy
**Pattern:** BFS / DFS reachability | **Companies:** Amazon, Google

**Hint:** Build adjacency list. Run BFS or DFS from `source`. If you reach `destination`, return true. Classic
reachability check — the "hello world" of graph problems.

---

### E2 · Find the Town Judge

**🔗 [LC 997 — Find the Town Judge](https://leetcode.com/problems/find-the-town-judge/)** · Easy
**Pattern:** In-degree / Out-degree | **Companies:** Amazon, Microsoft

**Hint:** The judge has in-degree `n - 1` and out-degree 0. Track `score[b]++` and `score[a]--` for every trust `a → b`, and look for the person with score `n - 1`.

---

### E3 · Destination City

**🔗 [LC 1436 — Destination City](https://leetcode.com/problems/destination-city/)** · Easy
**Pattern:** Out-degree Zero | **Companies:** Yelp, Amazon

**Hint:** Put every start city in a set. The destination is the only end city that is never a start city.

---

### E4 · Find Center of Star Graph

**🔗 [LC 1791 — Find Center of Star Graph](https://leetcode.com/problems/find-center-of-star-graph/)** · Easy
**Pattern:** Graph properties | **Companies:** Amazon

**Hint:** In a star graph, the center node appears in every edge. Just check which node is common between `edges[0]` and
`edges[1]` — no traversal needed.

---

## 🟡 Medium Tier (8 Problems)

_Components, flood fill, and your first implicit graphs. If the problem does not mention a graph, ask what a node would be._

### M1 · Count Unreachable Pairs of Nodes in an Undirected Graph

**🔗 [LC 2316 — Count Unreachable Pairs of Nodes in an Undirected Graph](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/)** · Medium
**Pattern:** Connected Component Sizes | **Companies:** Amazon, Google

**Hint:** Find each component's size with DFS, BFS or Union-Find. Pairs in different components: keep `seen` (nodes processed so far) and for each component of size `s` add `s × seen`, then `seen += s`. Use `long`.

---

### M2 · Keys and Rooms

**🔗 [LC 841 — Keys and Rooms](https://leetcode.com/problems/keys-and-rooms/)** · Medium
**Pattern:** DFS reachability | **Companies:** Google, Amazon

**Hint:** Room 0 is unlocked. Keys in each room open other rooms. DFS/BFS from room 0 adding newly reachable rooms.
Return `visited.size() == n`.

---

### M3 · Count Sub Islands

**🔗 [LC 1905 — Count Sub Islands](https://leetcode.com/problems/count-sub-islands/)** · Medium
**Pattern:** DFS flood fill | **Companies:** Google

**Hint:** DFS across grid2 islands. An island in grid2 is a sub-island of grid1 only if every cell of that island is
also land in grid1. Track with a flag: if any cell of the DFS is water in grid1, the whole island fails.

---

### M4 · Number of Operations to Make Network Connected

**🔗 [LC 1319 — Number of Operations to Make Network Connected](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)** · Medium
**Pattern:** Connected Components | **Companies:** Amazon, Google, Meta

**Hint:** If `edges < n - 1`, it's impossible. Otherwise count components (DFS/BFS over an adjacency list); you need `components - 1` moves, since each redundant cable can join two components.

---

### M5 · Open the Lock

**🔗 [LC 752 — Open the Lock](https://leetcode.com/problems/open-the-lock/)** · Medium
**Pattern:** BFS on an Implicit Graph | **Companies:** Google, Amazon, Microsoft

**Hint:** Each 4-digit string is a node with 8 neighbours (each wheel ±1). BFS from `"0000"`, skipping deadends and visited states. The level at which you reach the target is the answer.

---

### M6 · Number of Provinces

**🔗 [LC 547 — Number of Provinces](https://leetcode.com/problems/number-of-provinces/)** · Medium
**Pattern:** DFS connected components | **Companies:** Google, Amazon, Facebook

**Hint:** Input is an adjacency matrix. DFS/BFS from each unvisited city. Each traversal = one province. Very similar to
Number of Islands but on an adjacency matrix.

---

### M7 · Clone Graph

**🔗 [LC 133 — Clone Graph](https://leetcode.com/problems/clone-graph/)** · Medium
**Pattern:** DFS/BFS with HashMap | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Use a `HashMap<Node, Node>` (original → clone). DFS: if `map.containsKey(node)`, return its clone. Otherwise
create a new node, add to map, then clone all neighbours recursively.

---

### M8 · Reorder Routes to Make All Paths Lead to the City Zero

**🔗 [LC 1466 — Reorder Routes to Make All Paths Lead to the City Zero](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/)** · Medium
**Pattern:** Edge Direction as Cost | **Companies:** Amazon, Google

**Hint:** Store each edge in both directions, marked with cost 1 if it's an original direction (away from 0) and 0 if reversed. DFS from city 0 and sum the costs of edges you traverse.

---

## 🔴 Hard Tier (4 Problems)

_BFS where the state is more than a node — a word, a route, or a position plus a budget._

### H1 · Word Ladder

**🔗 [LC 127 — Word Ladder](https://leetcode.com/problems/word-ladder/)** · Hard
**Pattern:** BFS on implicit graph | **Companies:** Google, Amazon, Facebook, Microsoft

> ⚠️ LeetCode rates this **Hard** — the core BFS concept is Medium; the challenge is the implicit graph construction and
> avoiding TLE.

**Hint:** BFS where each word is a node. Two words are connected if they differ by exactly one letter. Try all 26
letters for each position. Use a set for O(1) lookup and remove words as visited. BFS level count = transformation
steps.

---

### H2 · Word Ladder II

**🔗 [LC 126 — Word Ladder II](https://leetcode.com/problems/word-ladder-ii/)** · Hard
**Pattern:** BFS + DFS (find all shortest paths) | **Companies:** Google, Amazon, Facebook

**Hint:** BFS to compute shortest distance from `beginWord` to every reachable word. Then DFS/backtracking from
`endWord` backward, following only edges that strictly decrease the BFS distance. This avoids storing all paths during
BFS.

**Why Hard?** Combining BFS distance labelling with DFS path reconstruction, handling the "all shortest paths"
requirement without TLE.

---

### H3 · Bus Routes

**🔗 [LC 815 — Bus Routes](https://leetcode.com/problems/bus-routes/)** · Hard
**Pattern:** BFS on route graph | **Companies:** Google, Uber

**Hint:** Nodes are BUS ROUTES (not stops). Two routes are connected if they share a stop. BFS from all routes
containing `source`. Answer = minimum bus changes + 1. Key insight: model routes as nodes to avoid O(stops²)
connections.

---

### H4 · Shortest Path in a Grid with Obstacles Elimination

**🔗 [LC 1293 — Shortest Path in a Grid with Obstacles Elimination](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/)** · Hard
**Pattern:** BFS with state = (row, col, k_remaining) | **Companies:** Google, Amazon, Uber

**Hint:** State is `(r, c, obstacles_remaining)`. BFS on this 3D state space. `visited[r][c][k]` = true if we've visited
`(r,c)` with `k` eliminations left. First time we reach `(m-1,n-1)`, return the BFS level.

**Why Hard?** Extending BFS state beyond just position. Recognising that using more eliminations isn't always better (
visited must track k too).

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — BFS on a graph stored as an adjacency list

// Snippet 2 — BFS on a graph stored as an adjacency matrix

// Snippet 3 — DFS from every node, with a shared visited set

// Snippet 4 — count connected components

// Snippet 5 — Word Ladder: n words of length L, trying 26 letters per position

// Snippet 6 — an adjacency matrix for V = 100,000 (SPACE)
```

**Complexity Answers:**

1. **O(V + E)**.
2. **O(V²)** — every row is scanned.
3. **O(V + E)** — the shared set stops repeats.
4. **O(V + E)**.
5. **O(n · L · 26)**, ignoring string-building costs.
6. **O(V²)** = 10¹⁰ cells — far too much memory. Use a list.

---

## 🔍 Self-Assessment — True / False

1. BFS finds shortest paths in any graph. → **False** — only when every edge has the same weight
2. DFS and BFS both run in O(V + E) with an adjacency list. → **True**
3. An undirected edge must be added to both endpoints' lists. → **True** — otherwise traversals miss half the connections
4. Detecting a cycle in a directed graph needs only a visited set. → **False** — you need to know which nodes are on the current path
5. A graph can have several connected components. → **True** — so traversal must restart from every unvisited node
6. An adjacency matrix is the best choice for a sparse graph. → **False** — it wastes O(V²) space; use a list

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Representation:** When is an adjacency matrix the right choice over an adjacency list? Give the memory cost of each.
2. **Why BFS:** Explain why BFS gives shortest paths on an unweighted graph but DFS does not.
3. **Visited placement:** Should you mark a node visited when you push it or when you pop it? What goes wrong with the other choice?
4. **Undirected cycles:** Why does the undirected cycle check need a parent argument, and what breaks without it?
5. **Directed cycles:** Why are two states (visited / unvisited) not enough for a directed graph? What does the third state mean?
6. **Implicit graphs:** In Word Ladder, what exactly is a node and what is an edge? How many neighbours does a node have?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Destination City](https://leetcode.com/problems/destination-city/), [Find Center of Star Graph](https://leetcode.com/problems/find-center-of-star-graph/), [Count Unreachable Pairs of Nodes in an Undirected Graph](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/), [Keys and Rooms](https://leetcode.com/problems/keys-and-rooms/)                                   |
| **Google**    | [Count Sub Islands](https://leetcode.com/problems/count-sub-islands/), [Bus Routes](https://leetcode.com/problems/bus-routes/), [Number of Operations to Make Network Connected](https://leetcode.com/problems/number-of-operations-to-make-network-connected/), [Reorder Routes to Make All Paths Lead to the City Zero](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/) |
| **Facebook**  | [Word Ladder II](https://leetcode.com/problems/word-ladder-ii/), [Number of Provinces](https://leetcode.com/problems/number-of-provinces/), [Word Ladder](https://leetcode.com/problems/word-ladder/), [Clone Graph](https://leetcode.com/problems/clone-graph/)                                                                                                                                                 |
| **Microsoft** | [Find the Town Judge](https://leetcode.com/problems/find-the-town-judge/), [Open the Lock](https://leetcode.com/problems/open-the-lock/), [Word Ladder](https://leetcode.com/problems/word-ladder/), [Clone Graph](https://leetcode.com/problems/clone-graph/)                                                                                                                                                   |
| **Uber**      | [Bus Routes](https://leetcode.com/problems/bus-routes/), [Shortest Path in a Grid with Obstacles Elimination](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/)                                                                                                                                                                                                                 |

---

## ✅ Completion Checklist

- [ ] All 4 Easy problems solved
- [ ] All 8 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write BFS and DFS from memory with a correct visited set
- [ ] I can detect cycles in both directed and undirected graphs
- [ ] I can spot an implicit graph and name its nodes and edges

---

**← [Lecture 20 · Heaps & Priority Queues](../Lecture20/Assignment.md)** &nbsp;·&nbsp; **[Lecture 22 · Graphs II — Topological Sort & Shortest Paths](../Lecture22/Assignment.md) →**
