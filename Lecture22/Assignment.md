# 🗺️ Assignment 22 — Graphs II — Topological Sort & Shortest Paths

> **Lecture:** 22 of 45 — Graphs II — Topological Sort & Shortest Paths
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 5 days · **Total Problems:** 16 (0 Easy · 13 Medium · 3 Hard)
> **Goal:** Order a dependency graph, and pick the right shortest-path algorithm from the constraints alone.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                             | Pattern                       | Move                                                          |
| ------------------------------------------------- | ----------------------------- | ------------------------------------------------------------- |
| Tasks with prerequisites; "is an order possible?" | Topological sort (Kahn)       | Queue the in-degree-0 nodes; leftovers mean a cycle           |
| Cheapest route, all weights non-negative          | Dijkstra                      | Priority queue, settle each node once                         |
| Weights may be negative, or hop count is limited  | Bellman-Ford                  | Relax every edge V−1 times, or k+1 times                      |
| Shortest path between every pair of nodes         | Floyd-Warshall                | Three nested loops, k on the outside                          |
| Shortest path where the state carries extra info  | Dijkstra on an expanded state | The node is (position, extra); distances indexed the same way |
| Count the shortest paths, not just measure one    | Dijkstra + counters           | Equal distance adds counts, shorter distance replaces them    |

---

## 🟢 Easy Tier (0 Problems)

_No Easy problems here — graph algorithms at this level simply do not have them. Start with the Medium tier._

## 🟡 Medium Tier (13 Problems)

_Ordering first, then routing. For each one, decide which of the four algorithms applies before writing anything._

### M1 · Find Champion II

