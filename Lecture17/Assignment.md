# 🕸️ Assignment 17 — Graphs

> **Lecture:** 17 of 38 — Graphs
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 12 days · **Total Problems:** 30 (8 Easy · 15 Medium · 7 Hard)
> **Goal:** Master the 6 graph patterns — BFS Shortest Path, DFS Flood Fill, Cycle Detection, Topological Sort,
> Dijkstra, MST.

---

## 🗺️ Pattern Recognition — Read Before Starting

| Signal Phrase                                            | Pattern            | Tool                               |
| -------------------------------------------------------- | ------------------ | ---------------------------------- |
| "Shortest path", "minimum steps/hops" — unweighted       | BFS                | Queue + visited[]                  |
| "Connected components", "number of islands", "regions"   | DFS flood fill     | visited[] + recursive DFS          |
| "Can complete all tasks", "detect cycle"                 | Cycle Detection    | 3-color DFS (directed) or Kahn's   |
| "Task order", "dependency", "prerequisite"               | Topological Sort   | Kahn's BFS (in-degree)             |
| "Shortest path" — non-negative weights                   | Dijkstra           | Min-heap PQ                        |
| "Minimum cost to connect all", "MST"                     | Kruskal's / Prim's | Sort edges + Union-Find / Min-heap |
| "Two groups", "no conflict", "bipartite"                 | BFS 2-coloring     | color[] alternating 0/1            |
| "All-pairs shortest path", "distance between every pair" | Floyd-Warshall     | 3-loop DP on distance matrix       |
| "Critical connections", "bridge", "remove one edge"      | Tarjan's Bridges   | DFS with disc[] and low[]          |

---

---

## 🟢 Easy Tier (8 Problems)

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

### E3 · Count Unreachable Pairs of Nodes in an Undirected Graph

