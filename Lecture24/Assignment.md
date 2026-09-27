# 🔗 Assignment 24 — Union-Find (Disjoint Set Union)

> **Lecture:** 24 of 38 — Union-Find (Disjoint Set Union)
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 4 days · **Total Problems:** 20 (6 Easy · 10 Medium · 4 Hard)
> **Goal:** Ten lines of code, then all the thinking goes into deciding what to unite.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                      | Pattern              | Move                                          |
| ------------------------------------------ | -------------------- | --------------------------------------------- |
| "are these two connected?"                 | Union-Find           | `find(a) == find(b)` — near O(1)              |
| "how many groups / provinces / islands"    | Count Components     | one counter, decremented per successful union |
| "which edge creates a cycle"               | Failed Union         | the first union that returns false            |
| "merge accounts / emails / names"          | Map to Ids First     | give every object an integer, then union      |
| edges arrive over time, queries in between | Union-Find           | DFS would rebuild the traversal each time     |
| things get removed over time               | Reverse the Timeline | DSU can add, never split                      |

---

## 🟢 Easy Tier (6 Problems)

_Grouping warm-ups: canonical keys and counting by group, before the structure arrives._

### E1 · Merge Similar Items

**🔗 [LC 2363 — Merge Similar Items](https://leetcode.com/problems/merge-similar-items/)** · Easy
**Pattern:** Group by Key | **Companies:** Amazon

**Hint:** Two sorted lists merged on a shared key — the same combine step a DSU does when it groups members by root. A map from value to total weight is enough.

---

### E2 · Divide Array Into Equal Pairs

**🔗 [LC 2206 — Divide Array Into Equal Pairs](https://leetcode.com/problems/divide-array-into-equal-pairs/)** · Easy
**Pattern:** Pair by Equality | **Companies:** Amazon

**Hint:** Count each value. Every group must have an even size, which is the simplest form of "is this partition valid?".

---

### E3 · Count Number of Pairs With Absolute Difference K

**🔗 [LC 2006 — Count Number of Pairs With Absolute Difference K](https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/)** · Easy
**Pattern:** Complement Counting | **Companies:** Amazon, Google

**Hint:** Count each value in a map; for every `x`, add `count[x - k]`. Grouping by value first, comparing second.

---

### E4 · Count Pairs Of Similar Strings

**🔗 [LC 2506 — Count Pairs Of Similar Strings](https://leetcode.com/problems/count-pairs-of-similar-strings/)** · Easy
**Pattern:** Signature as the Group Key | **Companies:** Amazon

**Hint:** Two words are similar when their letter _sets_ match, so reduce each word to a 26-bit mask and count equal masks — a canonical key, exactly like sorting characters for anagrams.

---

### E5 · Count Items Matching a Rule

**🔗 [LC 1773 — Count Items Matching a Rule](https://leetcode.com/problems/count-items-matching-a-rule/)** · Easy
**Pattern:** Filter by Attribute | **Companies:** Amazon

**Hint:** Pick the field named by `ruleKey` and count matches. A warm-up in mapping a name to an index before you do it for DSU ids.

---

### E6 · Counting Words With a Given Prefix

**🔗 [LC 2185 — Counting Words With a Given Prefix](https://leetcode.com/problems/counting-words-with-a-given-prefix/)** · Easy
**Pattern:** Prefix Match | **Companies:** Amazon

**Hint:** Count words starting with the given prefix. Simple, but note how a shared prefix defines a group — the idea Tries formalise in Lecture 29.

---

## 🟡 Medium Tier (10 Problems)

_The structure proper — nodes, letters, emails, grid cells and ratios._

### M1 · Redundant Connection

**🔗 [LC 684 — Redundant Connection](https://leetcode.com/problems/redundant-connection/)** · Medium
**Pattern:** Cycle Detection | **Companies:** Amazon, Google, Meta

**Hint:** Union the edges in order; the first union that fails joins two already-connected nodes, so that edge closes the cycle.

---

### M2 · Satisfiability of Equality Equations

**🔗 [LC 990 — Satisfiability of Equality Equations](https://leetcode.com/problems/satisfiability-of-equality-equations/)** · Medium
**Pattern:** Union, Then Verify | **Companies:** Google, Amazon, Meta

**Hint:** Union every `==` pair first, then check each `!=` pair. Doing both in one pass lets a later equality invalidate an earlier check.

---

### M3 · Accounts Merge

**🔗 [LC 721 — Accounts Merge](https://leetcode.com/problems/accounts-merge/)** · Medium
**Pattern:** Map to Ids, Then Union | **Companies:** Amazon, Google, Meta

**Hint:** Give every email an id and remember its owner. Union each account's emails to its first email, then group by root and sort.

---

### M4 · Most Stones Removed with Same Row or Column

**🔗 [LC 947 — Most Stones Removed with Same Row or Column](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/)** · Medium
**Pattern:** Union Rows with Columns | **Companies:** Google, Amazon, Meta

**Hint:** The answer is `stones − components`. Union row `r` with column `c`, keeping the two id ranges apart so a row never collides with a column.

---

### M5 · Regions Cut By Slashes

**🔗 [LC 959 — Regions Cut By Slashes](https://leetcode.com/problems/regions-cut-by-slashes/)** · Medium
**Pattern:** Split Each Cell | **Companies:** Google, Amazon

**Hint:** Cut every cell into four triangles. Union across cell borders always, and inside a cell according to the slash. The component count is the number of regions.

---

### M6 · Lexicographically Smallest Equivalent String

**🔗 [LC 1061 — Lexicographically Smallest Equivalent String](https://leetcode.com/problems/lexicographically-smallest-equivalent-string/)** · Medium
**Pattern:** Smallest Member as Root | **Companies:** Google, Amazon

**Hint:** Union the matching letters, but always make the alphabetically smaller letter the root. Then map each character of the string to its root.

---

### M7 · Minimum Score of a Path Between Two Cities

**🔗 [LC 2492 — Minimum Score of a Path Between Two Cities](https://leetcode.com/problems/minimum-score-of-a-path-between-two-cities/)** · Medium
**Pattern:** Components + Minimum Edge | **Companies:** Amazon, Google

**Hint:** Any path may reuse edges, so the answer is the smallest edge weight in the component containing city 1. Union everything, then scan the edges once.

---

### M8 · Evaluate Division

**🔗 [LC 399 — Evaluate Division](https://leetcode.com/problems/evaluate-division/)** · Medium
**Pattern:** Union-Find with Ratios | **Companies:** Google, Amazon, Meta

**Hint:** Store each node's value relative to its root and multiply the ratios during path compression. Same root means the answer is a division; different roots mean −1.

---

### M9 · Minimize Hamming Distance After Swap Operations

**🔗 [LC 1722 — Minimize Hamming Distance After Swap Operations](https://leetcode.com/problems/minimize-hamming-distance-after-swap-operations/)** · Medium
**Pattern:** Union the Swappable Indices | **Companies:** Google, Amazon

**Hint:** Indices connected by swaps can be permuted freely, so within each group compare the multiset of source and target values; mismatches count as errors.

---

### M10 · Count the Number of Complete Components

**🔗 [LC 2685 — Count the Number of Complete Components](https://leetcode.com/problems/count-the-number-of-complete-components/)** · Medium
**Pattern:** Count Nodes and Edges per Group | **Companies:** Amazon, Google

**Hint:** A component with `k` nodes is complete when it has exactly `k(k−1)/2` edges. Union everything, then tally nodes and edges per root.

---

## 🔴 Hard Tier (4 Problems)

_DSU carrying an extra argument: direction, similarity, sorted queries or value order._

### H1 · Redundant Connection II

**🔗 [LC 685 — Redundant Connection II](https://leetcode.com/problems/redundant-connection-ii/)** · Hard
**Pattern:** Directed Variant | **Companies:** Google, Amazon

**Hint:** A directed graph adds a second failure mode: a node with two parents. Find that node's two candidate edges first, then use DSU to decide which one to drop.

---

### H2 · Similar String Groups

**🔗 [LC 839 — Similar String Groups](https://leetcode.com/problems/similar-string-groups/)** · Hard
**Pattern:** Union on Similarity | **Companies:** Google, Amazon

**Hint:** Compare every pair of strings (they are short) and union those differing in at most two positions. The answer is the number of components.

---

### H3 · Checking Existence of Edge Length Limited Paths

**🔗 [LC 1697 — Checking Existence of Edge Length Limited Paths](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/)** · Hard
**Pattern:** Sort Edges + Sort Queries | **Companies:** Google, Amazon

**Hint:** Answer queries offline: sort edges by weight and queries by limit, then sweep, adding edges below the current limit before each connectivity check.

---

### H4 · Number of Good Paths

**🔗 [LC 2421 — Number of Good Paths](https://leetcode.com/problems/number-of-good-paths/)** · Hard
**Pattern:** Sort by Value, Union Upwards | **Companies:** Google, Amazon

**Hint:** Process nodes in increasing value, uniting each node with neighbours of smaller or equal value. Count paths as groups merge, tracking how many maximum-value nodes each root holds.

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The two optimisations:** What does path compression fix, and what does union by size fix? Give the input that breaks a DSU without each one.
2. **Complexity:** What is α(n), and why do we treat O(α(n)) as constant?
3. **Cycles:** Why does a failed union mean a cycle in an undirected graph? Does the same argument hold for directed graphs?
4. **Id spaces:** In Most Stones Removed you union rows with columns. What goes wrong if both use the same range of indices?
5. **DSU vs BFS:** Give one problem where DSU is clearly better, and one where BFS is — and say what makes the difference.
6. **Deletion:** DSU cannot split a group. How do problems that remove edges or bricks get solved anyway?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                               |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon** | [Redundant Connection II](https://leetcode.com/problems/redundant-connection-ii/), [Similar String Groups](https://leetcode.com/problems/similar-string-groups/), [Checking Existence of Edge Length Limited Paths](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/), [Number of Good Paths](https://leetcode.com/problems/number-of-good-paths/)     |
| **Google** | [Redundant Connection II](https://leetcode.com/problems/redundant-connection-ii/), [Similar String Groups](https://leetcode.com/problems/similar-string-groups/), [Checking Existence of Edge Length Limited Paths](https://leetcode.com/problems/checking-existence-of-edge-length-limited-paths/), [Number of Good Paths](https://leetcode.com/problems/number-of-good-paths/)     |
| **Meta**   | [Redundant Connection](https://leetcode.com/problems/redundant-connection/), [Satisfiability of Equality Equations](https://leetcode.com/problems/satisfiability-of-equality-equations/), [Accounts Merge](https://leetcode.com/problems/accounts-merge/), [Most Stones Removed with Same Row or Column](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/) |

---

## ✅ Completion Checklist

- [ ] All 6 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write a DSU class from memory in under three minutes
- [ ] I can decide what to union — and with what ids — before writing any code

---

**← [Lecture 23 · Divide & Conquer](../Lecture23/Assignment.md)** &nbsp;·&nbsp; **[Lecture 25 · Dynamic Programming I — Foundations & 1D](../Lecture25/Assignment.md) →**
