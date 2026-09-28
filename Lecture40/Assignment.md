# 🕳️ Assignment 40 — Advanced Graph Algorithms

> **Lecture:** 40 of 45 — Advanced Graph Algorithms
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 6 days · **Total Problems:** 22 (0 Easy · 10 Medium · 12 Hard)
> **Goal:** Find the nodes and groups a directed or undirected graph depends on, handle unusual edge weights, and recognise flow and matching.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                      | Pattern                       | Move                                                    |
| ---------------------------------------------------------- | ----------------------------- | ------------------------------------------------------- |
| A single node or link whose failure disconnects everything | Articulation points / bridges | disc and low in one DFS                                 |
| Directed graph: groups where everyone reaches everyone     | SCC (Kosaraju / Tarjan)       | Then condense into a DAG                                |
| Each node has at most one outgoing edge                    | Functional graph              | Walk with timestamps; components are cycles plus chains |
| Every step costs 0 or 1                                    | 0-1 BFS                       | Deque: 0 to the front, 1 to the back                    |
| The best route depends on keys, stops, time or fuel        | Dijkstra / BFS over states    | Put the extra information in the node                   |
| Pair two groups with allowed or scored pairs               | Matching                      | Augmenting paths — or bitmask DP when a side is ≤ 15    |
| Use every edge exactly once                                | Eulerian path (Hierholzer)    | Check degrees, build backwards                          |

---

## 🟢 Easy Tier (0 Problems)

_No Easy problems — advanced graph algorithms do not come in an Easy form. Start with the Medium tier._

## 🟡 Medium Tier (10 Problems)

_Special weights, functional graphs, multi-source BFS and a small matching. Most are one idea from this lecture layered on a traversal you already know._

### M1 · Find Closest Node to Given Two Nodes