**🔗 [LC 2924 — Find Champion II](https://leetcode.com/problems/find-champion-ii/)** · Medium
**Pattern:** In-degree Counting (DAG) | **Companies:** Amazon, Google

**Hint:** The champion is the unique node with in-degree 0. Count in-degrees; if exactly one node has 0, return it, otherwise return -1.

---

### M2 · Course Schedule

**🔗 [LC 207 — Course Schedule](https://leetcode.com/problems/course-schedule/)** · Medium
**Pattern:** Cycle detection in directed graph | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Build directed graph: prerequisite → course. Run Kahn's topological sort. If you can process all n courses (
idx == n), no cycle exists → return true.

---

### M3 · Course Schedule II

**🔗 [LC 210 — Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)** · Medium
**Pattern:** Topological sort | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Same as LC 207 but return the topological order. Use Kahn's: when in-degree reaches 0, add to queue and to
result array. If result length < n, cycle exists.

---

### M4 · Find Eventual Safe States

**🔗 [LC 802 — Find Eventual Safe States](https://leetcode.com/problems/find-eventual-safe-states/)** · Medium
**Pattern:** Reverse Graph + Topological Sort | **Companies:** Google, Amazon

**Hint:** Safe nodes are those that can't reach a cycle. Reverse the edges, start from terminal nodes (out-degree 0), and peel with Kahn's algorithm — every node peeled is safe. Or use DFS three-colouring.

---

### M5 · Network Delay Time

**🔗 [LC 743 — Network Delay Time](https://leetcode.com/problems/network-delay-time/)** · Medium
**Pattern:** Dijkstra | **Companies:** Google, Amazon, Meta, Uber

**Hint:** Build weighted directed adjacency list. Dijkstra from node `k`. Answer = max of all `dist[i]`. If any node has
`dist = ∞`, return -1.

---

### M6 · Path With Minimum Effort

**🔗 [LC 1631 — Path With Minimum Effort](https://leetcode.com/problems/path-with-minimum-effort/)** · Medium
**Pattern:** Dijkstra on grid | **Companies:** Google, Amazon

**Hint:** Nodes = grid cells. Edge weight = absolute height difference. Dijkstra where `dist[r][c]` = min effort to
reach that cell. Effort for a path = maximum edge weight along it.

---

### M7 · Find the City With the Smallest Number of Neighbours at a Threshold Distance

**🔗 [LC 1334 — Find the City With the Smallest Number of Neighbors at a Threshold Distance](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/)** · Medium
**Pattern:** Floyd-Warshall (all-pairs shortest path) | **Companies:** Google, Amazon

**Hint:** Run Floyd-Warshall to compute all-pairs shortest paths. For each city, count how many other cities are reachable within `distanceThreshold`. Return the city with the fewest reachable neighbours (ties broken by largest city index). Floyd-Warshall fits here because n ≤ 100.

---

### M8 · Cheapest Flights Within K Stops

**🔗 [LC 787 — Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)** · Medium
**Pattern:** Modified Bellman-Ford | **Companies:** Google, Amazon, Uber

**Hint:** Bellman-Ford with at most K+1 rounds (K stops = K+1 edges). Key: copy `dist` array before each round to
prevent using updates from the same round. Dijkstra doesn't apply here because of the K-stop constraint changing the
state space.

---

### M9 · Minimum Number of Vertices to Reach All Nodes

**🔗 [LC 1557 — Minimum Number of Vertices to Reach All Nodes](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/)** · Medium
**Pattern:** Reverse thinking on in-degree | **Companies:** Amazon, Google

**Hint:** A node with in-degree 0 cannot be reached from anywhere else, so it must be in the answer — and nothing else needs to be.

---

### M10 · Find All Possible Recipes from Given Supplies

**🔗 [LC 2115 — Find All Possible Recipes from Given Supplies](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/)** · Medium
**Pattern:** Topological sort | **Companies:** Amazon, Google

**Hint:** Ingredients are prerequisites. Kahn from the supplies you already have, and cook a recipe when its last ingredient arrives.

---

### M11 · Shortest Path with Alternating Colors

**🔗 [LC 1129 — Shortest Path with Alternating Colors](https://leetcode.com/problems/shortest-path-with-alternating-colors/)** · Medium
**Pattern:** BFS with state = (node, last colour) | **Companies:** Google, Amazon

**Hint:** The state is not just the node — it is the node plus the colour you arrived on. Two distance arrays, or one indexed by colour.

---

### M12 · Number of Ways to Arrive at Destination

**🔗 [LC 1976 — Number of Ways to Arrive at Destination](https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/)** · Medium
**Pattern:** Dijkstra + path counting | **Companies:** Google, Amazon

**Hint:** Run Dijkstra once; when you relax to an equal distance, add the path counts, and when you find a shorter one, replace them.

---

### M13 · Path with Maximum Probability

**🔗 [LC 1514 — Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/)** · Medium
**Pattern:** Dijkstra on products | **Companies:** Amazon, Google

**Hint:** Probabilities multiply instead of adding, and you want the maximum — flip the comparison and use a max-heap.

---

## 🔴 Hard Tier (3 Problems)

_Two-level ordering, and shortest paths where the cost function is not what you expect._

### H1 · Sort Items by Groups Respecting Dependencies

**🔗 [LC 1203 — Sort Items by Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/)** · Hard
**Pattern:** Two-Level Topological Sort | **Companies:** Google, Amazon

**Hint:** Give every ungrouped item its own new group. Build two graphs — item dependencies and group dependencies (edges between different groups) — and topologically sort both. Then emit items group by group in group order, each group's items in item order. Any cycle means return `[]`.

---

### H2 · Swim in Rising Water

**🔗 [LC 778 — Swim in Rising Water](https://leetcode.com/problems/swim-in-rising-water/)** · Hard
**Pattern:** Dijkstra / Binary Search + BFS | **Companies:** Google

**Hint:** Dijkstra variant: `dist[r][c]` = min time to reach `(r,c)` = max elevation on the path (bottleneck path). PQ
ordered by current time. Alternatively: binary search on answer t + BFS to check if path exists using only cells ≤ t.

---

### H3 · Largest Color Value in a Directed Graph

**🔗 [LC 1857 — Largest Color Value in a Directed Graph](https://leetcode.com/problems/largest-color-value-in-a-directed-graph/)** · Hard
**Pattern:** Topological sort + DP | **Companies:** Google, Amazon

**Hint:** Carry 26 counters along the topological order; a cycle means the answer is −1.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — Kahn's topological sort

// Snippet 2 — Dijkstra with a binary heap

// Snippet 3 — Dijkstra with a plain array scan for the minimum

// Snippet 4 — Bellman-Ford

// Snippet 5 — Floyd-Warshall with V = 400

// Snippet 6 — Floyd-Warshall with V = 10,000
```

**Complexity Answers:**

1. **O(V + E)**.
2. **O((V + E) log V)**.
3. **O(V²)** — fine for dense graphs.
4. **O(V · E)**.
5. **O(V³)** ≈ 6.4 × 10⁷ — fine.
6. **O(V³)** = 10¹² — hopeless. Run Dijkstra from each source only if needed.

---

## 🔍 Self-Assessment — True / False

1. Dijkstra works with negative edge weights. → **False** — it may settle a node too early
2. A topological order exists only for a directed acyclic graph. → **True**
3. Bellman-Ford can detect a negative cycle. → **True** — if a V-th round still relaxes an edge
4. In Floyd-Warshall the loop over k may be placed anywhere. → **False** — it must be outermost
5. Kahn's algorithm reports a cycle when some nodes are never output. → **True**
6. BFS gives shortest paths when all weights are 0 or 1. → **False** — plain BFS does not; 0-1 BFS with a deque does

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Kahn:** How does Kahn’s algorithm tell you the graph has a cycle? What exactly do you check at the end?
2. **Dijkstra’s assumption:** State it precisely, then give a small graph with a negative edge where Dijkstra returns the wrong answer.
3. **Settling:** Why may Dijkstra ignore a node the second time it pops it?
4. **Bellman-Ford rounds:** Why V−1 rounds and not V? What does a V-th successful relaxation prove?
5. **Floyd-Warshall order:** Why must the k loop be outermost? What does dp`[i][j]` mean after k rounds?
6. **Choosing:** Given V = 400 and a request for all-pairs distances, which algorithm and why? What if V = 100000 with one source?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Google**    | [Swim in Rising Water](https://leetcode.com/problems/swim-in-rising-water/), [Largest Color Value in a Directed Graph](https://leetcode.com/problems/largest-color-value-in-a-directed-graph/), [Sort Items by Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/), [Find All Possible Recipes from Given Supplies](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/)                           |
| **Amazon**    | [Find Champion II](https://leetcode.com/problems/find-champion-ii/), [Find Eventual Safe States](https://leetcode.com/problems/find-eventual-safe-states/), [Find the City With the Smallest Number of Neighbors at a Threshold Distance](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/), [Minimum Number of Vertices to Reach All Nodes](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/) |
| **Meta**      | [Course Schedule](https://leetcode.com/problems/course-schedule/), [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/), [Network Delay Time](https://leetcode.com/problems/network-delay-time/)                                                                                                                                                                                                                                                                  |
| **Microsoft** | [Course Schedule](https://leetcode.com/problems/course-schedule/), [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)                                                                                                                                                                                                                                                                                                                                           |
| **Uber**      | [Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/), [Network Delay Time](https://leetcode.com/problems/network-delay-time/)                                                                                                                                                                                                                                                                                                           |

---

## ✅ Completion Checklist

- [ ] All 13 Medium problems solved
- [ ] All 3 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write Kahn’s algorithm and detect impossibility
- [ ] I can write Dijkstra with a priority queue from memory
- [ ] I can name the algorithm from the constraints in under a minute

---

**← [Lecture 21 · Graphs I — Representation, BFS & DFS](../Lecture21/Assignment.md)** &nbsp;·&nbsp; **[Lecture 23 · Graphs III — MST, Bipartite & Bridges](../Lecture23/Assignment.md) →**