**🔗 [LC 2316 — Count Unreachable Pairs of Nodes in an Undirected Graph](https://leetcode.com/problems/count-unreachable-pairs-of-nodes-in-an-undirected-graph/)** · Medium
**Pattern:** Connected Component Sizes | **Companies:** Amazon, Google

**Hint:** Find each component's size with DFS, BFS or Union-Find. Pairs in different components: keep `seen` (nodes processed so far) and for each component of size `s` add `s × seen`, then `seen += s`. Use `long`.

---

### E4 · Destination City

**🔗 [LC 1436 — Destination City](https://leetcode.com/problems/destination-city/)** · Easy
**Pattern:** Out-degree Zero | **Companies:** Yelp, Amazon

**Hint:** Put every start city in a set. The destination is the only end city that is never a start city.

---

### E5 · Find Center of Star Graph

**🔗 [LC 1791 — Find Center of Star Graph](https://leetcode.com/problems/find-center-of-star-graph/)** · Easy
**Pattern:** Graph properties | **Companies:** Amazon

**Hint:** In a star graph, the center node appears in every edge. Just check which node is common between `edges[0]` and
`edges[1]` — no traversal needed.

---

### E6 · Keys and Rooms

**🔗 [LC 841 — Keys and Rooms](https://leetcode.com/problems/keys-and-rooms/)** · Medium
**Pattern:** DFS reachability | **Companies:** Google, Amazon

**Hint:** Room 0 is unlocked. Keys in each room open other rooms. DFS/BFS from room 0 adding newly reachable rooms.
Return `visited.size() == n`.

---

### E7 · Find Champion II

**🔗 [LC 2924 — Find Champion II](https://leetcode.com/problems/find-champion-ii/)** · Medium
**Pattern:** In-degree Counting (DAG) | **Companies:** Amazon, Google

**Hint:** The champion is the unique node with in-degree 0. Count in-degrees; if exactly one node has 0, return it, otherwise return -1.

---

### E8 · Count Sub Islands

**🔗 [LC 1905 — Count Sub Islands](https://leetcode.com/problems/count-sub-islands/)** · Medium
**Pattern:** DFS flood fill | **Companies:** Google

**Hint:** DFS across grid2 islands. An island in grid2 is a sub-island of grid1 only if every cell of that island is
also land in grid1. Track with a flag: if any cell of the DFS is water in grid1, the whole island fails.

---

## 🟡 Medium Tier (15 Problems)

_Core Interview Patterns._

### M1 · Number of Operations to Make Network Connected

**🔗 [LC 1319 — Number of Operations to Make Network Connected](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)** · Medium
**Pattern:** Connected Components | **Companies:** Amazon, Google, Meta

**Hint:** If `edges < n - 1`, it's impossible. Otherwise count components (DFS/BFS over an adjacency list); you need `components - 1` moves, since each redundant cable can join two components.

---

### M2 · Open the Lock

**🔗 [LC 752 — Open the Lock](https://leetcode.com/problems/open-the-lock/)** · Medium
**Pattern:** BFS on an Implicit Graph | **Companies:** Google, Amazon, Microsoft

**Hint:** Each 4-digit string is a node with 8 neighbours (each wheel ±1). BFS from `"0000"`, skipping deadends and visited states. The level at which you reach the target is the answer.

---

### M3 · Reorder Routes to Make All Paths Lead to the City Zero

**🔗 [LC 1466 — Reorder Routes to Make All Paths Lead to the City Zero](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/)** · Medium
**Pattern:** Edge Direction as Cost | **Companies:** Amazon, Google

**Hint:** Store each edge in both directions, marked with cost 1 if it's an original direction (away from 0) and 0 if reversed. DFS from city 0 and sum the costs of edges you traverse.

---

### M4 · Course Schedule

**🔗 [LC 207 — Course Schedule](https://leetcode.com/problems/course-schedule/)** · Medium
**Pattern:** Cycle detection in directed graph | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Build directed graph: prerequisite → course. Run Kahn's topological sort. If you can process all n courses (
idx == n), no cycle exists → return true.

---

### M5 · Course Schedule II

**🔗 [LC 210 — Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)** · Medium
**Pattern:** Topological sort | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Same as LC 207 but return the topological order. Use Kahn's: when in-degree reaches 0, add to queue and to
result array. If result length < n, cycle exists.

---

### M6 · Number of Provinces

**🔗 [LC 547 — Number of Provinces](https://leetcode.com/problems/number-of-provinces/)** · Medium
**Pattern:** DFS connected components | **Companies:** Google, Amazon, Facebook

**Hint:** Input is an adjacency matrix. DFS/BFS from each unvisited city. Each traversal = one province. Very similar to
Number of Islands but on an adjacency matrix.

---

### M7 · Find Eventual Safe States

**🔗 [LC 802 — Find Eventual Safe States](https://leetcode.com/problems/find-eventual-safe-states/)** · Medium
**Pattern:** Reverse Graph + Topological Sort | **Companies:** Google, Amazon

**Hint:** Safe nodes are those that can't reach a cycle. Reverse the edges, start from terminal nodes (out-degree 0), and peel with Kahn's algorithm — every node peeled is safe. Or use DFS three-colouring.

---

### M8 · Clone Graph

**🔗 [LC 133 — Clone Graph](https://leetcode.com/problems/clone-graph/)** · Medium
**Pattern:** DFS/BFS with HashMap | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Use a `HashMap<Node, Node>` (original → clone). DFS: if `map.containsKey(node)`, return its clone. Otherwise
create a new node, add to map, then clone all neighbors recursively.

---

### M9 · Word Ladder

**🔗 [LC 127 — Word Ladder](https://leetcode.com/problems/word-ladder/)** · Hard
**Pattern:** BFS on implicit graph | **Companies:** Google, Amazon, Facebook, Microsoft

> ⚠️ LeetCode rates this **Hard** — the core BFS concept is Medium; the challenge is the implicit graph construction and
> avoiding TLE.

**Hint:** BFS where each word is a node. Two words are connected if they differ by exactly one letter. Try all 26
letters for each position. Use a set for O(1) lookup and remove words as visited. BFS level count = transformation
steps.

---

### M10 · Network Delay Time

**🔗 [LC 743 — Network Delay Time](https://leetcode.com/problems/network-delay-time/)** · Medium
**Pattern:** Dijkstra | **Companies:** Google, Amazon, Facebook, Uber

**Hint:** Build weighted directed adjacency list. Dijkstra from node `k`. Answer = max of all `dist[i]`. If any node has
`dist = ∞`, return -1.

---

### M11 · Path With Minimum Effort

**🔗 [LC 1631 — Path With Minimum Effort](https://leetcode.com/problems/path-with-minimum-effort/)** · Medium
**Pattern:** Dijkstra on grid | **Companies:** Google, Amazon

**Hint:** Nodes = grid cells. Edge weight = absolute height difference. Dijkstra where `dist[r][c]` = min effort to
reach that cell. Effort for a path = maximum edge weight along it.

---

### M12 · Is Graph Bipartite?

**🔗 [LC 785 — Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/)** · Medium
**Pattern:** BFS 2-coloring | **Companies:** Google, Amazon, Facebook

**Hint:** BFS coloring: assign color 0 to the start, alternate colors for neighbors. If any neighbor has the same color
as current node → not bipartite. Must handle disconnected graphs (loop all nodes).

---

### M13 · Find the City With the Smallest Number of Neighbors at a Threshold Distance

**🔗 [LC 1334 — Find the City With the Smallest Number of Neighbors at a Threshold Distance](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/)** · Medium
**Pattern:** Floyd-Warshall (all-pairs shortest path) | **Companies:** Google, Amazon

**Hint:** Run Floyd-Warshall to compute all-pairs shortest paths. For each city, count how many other cities are reachable within `distanceThreshold`. Return the city with the fewest reachable neighbors (ties broken by largest city index). Floyd-Warshall fits here because n ≤ 100.

---

### M14 · Min Cost to Connect All Points

**🔗 [LC 1584 — Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/)** · Medium
**Pattern:** MST (Prim's) | **Companies:** Google, Amazon

**Hint:** Each pair of points has an edge with weight = Manhattan distance. MST on this complete graph. Use Prim's with
a min-heap OR Kruskal's with sorted edges. Prim's is more efficient here since it avoids generating all O(n²) edges
upfront.

---

### M15 · Cheapest Flights Within K Stops

**🔗 [LC 787 — Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)** · Medium
**Pattern:** Modified Bellman-Ford | **Companies:** Google, Amazon, Uber

**Hint:** Bellman-Ford with at most K+1 rounds (K stops = K+1 edges). Key: copy `dist` array before each round to
prevent using updates from the same round. Dijkstra doesn't apply here because of the K-stop constraint changing the
state space.

---

## 🔴 Hard Tier (7 Problems)

_FAANG Mastery._

### H1 · Word Ladder II

**🔗 [LC 126 — Word Ladder II](https://leetcode.com/problems/word-ladder-ii/)** · Hard
**Pattern:** BFS + DFS (find all shortest paths) | **Companies:** Google, Amazon, Facebook

**Hint:** BFS to compute shortest distance from `beginWord` to every reachable word. Then DFS/backtracking from
`endWord` backward, following only edges that strictly decrease the BFS distance. This avoids storing all paths during
BFS.

**Why Hard?** Combining BFS distance labelling with DFS path reconstruction, handling the "all shortest paths"
requirement without TLE.

---

### H2 · Sort Items by Groups Respecting Dependencies

**🔗 [LC 1203 — Sort Items by Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/)** · Hard
**Pattern:** Two-Level Topological Sort | **Companies:** Google, Amazon

**Hint:** Give every ungrouped item its own new group. Build two graphs — item dependencies and group dependencies (edges between different groups) — and topologically sort both. Then emit items group by group in group order, each group's items in item order. Any cycle means return `[]`.

---

### H3 · Critical Connections in a Network

**🔗 [LC 1192 — Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/)** · Hard
**Pattern:** Tarjan's bridges algorithm | **Companies:** Amazon, Google, Uber

**Hint:** DFS tracking `disc[]` (discovery time) and `low[]` (lowest disc reachable via DFS subtree). Edge `(u,v)` is a
bridge if `low[v] > disc[u]` — meaning v's subtree can't reach u or above without this edge.

**Why Hard?** Tarjan's algorithm requires careful `low[]` update logic and parent tracking to avoid using the same
undirected edge bidirectionally.

---

### H4 · Reconstruct Itinerary

**🔗 [LC 332 — Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/)** · Hard
**Pattern:** Eulerian path (Hierholzer's algorithm) | **Companies:** Google, Amazon

**Hint:** Build adjacency list with sorted destinations (min-heap or sorted list). DFS Hierholzer: post-order add to
result. Reverse at end. The post-order trick ensures we don't get stuck in a dead end before exploring all other paths.

**Why Hard?** Recognizing this as Eulerian path + the post-order trick to avoid greedy dead ends.

---

### H5 · Swim in Rising Water

**🔗 [LC 778 — Swim in Rising Water](https://leetcode.com/problems/swim-in-rising-water/)** · Hard
**Pattern:** Dijkstra / Binary Search + BFS | **Companies:** Google

**Hint:** Dijkstra variant: `dist[r][c]` = min time to reach `(r,c)` = max elevation on the path (bottleneck path). PQ
ordered by current time. Alternatively: binary search on answer t + BFS to check if path exists using only cells ≤ t.

---

### H6 · Bus Routes

**🔗 [LC 815 — Bus Routes](https://leetcode.com/problems/bus-routes/)** · Hard
**Pattern:** BFS on route graph | **Companies:** Google, Uber

**Hint:** Nodes are BUS ROUTES (not stops). Two routes are connected if they share a stop. BFS from all routes
containing `source`. Answer = minimum bus changes + 1. Key insight: model routes as nodes to avoid O(stops²)
connections.

---

### H7 · Shortest Path in a Grid with Obstacles Elimination

**🔗 [LC 1293 — Shortest Path in a Grid with Obstacles Elimination](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/)** · Hard
**Pattern:** BFS with state = (row, col, k_remaining) | **Companies:** Google, Amazon, Uber

**Hint:** State is `(r, c, obstacles_remaining)`. BFS on this 3D state space. `visited[r][c][k]` = true if we've visited
`(r,c)` with `k` eliminations left. First time we reach `(m-1,n-1)`, return the BFS level.

**Why Hard?** Extending BFS state beyond just position. Recognizing that using more eliminations isn't always better (
visited must track k too).

---

## 🧠 Conceptual Check

1. **BFS vs DFS choice:** For "minimum moves in a maze", why is BFS strictly correct and DFS wrong? What property of BFS
   guarantees the shortest path?

2. **Multi-source BFS:** Why does seeding multiple sources at distance 0 give the correct result for Rotting Oranges?
   What would go wrong if you ran BFS separately from each source?

3. **Kahn's cycle detection:** In Course Schedule, Kahn's algorithm returns the topological order. How exactly does it
   tell you a cycle exists? What does `processedCount < n` mean structurally?

4. **Dijkstra stale entry:** Why does adding a duplicate entry to the PQ (instead of decrease-key) still give the
   correct result? What invariant ensures stale entries are always ignored safely?

5. **Kruskal's correctness:** Why is it safe to greedily always pick the minimum weight edge that doesn't form a cycle?
   What property of MSTs (the cut property) guarantees this greedy choice is always optimal?

6. **Bellman-Ford round limit:** In LC 787 (K stops), why do you need to copy the `dist` array before each round? What
   wrong answer would you get if you didn't?

7. **Implicit graph design:** In Word Ladder, the graph is never explicitly built. What makes BFS still correct on this
   implicit graph? How do you avoid visiting the same word twice?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                             |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Word Ladder II](https://leetcode.com/problems/word-ladder-ii/), [Sort Items by Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/), [Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/), [Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/) |
| **Google**    | [Word Ladder II](https://leetcode.com/problems/word-ladder-ii/), [Sort Items by Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/), [Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/), [Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/) |
| **Facebook**  | [Word Ladder II](https://leetcode.com/problems/word-ladder-ii/), [Course Schedule](https://leetcode.com/problems/course-schedule/), [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/), [Number of Provinces](https://leetcode.com/problems/number-of-provinces/)                                                                                             |
| **Microsoft** | [Open the Lock](https://leetcode.com/problems/open-the-lock/), [Course Schedule](https://leetcode.com/problems/course-schedule/), [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/), [Clone Graph](https://leetcode.com/problems/clone-graph/)                                                                                                               |
| **Uber**      | [Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/), [Bus Routes](https://leetcode.com/problems/bus-routes/), [Shortest Path in a Grid with Obstacles Elimination](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/), [Network Delay Time](https://leetcode.com/problems/network-delay-time/)   |

---

## ✅ Completion Checklist

- [ ] All 8 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 7 Hard problems attempted
- [ ] All 7 conceptual questions answered out loud
- [ ] Can write BFS shortest path template from memory
- [ ] Can write DFS flood fill template from memory
- [ ] Can write Kahn's topological sort from memory
- [ ] Can write Dijkstra's with min-heap from memory
- [ ] Can write Floyd-Warshall 3-loop DP from memory and know when V is small enough to use it
- [ ] Understand Tarjan's bridge condition (`low[v] > disc[u]`) and can implement it for LC 1192
- [ ] Know when to use BFS vs DFS vs Dijkstra vs Bellman-Ford vs Floyd-Warshall without hesitation
- [ ] Can apply the 4-question framework (nodes, edges, directed?, computing what?) to any new graph problem

---

**← [Lecture 16 · Heaps & Priority Queues](../Lecture16/Assignment.md)** &nbsp;·&nbsp; **[Lecture 18 · Two Pointers & Sliding Window](../Lecture18/Assignment.md) →**