**🔗 [LC 2359 — Find Closest Node to Given Two Nodes](https://leetcode.com/problems/find-closest-node-to-given-two-nodes/)** · Medium
**Pattern:** Functional graph walks | **Companies:** Google, Amazon

**Hint:** Each node has one outgoing edge, so walk from node1 and from node2 recording distances. Choose the node minimising the larger of the two distances; smallest index on ties.

---

### M2 · All Ancestors of a Node in a Directed Acyclic Graph

**🔗 [LC 2192 — All Ancestors of a Node in a Directed Acyclic Graph](https://leetcode.com/problems/all-ancestors-of-a-node-in-a-directed-acyclic-graph/)** · Medium
**Pattern:** DAG ancestors | **Companies:** Amazon, Google

**Hint:** For every node, DFS forward and add the start node as an ancestor of everything it reaches. Starting in increasing order keeps each list sorted.

---

### M3 · Minimum Sideway Jumps

**🔗 [LC 1824 — Minimum Sideway Jumps](https://leetcode.com/problems/minimum-sideway-jumps/)** · Medium
**Pattern:** 0-1 BFS over (point, lane) | **Companies:** Amazon, Google

**Hint:** Moving forward in the same lane costs 0; switching lanes at the same point costs 1, unless the new lane has a rock there.

---

### M4 · Find Minimum Time to Reach Last Room I

**🔗 [LC 3341 — Find Minimum Time to Reach Last Room I](https://leetcode.com/problems/find-minimum-time-to-reach-last-room-i/)** · Medium
**Pattern:** Dijkstra with opening times | **Companies:** Google, Amazon

**Hint:** Arriving in a room costs max(current time, moveTime of the room) + 1. The time only grows, so plain Dijkstra works.

---

### M5 · Find Minimum Time to Reach Last Room II

**🔗 [LC 3342 — Find Minimum Time to Reach Last Room II](https://leetcode.com/problems/find-minimum-time-to-reach-last-room-ii/)** · Medium
**Pattern:** Dijkstra with alternating costs | **Companies:** Google, Amazon

**Hint:** Moves alternate between 1 and 2 seconds, and every move changes the parity of i + j. So the cost of leaving (i, j) is fixed by that parity — still plain Dijkstra.

---

### M6 · Find the Safest Path in a Grid

**🔗 [LC 2812 — Find the Safest Path in a Grid](https://leetcode.com/problems/find-the-safest-path-in-a-grid/)** · Medium
**Pattern:** Multi-source BFS + maximise the minimum | **Companies:** Google, Amazon

**Hint:** BFS from all thieves at once gives each cell its safeness. Then find the path maximising its smallest safeness: Dijkstra with a max-heap, or binary search the answer and BFS.

---

### M7 · Shortest Bridge

**🔗 [LC 934 — Shortest Bridge](https://leetcode.com/problems/shortest-bridge/)** · Medium
**Pattern:** Flood fill + multi-source BFS | **Companies:** Google, Amazon

**Hint:** Mark one island with DFS, then BFS outwards from all its cells at once. The first layer that touches the other island is the answer.

---

### M8 · Detect Cycles in 2D Grid

**🔗 [LC 1559 — Detect Cycles in 2D Grid](https://leetcode.com/problems/detect-cycles-in-2d-grid/)** · Medium
**Pattern:** Cycle in an undirected grid graph | **Companies:** Google, Amazon

**Hint:** DFS over same-letter cells; reaching an already-visited cell that is not the one you came from closes a cycle — the undirected rule from Lecture 21.

---

### M9 · Maximum Compatibility Score Sum

**🔗 [LC 1947 — Maximum Compatibility Score Sum](https://leetcode.com/problems/maximum-compatibility-score-sum/)** · Medium
**Pattern:** Assignment via bitmask DP | **Companies:** Google, Amazon

**Hint:** With m ≤ 8, dp[mask] over the mentors used; the next student is popcount(mask).

---

### M10 · Node With Highest Edge Score

**🔗 [LC 2374 — Node With Highest Edge Score](https://leetcode.com/problems/node-with-highest-edge-score/)** · Medium
**Pattern:** Functional graph scores | **Companies:** Amazon

**Hint:** Add i to the score of edges[i]. Scores can exceed the int range — use long. Highest score, smallest index on ties.

---

## 🔴 Hard Tier (12 Problems)

_The ideas at full strength: articulation points, functional-graph cycles, 0-1 BFS, searches over states, Eulerian circuits and assignment._

### H1 · Minimum Number of Days to Disconnect Island

**🔗 [LC 1568 — Minimum Number of Days to Disconnect Island](https://leetcode.com/problems/minimum-number-of-days-to-disconnect-island/)** · Hard
**Pattern:** Articulation point, answer ≤ 2 | **Companies:** Google, Amazon

**Hint:** The answer is 0, 1 or 2. It is 1 if the island is a single cell or some land cell is an articulation point.

---

### H2 · Longest Cycle in a Graph

**🔗 [LC 2360 — Longest Cycle in a Graph](https://leetcode.com/problems/longest-cycle-in-a-graph/)** · Hard
**Pattern:** Cycles in a functional graph | **Companies:** Google, Amazon

**Hint:** Walk from each unvisited node stamping visit times; returning to a node stamped in the current walk closes a cycle of length (clock − stamp).

---

### H3 · Maximum Employees to Be Invited to a Meeting

**🔗 [LC 2127 — Maximum Employees to Be Invited to a Meeting](https://leetcode.com/problems/maximum-employees-to-be-invited-to-a-meeting/)** · Hard
**Pattern:** Functional graph: cycles and chains | **Companies:** Google, Amazon

**Hint:** Two kinds of table: one big cycle (its length), or every mutual pair (2-cycle) plus the longest chain feeding into each side — all such pairs can sit together. Peel chains with a topological sort.

---

### H4 · Shortest Cycle in a Graph

**🔗 [LC 2608 — Shortest Cycle in a Graph](https://leetcode.com/problems/shortest-cycle-in-a-graph/)** · Hard
**Pattern:** BFS from every vertex | **Companies:** Google, Amazon

**Hint:** From each start, BFS; any edge to an already-visited node that is not the BFS parent closes a cycle of length dist[u] + dist[v] + 1. Take the minimum.

---

### H5 · Minimum Obstacle Removal to Reach Corner

**🔗 [LC 2290 — Minimum Obstacle Removal to Reach Corner](https://leetcode.com/problems/minimum-obstacle-removal-to-reach-corner/)** · Hard
**Pattern:** 0-1 BFS | **Companies:** Google, Amazon

**Hint:** Entering an obstacle costs 1, an empty cell 0. Deque: front for 0, back for 1.

---

### H6 · Minimum Cost to Make at Least One Valid Path in a Grid

**🔗 [LC 1368 — Minimum Cost to Make at Least One Valid Path in a Grid](https://leetcode.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid/)** · Hard
**Pattern:** 0-1 BFS on arrows | **Companies:** Google, Amazon

**Hint:** Following a cell’s arrow is free; moving any other way means changing the sign, which costs 1.

---

### H7 · Shortest Path to Get All Keys

**🔗 [LC 864 — Shortest Path to Get All Keys](https://leetcode.com/problems/shortest-path-to-get-all-keys/)** · Hard
**Pattern:** BFS over (cell, keys) | **Companies:** Google, Amazon, Airbnb

**Hint:** Make the keys held part of the state as a bitmask; a lock is passable only with its bit set.

---

### H8 · Minimum Cost to Reach Destination in Time

**🔗 [LC 1928 — Minimum Cost to Reach Destination in Time](https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/)** · Hard
**Pattern:** Dijkstra over (city, time) | **Companies:** Google, Amazon

**Hint:** Minimise fees subject to a time limit. Dijkstra on fee, discarding a state if you already reached that city faster — or DP over time, since maxTime ≤ 1000.

---

### H9 · Second Minimum Time to Reach Destination

**🔗 [LC 2045 — Second Minimum Time to Reach Destination](https://leetcode.com/problems/second-minimum-time-to-reach-destination/)** · Hard
**Pattern:** BFS keeping two distances | **Companies:** Google, Amazon

**Hint:** Track the first and the second distinct arrival counts at every node. Convert the second-best edge count at node n into time, waiting for each red light.

---

### H10 · Cracking the Safe

**🔗 [LC 753 — Cracking the Safe](https://leetcode.com/problems/cracking-the-safe/)** · Hard
**Pattern:** Eulerian circuit (de Bruijn) | **Companies:** Google

**Hint:** Nodes are (n − 1)-digit strings; each edge appends a digit. An Eulerian circuit uses every edge — every n-digit password — exactly once. Build it with Hierholzer.

---

### H11 · Valid Arrangement of Pairs

**🔗 [LC 2097 — Valid Arrangement of Pairs](https://leetcode.com/problems/valid-arrangement-of-pairs/)** · Hard
**Pattern:** Eulerian path | **Companies:** Google, Amazon

**Hint:** Start at the node whose out-degree exceeds its in-degree by one (or anywhere if none does). Hierholzer builds the path backwards; reverse it at the end.

---

### H12 · Minimum XOR Sum of Two Arrays

**🔗 [LC 1879 — Minimum XOR Sum of Two Arrays](https://leetcode.com/problems/minimum-xor-sum-of-two-arrays/)** · Hard
**Pattern:** Assignment via bitmask DP | **Companies:** Google, Amazon

**Hint:** n ≤ 14: dp[mask] over the used elements of nums2; the next element of nums1 is popcount(mask).

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — articulation points or bridges in one DFS

// Snippet 2 — Kosaraju: two DFS passes plus building the reversed graph

// Snippet 3 — 0-1 BFS on an m × n grid

// Snippet 4 — BFS over (cell, key mask) with K keys on an m × n grid

// Snippet 5 — Edmonds-Karp max flow

// Snippet 6 — shortest cycle by running BFS from every vertex
```

**Complexity Answers:**

1. **O(V + E)**.
2. **O(V + E)**.
3. **O(m · n)** — each cell settled at most a constant number of times.
4. **O(m · n · 2ᴷ)**.
5. **O(V · E²)**.
6. **O(V · (V + E))**.

---

## 🔍 Self-Assessment — True / False

1. An articulation point test uses the same inequality as a bridge test. → **False** — articulation uses ≥, bridges use >
2. Condensing strongly connected components always produces a DAG. → **True**
3. 0-1 BFS gives correct shortest paths when every edge weight is 0 or 1. → **True**
4. Adding state to Dijkstra changes the algorithm itself. → **False** — only the nodes change; the algorithm runs unchanged
5. Residual edges let later augmenting paths undo earlier flow. → **True**
6. Visiting every node exactly once (a Hamiltonian path) has a known polynomial algorithm. → **False** — it is NP-hard; small n means bitmask DP

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **≥ versus >**: Why does the articulation-point test use ≥ while the bridge test uses >? Give a small graph that shows the difference.
2. **Kosaraju**: Why does the second pass have to run on the reversed graph, in order of latest finish?
3. **Functional graphs**: What do strongly connected components look like when every node has one outgoing edge?
4. **0-1 BFS**: Why does pushing weight-0 neighbours to the front keep the deque sorted by distance?
5. **States**: In Shortest Path to Get All Keys, how many states are there, and why can a cell be visited more than once?
6. **Min cut**: State the max-flow min-cut theorem in plain words.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon** | [Node With Highest Edge Score](https://leetcode.com/problems/node-with-highest-edge-score/), [Longest Cycle in a Graph](https://leetcode.com/problems/longest-cycle-in-a-graph/), [Maximum Employees to Be Invited to a Meeting](https://leetcode.com/problems/maximum-employees-to-be-invited-to-a-meeting/), [Minimum Cost to Make at Least One Valid Path in a Grid](https://leetcode.com/problems/minimum-cost-to-make-at-least-one-valid-path-in-a-grid/) |
| **Google** | [Cracking the Safe](https://leetcode.com/problems/cracking-the-safe/), [Minimum Cost to Reach Destination in Time](https://leetcode.com/problems/minimum-cost-to-reach-destination-in-time/), [Minimum Number of Days to Disconnect Island](https://leetcode.com/problems/minimum-number-of-days-to-disconnect-island/), [Minimum Obstacle Removal to Reach Corner](https://leetcode.com/problems/minimum-obstacle-removal-to-reach-corner/)                   |
| **Airbnb** | [Shortest Path to Get All Keys](https://leetcode.com/problems/shortest-path-to-get-all-keys/)                                                                                                                                                                                                                                                                                                                                                                  |

---

## ✅ Completion Checklist

- [ ] All 10 Medium problems solved
- [ ] All 12 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name the idea each problem uses before solving it
- [ ] I wrote 0-1 BFS and one state-expanded search from memory

---

**← [Lecture 39 · String Algorithms (KMP, Z, Rabin-Karp, Manacher)](../Lecture39/Assignment.md)** &nbsp;·&nbsp; **Lecture 41 · Balanced BSTs & Ordered Structures — coming soon →**
