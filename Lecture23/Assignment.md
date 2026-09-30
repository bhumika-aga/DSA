# 🛡️ Assignment 23 — Graphs III — MST, Bipartite & Bridges

> **Lecture:** 23 of 45 — Graphs III — MST, Bipartite & Bridges
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 4 days · **Total Problems:** 10 (0 Easy · 7 Medium · 3 Hard)
> **Goal:** Answer structural questions about a graph: cheapest connection, two-colouring, and the edges everything depends on.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                | Pattern                    | Move                                                       |
| ---------------------------------------------------- | -------------------------- | ---------------------------------------------------------- |
| Connect everything as cheaply as possible            | MST — Kruskal or Prim      | Sort edges + union-find, or grow from one node with a heap |
| Sparse graph, edges given as a list                  | Kruskal                    | Sorting edges dominates: O(E log E)                        |
| Dense graph, or edges easy to enumerate per node     | Prim                       | O(E log V) with a priority queue                           |
| Split into two groups with no conflict inside either | Bipartite 2-colouring      | BFS/DFS assigning alternating colours                      |
| Which single edge would disconnect the graph?        | Tarjan bridges             | Compare low[child] with disc[parent]                       |
| Use every edge exactly once                          | Eulerian path (Hierholzer) | Check degrees, then build the path backwards               |

---

## 🟢 Easy Tier (0 Problems)

_No Easy problems here — graph algorithms at this level simply do not have them. Start with the Medium tier._

## 🟡 Medium Tier (7 Problems)

_Spanning trees, two-colouring and degree arguments — structural questions rather than routing ones._

### M1 · Is Graph Bipartite?

**🔗 [LC 785 — Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/)** · Medium
**Pattern:** BFS 2-coloring | **Companies:** Google, Amazon, Meta

**Hint:** BFS coloring: assign color 0 to the start, alternate colors for neighbours. If any neighbour has the same color
as current node → not bipartite. Must handle disconnected graphs (loop all nodes).

---

### M2 · Min Cost to Connect All Points

