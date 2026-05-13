# 🕸️ Assignment 17 — Graphs

> **Lecture:** Topic 17 — Graphs
> **Phase:** 3 — Advanced DS · **Topic:** 17 of 30
> **Estimated Time:** 12 Days · **Total Problems:** 30 (8 Easy · 15 Medium · 7 Hard)
> **Goal:** Master the 6 graph patterns — BFS Shortest Path, DFS Flood Fill, Cycle Detection, Topological Sort,
> Dijkstra, MST.

---

## 🗺️ Pattern Recognition — Read Before Starting

| Signal Phrase                                            | Pattern            | Tool                               |
|----------------------------------------------------------|--------------------|------------------------------------|
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

## 🟢 Easy Tier (8 Problems)

---

### E1 · Find if Path Exists in Graph

**🔗 [LC 1971](https://leetcode.com/problems/find-if-path-exists-in-graph/)**
**Pattern:** BFS / DFS reachability | **Companies:** Amazon, Google

**Hint:** Build adjacency list. Run BFS or DFS from `source`. If you reach `destination`, return true. Classic
reachability check — the "hello world" of graph problems.

---

### E2 · Flood Fill

**🔗 [LC 733](https://leetcode.com/problems/flood-fill/)**
**Pattern:** DFS on grid | **Companies:** Amazon, Google

**Hint:** DFS from the starting cell. At each cell: if it matches the original color and hasn't been recolored yet,
update it and recurse into 4 neighbors. Early exit if `newColor == oldColor` to avoid infinite recursion.

---

### E3 · Number of Connected Components in Undirected Graph

**🔗 [LC 323](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)**
**Pattern:** DFS connected components | **Companies:** LinkedIn, Amazon

**Hint:** For each unvisited node run DFS/BFS and increment a counter. *(Union-Find is an alternative — covered in
Lecture 18.)*

---

### E4 · Island Perimeter

**🔗 [LC 463](https://leetcode.com/problems/island-perimeter/)**
**Pattern:** Grid traversal | **Companies:** Google

**Hint:** For each land cell, start with contribution = 4. Subtract 1 for each adjacent land neighbor. No DFS needed —
just a single pass. But can also be solved with DFS marking visited cells.

---

### E5 · Find Center of Star Graph

**🔗 [LC 1791](https://leetcode.com/problems/find-center-of-star-graph/)**
**Pattern:** Graph properties | **Companies:** Amazon

**Hint:** In a star graph, the center node appears in every edge. Just check which node is common between `edges[0]` and
`edges[1]` — no traversal needed.

---

### E6 · Keys and Rooms

**🔗 [LC 841](https://leetcode.com/problems/keys-and-rooms/)**
**Pattern:** DFS reachability | **Companies:** Google, Amazon

**Hint:** Room 0 is unlocked. Keys in each room open other rooms. DFS/BFS from room 0 adding newly reachable rooms.
Return `visited.size() == n`.

---

### E7 · Max Area of Island

**🔗 [LC 695](https://leetcode.com/problems/max-area-of-island/)**
**Pattern:** DFS flood fill | **Companies:** Amazon, Google, Facebook

**Hint:** DFS from each unvisited land cell (`1`). Return the size of the component by accumulating a count at each
recursive call. Track the global maximum across all DFS calls. Same flood fill template as Number of Islands — just
return area instead of a boolean.

---

### E8 · Count Sub Islands

**🔗 [LC 1905](https://leetcode.com/problems/count-sub-islands/)**
**Pattern:** DFS flood fill | **Companies:** Google

**Hint:** DFS across grid2 islands. An island in grid2 is a sub-island of grid1 only if every cell of that island is
also land in grid1. Track with a flag: if any cell of the DFS is water in grid1, the whole island fails.

---

## 🟡 Medium Tier — Core Interview Patterns (15 Problems)

---

### M1 · Number of Islands ⭐

**🔗 [LC 200](https://leetcode.com/problems/number-of-islands/)**
**Pattern:** DFS flood fill | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** DFS from each unvisited `'1'`, marking visited cells as `'0'` (or use a visited array). Each DFS call = one
island. Count how many times you start a DFS.

---

### M2 · Rotting Oranges ⭐

**🔗 [LC 994](https://leetcode.com/problems/rotting-oranges/)**
**Pattern:** Multi-source BFS | **Companies:** Amazon, Google, Facebook

**Hint:** Seed all initially rotten oranges into the queue. BFS level by level (each level = 1 minute). Track minutes
elapsed. After BFS, if any fresh orange remains, return -1.

---

### M3 · 01 Matrix ⭐

**🔗 [LC 542](https://leetcode.com/problems/01-matrix/)**
**Pattern:** Multi-source BFS | **Companies:** Amazon, Google

**Hint:** Seed all `0` cells into the queue at distance 0. BFS outward — `1` cells get their distance from the nearest
`0` naturally. Don't BFS from each `1` separately (TLE).

---

### M4 · Course Schedule ⭐

**🔗 [LC 207](https://leetcode.com/problems/course-schedule/)**
**Pattern:** Cycle detection in directed graph | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Build directed graph: prerequisite → course. Run Kahn's topological sort. If you can process all n courses (
idx == n), no cycle exists → return true.

---

### M5 · Course Schedule II ⭐

**🔗 [LC 210](https://leetcode.com/problems/course-schedule-ii/)**
**Pattern:** Topological sort | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Same as LC 207 but return the topological order. Use Kahn's: when in-degree reaches 0, add to queue and to
result array. If result length < n, cycle exists.

---

### M6 · Number of Provinces

**🔗 [LC 547](https://leetcode.com/problems/number-of-provinces/)**
**Pattern:** DFS connected components | **Companies:** Google, Amazon, Facebook

**Hint:** Input is an adjacency matrix. DFS/BFS from each unvisited city. Each traversal = one province. Very similar to
Number of Islands but on an adjacency matrix.

---

### M7 · Pacific Atlantic Water Flow

**🔗 [LC 417](https://leetcode.com/problems/pacific-atlantic-water-flow/)**
**Pattern:** Reverse BFS from borders | **Companies:** Google, Amazon

**Hint:** Instead of checking each cell, run BFS/DFS backward from the Pacific border and separately from the Atlantic
border. A cell is an answer if it's reachable from both.

---

### M8 · Clone Graph

**🔗 [LC 133](https://leetcode.com/problems/clone-graph/)**
**Pattern:** DFS/BFS with HashMap | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Use a `HashMap<Node, Node>` (original → clone). DFS: if `map.containsKey(node)`, return its clone. Otherwise
create a new node, add to map, then clone all neighbors recursively.

---

### M9 · Word Ladder ⭐

**🔗 [LC 127](https://leetcode.com/problems/word-ladder/)**
**Pattern:** BFS on implicit graph | **Companies:** Google, Amazon, Facebook, Microsoft
> ⚠️ LeetCode rates this **Hard** — the core BFS concept is Medium; the challenge is the implicit graph construction and
> avoiding TLE.

**Hint:** BFS where each word is a node. Two words are connected if they differ by exactly one letter. Try all 26
letters for each position. Use a set for O(1) lookup and remove words as visited. BFS level count = transformation
steps.

---

### M10 · Network Delay Time ⭐

**🔗 [LC 743](https://leetcode.com/problems/network-delay-time/)**
**Pattern:** Dijkstra | **Companies:** Google, Amazon, Facebook, Uber

**Hint:** Build weighted directed adjacency list. Dijkstra from node `k`. Answer = max of all `dist[i]`. If any node has
`dist = ∞`, return -1.

---

### M11 · Path With Minimum Effort

**🔗 [LC 1631](https://leetcode.com/problems/path-with-minimum-effort/)**
**Pattern:** Dijkstra on grid | **Companies:** Google, Amazon

**Hint:** Nodes = grid cells. Edge weight = absolute height difference. Dijkstra where `dist[r][c]` = min effort to
reach that cell. Effort for a path = maximum edge weight along it.

---

### M12 · Is Graph Bipartite?

**🔗 [LC 785](https://leetcode.com/problems/is-graph-bipartite/)**
**Pattern:** BFS 2-coloring | **Companies:** Google, Amazon, Facebook

**Hint:** BFS coloring: assign color 0 to the start, alternate colors for neighbors. If any neighbor has the same color
as current node → not bipartite. Must handle disconnected graphs (loop all nodes).

---

### M13 · Find the City With the Smallest Number of Neighbors ⭐

*

*🔗 [LC 1334](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/)
**
**Pattern:** Floyd-Warshall (all-pairs shortest path) | **Companies:** Google, Amazon

**Hint:** Run Floyd-Warshall to compute all-pairs shortest paths. For each city, count how many other cities are
reachable within `distanceThreshold`. Return the city with the fewest reachable neighbors (ties broken by largest city
index). Floyd-Warshall fits here because n ≤ 100.

---

### M14 · Min Cost to Connect All Points ⭐

**🔗 [LC 1584](https://leetcode.com/problems/min-cost-to-connect-all-points/)**
**Pattern:** MST (Prim's) | **Companies:** Google, Amazon

**Hint:** Each pair of points has an edge with weight = Manhattan distance. MST on this complete graph. Use Prim's with
a min-heap OR Kruskal's with sorted edges. Prim's is more efficient here since it avoids generating all O(n²) edges
upfront.

---

### M15 · Cheapest Flights Within K Stops ⭐

**🔗 [LC 787](https://leetcode.com/problems/cheapest-flights-within-k-stops/)**
**Pattern:** Modified Bellman-Ford | **Companies:** Google, Amazon, Uber

**Hint:** Bellman-Ford with at most K+1 rounds (K stops = K+1 edges). Key: copy `dist` array before each round to
prevent using updates from the same round. Dijkstra doesn't apply here because of the K-stop constraint changing the
state space.

---

## 🔴 Hard Tier — FAANG Mastery (7 Problems)

---

### H1 · Word Ladder II

**🔗 [LC 126](https://leetcode.com/problems/word-ladder-ii/)**
**Pattern:** BFS + DFS (find all shortest paths) | **Companies:** Google, Amazon, Facebook

**Hint:** BFS to compute shortest distance from `beginWord` to every reachable word. Then DFS/backtracking from
`endWord` backward, following only edges that strictly decrease the BFS distance. This avoids storing all paths during
BFS.

**Why Hard?** Combining BFS distance labelling with DFS path reconstruction, handling the "all shortest paths"
requirement without TLE.

---

### H2 · Alien Dictionary

**🔗 [LC 269](https://leetcode.com/problems/alien-dictionary/)** ⚠️ *LeetCode Premium*
**Pattern:** Topological sort on character ordering | **Companies:** Google, Amazon, Facebook, Microsoft

**Hint:** Compare adjacent words character by character to find ordering constraints (e.g., `'t' → 'f'`). Build directed
graph on characters, run Kahn's topo sort. If cycle exists, return `""`. If not all characters appear in constraints,
include them with in-degree 0 (any order is valid for unconstrained chars).

**Why Hard?** Edge case: `["abc","ab"]` is invalid (longer word before shorter prefix — detect this during comparison).
Building the constraint graph without missing or duplicating edges is the crux.

---

### H3 · Critical Connections in a Network ⭐

**🔗 [LC 1192](https://leetcode.com/problems/critical-connections-in-a-network/)**
**Pattern:** Tarjan's bridges algorithm | **Companies:** Amazon, Google, Uber

**Hint:** DFS tracking `disc[]` (discovery time) and `low[]` (lowest disc reachable via DFS subtree). Edge `(u,v)` is a
bridge if `low[v] > disc[u]` — meaning v's subtree can't reach u or above without this edge.

**Why Hard?** Tarjan's algorithm requires careful `low[]` update logic and parent tracking to avoid using the same
undirected edge bidirectionally.

---

### H4 · Reconstruct Itinerary

**🔗 [LC 332](https://leetcode.com/problems/reconstruct-itinerary/)**
**Pattern:** Eulerian path (Hierholzer's algorithm) | **Companies:** Google, Amazon

**Hint:** Build adjacency list with sorted destinations (min-heap or sorted list). DFS Hierholzer: post-order add to
result. Reverse at end. The post-order trick ensures we don't get stuck in a dead end before exploring all other paths.

**Why Hard?** Recognizing this as Eulerian path + the post-order trick to avoid greedy dead ends.

---

### H5 · Swim in Rising Water

**🔗 [LC 778](https://leetcode.com/problems/swim-in-rising-water/)**
**Pattern:** Dijkstra / Binary Search + BFS | **Companies:** Google

**Hint:** Dijkstra variant: `dist[r][c]` = min time to reach `(r,c)` = max elevation on the path (bottleneck path). PQ
ordered by current time. Alternatively: binary search on answer t + BFS to check if path exists using only cells ≤ t.

---

### H6 · Bus Routes

**🔗 [LC 815](https://leetcode.com/problems/bus-routes/)**
**Pattern:** BFS on route graph | **Companies:** Google, Uber

**Hint:** Nodes are BUS ROUTES (not stops). Two routes are connected if they share a stop. BFS from all routes
containing `source`. Answer = minimum bus changes + 1. Key insight: model routes as nodes to avoid O(stops²)
connections.

---

### H7 · Shortest Path in a Grid with Obstacles Elimination ⭐

**🔗 [LC 1293](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/)**
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

## 🏢 Company Focus Table

| Company       | Must-Know Problems                                                                                      |
|---------------|---------------------------------------------------------------------------------------------------------|
| **Amazon**    | Number of Islands (LC 200), Course Schedule (LC 207), Word Ladder (LC 127), Clone Graph (LC 133)        |
| **Google**    | Word Ladder (LC 127), Pacific Atlantic (LC 417), Critical Connections (LC 1192), Swim in Water (LC 778) |
| **Meta**      | Number of Islands (LC 200), Course Schedule II (LC 210), Clone Graph (LC 133), Rotting Oranges (LC 994) |
| **Microsoft** | Course Schedule (LC 207), Network Delay (LC 743), Word Ladder (LC 127)                                  |
| **Uber**      | Network Delay (LC 743), Cheapest Flights (LC 787), Shortest Path with Eliminations (LC 1293)            |

---

## ✅ Completion Checklist

* [ ] Completed all 8 Easy problems
* [ ] Completed all 15 Medium problems (including LC 1334 Floyd-Warshall)
* [ ] Attempted all 7 Hard problems
* [ ] Can answer all 7 Conceptual Check questions verbally
* [ ] Can write BFS shortest path template from memory
* [ ] Can write DFS flood fill template from memory
* [ ] Can write Kahn's topological sort from memory
* [ ] Can write Dijkstra's with min-heap from memory
* [ ] Can write Floyd-Warshall 3-loop DP from memory and know when V is small enough to use it
* [ ] Understand Tarjan's bridge condition (`low[v] > disc[u]`) and can implement it for LC 1192
* [ ] Know when to use BFS vs DFS vs Dijkstra vs Bellman-Ford vs Floyd-Warshall without hesitation
* [ ] Can apply the 4-question framework (nodes, edges, directed?, computing what?) to any new graph problem

---

**← Topic 16: Heaps & Priority Queues** &nbsp;&nbsp;|&nbsp;&nbsp; **Topic 18: Union-Find →**
