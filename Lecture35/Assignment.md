# 🎛️ Assignment 35 — Dynamic Programming IV — Interval, Tree, Bitmask & Digit

> **Lecture:** 35 of 45 — Dynamic Programming IV — Interval, Tree, Bitmask & Digit
> **Phase:** 4 — Dynamic Programming
> **Estimated Time:** 7 days · **Total Problems:** 25 (5 Easy · 12 Medium · 8 Hard)
> **Goal:** Recognise the four advanced DP state shapes from the constraints alone, and write each template without looking it up.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                                     | Pattern                  | Move                                                               |
| ------------------------------------------------------------------------- | ------------------------ | ------------------------------------------------------------------ |
| Answer depends on a contiguous range, and splitting it changes the pieces | Interval DP              | dp`[i][j]`, loop over length, pivot k inside                       |
| Removing an element merges its neighbours                                 | Interval DP, think LAST  | The last one removed still has the original boundaries             |
| Two players alternate, both play optimally                                | Interval DP on advantage | dp`[i][j]` = my score − yours; flip the sign at the recursive call |
| Question asked about every subtree                                        | Tree DP                  | Post-order walk, return a tuple, combine at the parent             |
| Question asked about every node as a root                                 | Rerooting                | Pass 1 down for sizes, pass 2 up to patch in O(1)                  |
| n ≤ 20 and the answer needs a set of used items                           | Bitmask DP               | dp[mask], position = popcount(mask)                                |
| Shortest walk that must cover everything                                  | Bitmask BFS              | State = (node, visitedMask)                                        |
| Count numbers in [A, B] with a digit property                             | Digit DP                 | count(pos, tight, started, state), answer = f(B) − f(A−1)          |

---

## 🟢 Easy Tier (5 Problems)

_Tree DP with the smallest possible state, plus a bitmask warm-up. The point is the shape of the recursion: walk post-order, return something, combine it at the parent._

### E1 · Binary Tree Tilt