**🔗 [LC 1584 — Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/)** · Medium
**Pattern:** MST (Prim's) | **Companies:** Google, Amazon

**Hint:** Each pair of points has an edge with weight = Manhattan distance. MST on this complete graph. Use Prim's with
a min-heap OR Kruskal's with sorted edges. Prim's is more efficient here since it avoids generating all O(n²) edges
upfront.

---

### M3 · Possible Bipartition

**🔗 [LC 886 — Possible Bipartition](https://leetcode.com/problems/possible-bipartition/)** · Medium
**Pattern:** Bipartite 2-colouring | **Companies:** Amazon, Google

**Hint:** "Dislikes" are edges. Two groups means two colours — the same BFS as Is Graph Bipartite.

---

### M4 · Maximal Network Rank

**🔗 [LC 1615 — Maximal Network Rank](https://leetcode.com/problems/maximal-network-rank/)** · Medium
**Pattern:** Degree counting | **Companies:** Amazon, Google

**Hint:** Rank is deg(a) + deg(b), minus one if they are directly connected. Only the highest-degree nodes can win.

---

### M5 · Detonate the Maximum Bombs

**🔗 [LC 2101 — Detonate the Maximum Bombs](https://leetcode.com/problems/detonate-the-maximum-bombs/)** · Medium
**Pattern:** Directed reachability | **Companies:** Amazon, Google

**Hint:** Build a directed edge a→b when b is inside a, then DFS from every bomb and take the best count.

---

### M6 · Minimum Fuel Cost to Report to the Capital

**🔗 [LC 2477 — Minimum Fuel Cost to Report to the Capital](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/)** · Medium
**Pattern:** Tree DFS accumulating passengers | **Companies:** Google, Amazon

**Hint:** Post-order: every subtree reports how many people it is sending up, and the edge cost is ceil(people ÷ seats).

---

### M7 · Minimum Height Trees

**🔗 [LC 310 — Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/)** · Medium
**Pattern:** Topological peeling from the leaves | **Companies:** Google, Amazon

**Hint:** Repeatedly strip the degree-1 nodes. Whatever survives last — one node or two — is the answer.

---

## 🔴 Hard Tier (3 Problems)

_Bridges, Eulerian paths, and an MST question that asks which edges matter rather than what the total is._

### H1 · Critical Connections in a Network

**🔗 [LC 1192 — Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/)** · Hard
**Pattern:** Tarjan's bridges algorithm | **Companies:** Amazon, Google, Uber

**Hint:** DFS tracking `disc[]` (discovery time) and `low[]` (lowest disc reachable via DFS subtree). Edge `(u,v)` is a
bridge if `low[v] > disc[u]` — meaning v's subtree can't reach u or above without this edge.

**Why Hard?** Tarjan's algorithm requires careful `low[]` update logic and parent tracking to avoid using the same
undirected edge bidirectionally.

---

### H2 · Reconstruct Itinerary

**🔗 [LC 332 — Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/)** · Hard
**Pattern:** Eulerian path (Hierholzer's algorithm) | **Companies:** Google, Amazon

**Hint:** Build adjacency list with sorted destinations (min-heap or sorted list). DFS Hierholzer: post-order add to
result. Reverse at end. The post-order trick ensures we don't get stuck in a dead end before exploring all other paths.

**Why Hard?** Recognising this as Eulerian path + the post-order trick to avoid greedy dead ends.

---

### H3 · Find Critical and Pseudo-Critical Edges in Minimum Spanning Tree

**🔗 [LC 1489 — Find Critical and Pseudo-Critical Edges in Minimum Spanning Tree](https://leetcode.com/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/)** · Hard
**Pattern:** Kruskal, run three ways | **Companies:** Google, Amazon

**Hint:** Build the MST weight once. An edge is critical if excluding it raises the weight, pseudo-critical if forcing it in keeps the weight the same.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — Kruskal: sort E edges, then union-find

// Snippet 2 — Prim with a binary heap

// Snippet 3 — Prim with an array scan, on a dense graph

// Snippet 4 — bipartite check by BFS two-colouring

// Snippet 5 — Tarjan's bridge-finding

// Snippet 6 — Hierholzer's Eulerian path over E edges
```

**Complexity Answers:**

1. **O(E log E)** — sorting dominates.
2. **O(E log V)**.
3. **O(V²)** — best for dense graphs.
4. **O(V + E)**.
5. **O(V + E)** — one DFS.
6. **O(E)**.

---

## 🔍 Self-Assessment — True / False

1. A minimum spanning tree of V nodes has V − 1 edges. → **True**
2. The minimum spanning tree is always unique. → **False** — only when all edge weights are distinct
3. A graph is bipartite exactly when it has no odd-length cycle. → **True**
4. Kruskal needs a way to detect when an edge would form a cycle. → **True** — that is what union-find provides
5. An edge that lies on a cycle can be a bridge. → **False** — removing it leaves the cycle's other path
6. Prim and Kruskal can give MSTs with different total weights. → **False** — any two MSTs of a graph have the same total

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **MST correctness:** Why is it safe to greedily take the cheapest edge that does not form a cycle?
2. **Kruskal vs Prim:** Give the complexity of each and say which you would pick for a dense graph.
3. **Uniqueness:** Is the minimum spanning tree unique? Under what condition is it?
4. **Bipartite:** Explain why "two-colourable" and "no odd cycle" are the same statement.
5. **Low-link:** Define disc and low in your own words. Why does low[v] > disc[u] mean (u, v) is a bridge?
6. **Back edges:** In the bridge algorithm you skip the edge you arrived on — but only once. Why does that matter for parallel edges?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon** | [Find Critical and Pseudo-Critical Edges in Minimum Spanning Tree](https://leetcode.com/problems/find-critical-and-pseudo-critical-edges-in-minimum-spanning-tree/), [Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/), [Detonate the Maximum Bombs](https://leetcode.com/problems/detonate-the-maximum-bombs/), [Maximal Network Rank](https://leetcode.com/problems/maximal-network-rank/) |
| **Google** | [Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/), [Minimum Fuel Cost to Report to the Capital](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/), [Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/), [Possible Bipartition](https://leetcode.com/problems/possible-bipartition/)                                       |
| **Meta**   | [Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/)                                                                                                                                                                                                                                                                                                                                                 |
| **Uber**   | [Critical Connections in a Network](https://leetcode.com/problems/critical-connections-in-a-network/)                                                                                                                                                                                                                                                                                                                    |

---

## ✅ Completion Checklist

- [ ] All 7 Medium problems solved
- [ ] All 3 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write Kruskal with union-find and Prim with a heap
- [ ] I can two-colour a graph and explain the odd-cycle connection
- [ ] I can find every bridge in one DFS and explain low-link

---

**← [Lecture 22 · Graphs II — Topological Sort & Shortest Paths](../Lecture22/Assignment.md)** &nbsp;·&nbsp; **[Lecture 24 · Backtracking — Systematic Search](../Lecture24/Assignment.md) →**