**🔗 [LC 563 — Binary Tree Tilt](https://leetcode.com/problems/binary-tree-tilt/)** · Easy
**Pattern:** Tree DP (post-order tuple) | **Companies:** Amazon · Microsoft

**Hint:** Return the subtree sum from the walk and accumulate the tilt on the way up — one pass, no repeated sums.

---

### E2 · Sum of Root To Leaf Binary Numbers

**🔗 [LC 1022 — Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)** · Easy
**Pattern:** Tree DP (path state) | **Companies:** Amazon · Meta

**Hint:** Carry the number built so far down the recursion; add it at the leaves only.

---

### E3 · Univalued Binary Tree

**🔗 [LC 965 — Univalued Binary Tree](https://leetcode.com/problems/univalued-binary-tree/)** · Easy
**Pattern:** Tree DP (boolean fold) | **Companies:** Amazon

**Hint:** Compare every node with the root value and AND the two children’s answers.

---

### E4 · Binary Watch

**🔗 [LC 401 — Binary Watch](https://leetcode.com/problems/binary-watch/)** · Easy
**Pattern:** Bitmask enumeration | **Companies:** Amazon · Google

**Hint:** There are only 1024 times; enumerate masks and keep those whose popcount matches.

---

### E5 · Second Minimum Node In a Binary Tree

**🔗 [LC 671 — Second Minimum Node In a Binary Tree](https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/)** · Easy
**Pattern:** Tree DP (two bests) | **Companies:** Amazon · Google

**Hint:** Track the smallest and the second smallest as you walk — the second value is the answer.

---

## 🟡 Medium Tier (12 Problems)

_The working core of the lecture — interval DP, game DP on an advantage, and your first real bitmask states. Read the constraints before you plan; they name the technique._

### M1 · Guess Number Higher or Lower II

**🔗 [LC 375 — Guess Number Higher or Lower II](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)** · Medium
**Pattern:** Interval DP (game) | **Companies:** Google · Amazon

**Hint:** dp`[i][j]` = min over k of k + max(dp`[i][k-1]`, dp`[k+1][j]`) — you pay for the worse branch.

---

### M2 · Stone Game

**🔗 [LC 877 — Stone Game](https://leetcode.com/problems/stone-game/)** · Medium
**Pattern:** Interval DP (game, advantage) | **Companies:** Amazon · Meta

**Hint:** dp`[i][j]` is the current player’s lead; take from either end and subtract the opponent’s lead.

---

### M3 · Stone Game VII

**🔗 [LC 1690 — Stone Game VII](https://leetcode.com/problems/stone-game-vii/)** · Medium
**Pattern:** Interval DP (game, advantage) | **Companies:** Google · Amazon

**Hint:** Same recurrence as Stone Game VII with the cost of the removed stone folded in.

---

### M4 · Predict the Winner

**🔗 [LC 486 — Predict the Winner](https://leetcode.com/problems/predict-the-winner/)** · Medium
**Pattern:** Interval DP (game, advantage) | **Companies:** Amazon · Google · Adobe

**Hint:** Identical to Stone Game — return whether the lead from the full range is ≥ 0.

---

### M5 · Minimum Score Triangulation of Polygon

**🔗 [LC 1039 — Minimum Score Triangulation of Polygon](https://leetcode.com/problems/minimum-score-triangulation-of-polygon/)** · Medium
**Pattern:** Interval DP (triangulation) | **Companies:** Amazon · Google

**Hint:** Fix the edge (i, j) and pick the third vertex k — the same pivot loop as Burst Balloons.

---

### M6 · Longest ZigZag Path in a Binary Tree

**🔗 [LC 1372 — Longest ZigZag Path in a Binary Tree](https://leetcode.com/problems/longest-zigzag-path-in-a-binary-tree/)** · Medium
**Pattern:** Tree DP (direction state) | **Companies:** Amazon · Google

**Hint:** Each node returns two lengths: the best zigzag continuing left, and continuing right.

---

### M7 · Binary Tree Coloring Game

**🔗 [LC 1145 — Binary Tree Coloring Game](https://leetcode.com/problems/binary-tree-coloring-game/)** · Medium
**Pattern:** Tree DP (three regions) | **Companies:** Amazon · Meta

**Hint:** Find x’s node, then compare its left size, right size, and the rest against n ÷ 2.

---

### M8 · Beautiful Arrangement

**🔗 [LC 526 — Beautiful Arrangement](https://leetcode.com/problems/beautiful-arrangement/)** · Medium
**Pattern:** Bitmask DP | **Companies:** Google · Amazon

**Hint:** The used set is the whole state; the position is popcount(mask) + 1.

---

### M9 · Maximum Product of the Length of Two Palindromic Subsequences

**🔗 [LC 2002 — Maximum Product of the Length of Two Palindromic Subsequences](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/)** · Medium
**Pattern:** Bitmask enumeration | **Companies:** Amazon · Google

**Hint:** Enumerate all 2ⁿ splits, keep the palindromic halves, and multiply the lengths.

---

### M10 · Can I Win

**🔗 [LC 464 — Can I Win](https://leetcode.com/problems/can-i-win/)** · Medium
**Pattern:** Bitmask DP (game) | **Companies:** Amazon · Google · Bloomberg

**Hint:** Memoise on the mask of used numbers; you win if some unused move loses for the opponent.

---

### M11 · Rotated Digits

**🔗 [LC 788 — Rotated Digits](https://leetcode.com/problems/rotated-digits/)** · Medium
**Pattern:** Digit DP (or precompute) | **Companies:** Google

**Hint:** Per digit: 0/1/8 are neutral, 2/5/6/9 make it different, 3/4/7 kill the number.

---

### M12 · Count Numbers with Unique Digits

**🔗 [LC 357 — Count Numbers with Unique Digits](https://leetcode.com/problems/count-numbers-with-unique-digits/)** · Medium
**Pattern:** Digit DP (counting) | **Companies:** Google · Amazon

**Hint:** Count numbers with no repeated digit by position: 9 × 9 × 8 × … — or run the skeleton.

---

## 🔴 Hard Tier (8 Problems)

_Interval DP where the split is subtle, rerooting, bitmask search, and digit DP. These are the versions interviewers actually ask when they want to see you choose a state._

### H1 · Burst Balloons

**🔗 [LC 312 — Burst Balloons](https://leetcode.com/problems/burst-balloons/)** · Hard
**Pattern:** Interval DP (think last) | **Companies:** Google · Amazon · Meta

**Hint:** Pad with 1s and choose which balloon bursts last; its neighbours are then the boundaries.

---

### H2 · Minimum Cost to Merge Stones

**🔗 [LC 1000 — Minimum Cost to Merge Stones](https://leetcode.com/problems/minimum-cost-to-merge-stones/)** · Hard
**Pattern:** Interval DP (k-way merge) | **Companies:** Google · Amazon

**Hint:** Split so the left part collapses to a multiple of (k − 1) piles; merge only when the length allows it.

---

### H3 · Strange Printer

**🔗 [LC 664 — Strange Printer](https://leetcode.com/problems/strange-printer/)** · Hard
**Pattern:** Interval DP (strange printer) | **Companies:** Google · Amazon

**Hint:** If s[i] = s[k], printing them together is free: dp`[i][j]` = dp`[i+1][j]` patched by matching characters.

---

### H4 · Minimum Cost to Cut a Stick

**🔗 [LC 1547 — Minimum Cost to Cut a Stick](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/)** · Hard
**Pattern:** Interval DP (coordinates) | **Companies:** Google · Amazon

**Hint:** Add 0 and n as sentinels, sort, and pay (cuts[j] − cuts[i]) at every split.

---

### H5 · Palindrome Partitioning II

**🔗 [LC 132 — Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/)** · Hard
**Pattern:** Interval DP + linear DP | **Companies:** Google · Amazon

**Hint:** Precompute the palindrome table with the length loop, then do a one-dimensional cut DP over it.

---

### H6 · Sum of Distances in Tree

**🔗 [LC 834 — Sum of Distances in Tree](https://leetcode.com/problems/sum-of-distances-in-tree/)** · Hard
**Pattern:** Tree DP (rerooting) | **Companies:** Google · Amazon · Meta

**Hint:** Two passes: sizes and inward sums down, then answer[v] = answer[u] − size[v] + (n − size[v]).

---

### H7 · Shortest Path Visiting All Nodes

**🔗 [LC 847 — Shortest Path Visiting All Nodes](https://leetcode.com/problems/shortest-path-visiting-all-nodes/)** · Hard
**Pattern:** Bitmask BFS ((node, mask)) | **Companies:** Google · Amazon · Meta

**Hint:** Visited belongs in the state: BFS over (node, mask), starting from every node at once.

---

### H8 · Non-negative Integers without Consecutive Ones

**🔗 [LC 600 — Non-negative Integers without Consecutive Ones](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/)** · Hard
**Pattern:** Digit DP (binary) | **Companies:** Google · Amazon

**Hint:** Walk the bits from the top with a tight flag and the previous bit; memoise only the loose states.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — interval DP on n elements with a pivot

// Snippet 2 — tree DP returning two values per node

// Snippet 3 — rerooting tree DP

// Snippet 4 — bitmask DP over subsets of n items

// Snippet 5 — enumerating all submasks of every mask

// Snippet 6 — digit DP over a number with d digits
```

**Complexity Answers:**

1. **O(n³)**.
2. **O(n)**.
3. **O(n)** — two passes.
4. **O(n · 2ⁿ)**.
5. **O(3ⁿ)**.
6. **O(d · 10 · states)**.

---

## 🔍 Self-Assessment — True / False

1. Interval DP fills shorter ranges before longer ones. → **True**
2. Bitmask DP is practical for n around 50. → **False** — 2⁵⁰ is far too large; about 20 is the limit
3. Rerooting computes an answer for every node as root in O(n). → **True**
4. In Burst Balloons, choosing the first balloon to burst gives independent subproblems. → **False** — choose the last one
5. Digit DP counts numbers in a range without listing them. → **True**
6. A game DP can store one value: the current player's advantage. → **True**

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Length loop:** Why must the interval template loop over length rather than over i and j directly? What breaks otherwise?
2. **Think last:** Burst Balloons picks the balloon that bursts last. What exactly goes wrong if you pick the first one instead?
3. **Advantage:** What does dp`[i][j]` mean in a game DP, and why is one number enough for two players?
4. **Two values:** In a tree DP, why does a node often return two numbers instead of just its best answer?
5. **Rerooting:** Derive `answer[v] = answer[u] − size[v] + (n − size[v])` from scratch, in words.
6. **The n ≤ 20 wall:** Why does bitmask DP stop being viable somewhere around n = 20? Do the arithmetic.
7. **Free position:** In Beautiful Arrangement the position is never stored in the state. Why is that safe?
8. **Tight states:** Why does digit DP memoise only the states where `tight` is false?
9. **Two bounds:** How do you count values in [A, B] when your function only counts from 0, and what is the edge case?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Binary Tree Tilt](https://leetcode.com/problems/binary-tree-tilt/), [Univalued Binary Tree](https://leetcode.com/problems/univalued-binary-tree/), [Minimum Cost to Cut a Stick](https://leetcode.com/problems/minimum-cost-to-cut-a-stick/), [Minimum Cost to Merge Stones](https://leetcode.com/problems/minimum-cost-to-merge-stones/)                   |
| **Google**    | [Rotated Digits](https://leetcode.com/problems/rotated-digits/), [Non-negative Integers without Consecutive Ones](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/), [Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/), [Strange Printer](https://leetcode.com/problems/strange-printer/) |
| **Meta**      | [Binary Tree Coloring Game](https://leetcode.com/problems/binary-tree-coloring-game/), [Stone Game](https://leetcode.com/problems/stone-game/), [Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/), [Burst Balloons](https://leetcode.com/problems/burst-balloons/)                                     |
| **Adobe**     | [Predict the Winner](https://leetcode.com/problems/predict-the-winner/)                                                                                                                                                                                                                                                                                      |
| **Bloomberg** | [Can I Win](https://leetcode.com/problems/can-i-win/)                                                                                                                                                                                                                                                                                                        |

---

## ✅ Completion Checklist

- [ ] All 5 Easy problems solved
- [ ] All 12 Medium problems solved
- [ ] All 8 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 9 conceptual questions answered out loud
- [ ] I can write the interval template from memory, including the length loop
- [ ] I can explain the think-last reversal and when it is unnecessary
- [ ] I can write a game DP as an advantage with the sign flip
- [ ] I can reroot a tree DP and derive the patch formula
- [ ] I know the bitmask operations, including submask enumeration
- [ ] I can write the digit DP skeleton with tight and started flags
- [ ] I can read a constraint like n ≤ 15 and name the intended technique

---

**← [Lecture 34 · Dynamic Programming III — Knapsack & Subsets](../Lecture34/Assignment.md)** &nbsp;·&nbsp; **[Lecture 36 · Tries (Prefix Trees)](../Lecture36/Assignment.md) →**
