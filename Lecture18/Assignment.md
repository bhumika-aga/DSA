# 🌳 Assignment 18 — Trees I — Traversals & Recursion

> **Lecture:** 18 of 45 — Trees I — Traversals & Recursion
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 6 days · **Total Problems:** 29 (11 Easy · 14 Medium · 4 Hard)
> **Goal:** Walk any binary tree three ways, level by level, and answer questions about heights and paths without looking up the template.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                        | Pattern            | Move                                            |
| -------------------------------------------- | ------------------ | ----------------------------------------------- |
| Question asks about depth, height or balance | Height recursion   | Return an int from a post-order walk            |
| Answer is about the whole tree, not one node | Global via local   | Keep a field, update it inside the DFS          |
| Process one level at a time                  | BFS level-order    | Queue, and loop exactly queue.size times        |
| Visit every node in a set order              | DFS traversal      | Pre / in / post — only the print position moves |
| Compare two trees, or a tree with its mirror | Paired DFS         | Recurse on two nodes at once                    |
| Collect the nodes along a root-to-leaf path  | DFS + backtracking | Append, recurse, then remove                    |

---

## 🟢 Easy Tier (11 Problems)

_Pure recursion practice. Every one of these is four lines once you trust the two subtrees — write the base case first, every time._

### E1 · Maximum Depth of Binary Tree

**🔗 [LC 104 — Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)** · Easy
**Pattern:** Height Recursion | **Companies:** Amazon, Google, Microsoft

**Hint:** `maxDepth(node) = 1 + max(maxDepth(left), maxDepth(right))`. Base case: null returns 0. 3 lines total.

---

### E2 · Invert Binary Tree

**🔗 [LC 226 — Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)** · Easy
**Pattern:** DFS Preorder | **Companies:** Amazon, Apple, Google

**Hint:** Swap left and right children, then recursively invert both subtrees. Or use BFS — swap children as you dequeue each node.

---

### E3 · Symmetric Tree

**🔗 [LC 101 — Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)** · Easy
**Pattern:** DFS (Two-pointer on tree) | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** A tree is symmetric if its left subtree is a mirror of its right subtree. Helper: `isMirror(left, right)` — check that `left.val == right.val` and `isMirror(left.left, right.right)` and `isMirror(left.right, right.left)`.

---

### E4 · Path Sum

**🔗 [LC 112 — Path Sum](https://leetcode.com/problems/path-sum/)** · Easy
**Pattern:** DFS Preorder | **Companies:** Amazon, Microsoft

**Hint:** Subtract the current node's value from `targetSum` as you go down. At a leaf, check if `targetSum - leaf.val == 0`.

---

### E5 · Merge Two Binary Trees

**🔗 [LC 617 — Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)** · Easy
**Pattern:** DFS Preorder | **Companies:** Amazon, Google

**Hint:** If either node is null, return the other. Otherwise create a new node with `t1.val + t2.val` and recurse on both children.

---

### E6 · Minimum Depth of Binary Tree

**🔗 [LC 111 — Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)** · Easy
**Pattern:** Height Recursion / BFS | **Companies:** Amazon, Google

**Hint:** BFS is simpler — the first leaf you reach is the minimum depth. For DFS: be careful — if a node has only one child, you can't use `min(leftDepth, rightDepth)` directly (null child would incorrectly give 0).

---

### E7 · Same Tree

**🔗 [LC 100 — Same Tree](https://leetcode.com/problems/same-tree/)** · Easy
**Pattern:** DFS | **Companies:** Bloomberg, Amazon

**Hint:** Two trees are the same if their roots have the same value AND their left subtrees are the same AND their right subtrees are the same. Base cases: both null → true, one null → false.

---

### E8 · Average of Levels in Binary Tree

**🔗 [LC 637 — Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/)** · Easy
**Pattern:** BFS Level-Order | **Companies:** Google, Amazon

**Hint:** Same BFS template. Sum all values in a level and divide by `size`.

---

### E9 · Diameter of Binary Tree

**🔗 [LC 543 — Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)** · Easy
**Pattern:** Global via Local | **Companies:** Google, Meta, Amazon

**Hint:** DFS returns height. At each node update global `max = max(max, leftH + rightH)`. The diameter passes through this node.

---

### E10 · Balanced Binary Tree

**🔗 [LC 110 — Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)** · Easy
**Pattern:** Height Recursion | **Companies:** Amazon, Google, Bloomberg

**Hint:** Return -1 as a sentinel for "unbalanced". At each node, if `|leftH - rightH| > 1` return -1. Short-circuit if either child returns -1. O(n) single pass.

---

### E11 · Binary Tree Inorder Traversal

**🔗 [LC 94 — Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)** · Easy
**Pattern:** Morris Traversal | **Companies:** Google, Apple

**Hint:** Threaded binary tree. For each node: if no left child → process and go right. Else find inorder predecessor (rightmost node of left subtree). If predecessor's right is null → thread it to current, go left. If already threaded → unthread, process current, go right.

**Why Hard?** O(1) space with no stack or recursion. Temporarily modifies tree structure.

---

## 🟡 Medium Tier (14 Problems)

_The same patterns with a twist: an extra piece of state, a different traversal order, or a level index to track._

### M1 · Count Complete Tree Nodes

**🔗 [LC 222 — Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/)** · Medium
**Pattern:** Height Recursion | **Companies:** Amazon, Google

**Hint:** _Target: O(log²n)._ Measure leftmost depth and rightmost depth. If equal → perfect subtree: return `2^h - 1`. Else recurse on both halves. This beats O(n).

---

### M2 · Binary Tree Level Order Traversal

**🔗 [LC 102 — Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)** · Medium
**Pattern:** BFS Level-Order | **Companies:** Amazon, Microsoft, Google, Bloomberg

**Hint:** Queue + `int size = q.size()` before inner loop. Process exactly `size` nodes per level, add children for next level.

---

### M3 · Binary Tree Zigzag Level Order Traversal

**🔗 [LC 103 — Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)** · Medium
**Pattern:** BFS Level-Order | **Companies:** Amazon, Google, Bloomberg

**Hint:** Same as M1 but track a boolean `leftToRight`. When false, add level elements using `addFirst()` on a `LinkedList` to reverse direction.

---

### M4 · Binary Tree Right Side View

**🔗 [LC 199 — Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)** · Medium
**Pattern:** BFS Level-Order | **Companies:** Meta, Amazon, Google

**Hint:** BFS — the last node dequeued in each level is the rightmost visible node. Add it to results.

---

### M5 · Path Sum II

**🔗 [LC 113 — Path Sum II](https://leetcode.com/problems/path-sum-ii/)** · Medium
**Pattern:** DFS + Backtracking | **Companies:** Amazon, Google

**Hint:** DFS while maintaining a current path list. At a leaf, if remaining sum equals the leaf value, add a copy of the path to results. Backtrack by removing the last element after returning.

---

### M6 · Path Sum III

**🔗 [LC 437 — Path Sum III](https://leetcode.com/problems/path-sum-iii/)** · Medium
**Pattern:** DFS + Prefix Sum HashMap | **Companies:** Amazon, Google, Meta

**Hint:** The classic "subarray sum = k" approach applied to trees. Store prefix sums in a map. At each node, check if `prefixSum - targetSum` exists in map. Backtrack by decrementing the map count on return.

---

### M7 · Maximum Difference Between Node and Ancestor

**🔗 [LC 1026 — Maximum Difference Between Node and Ancestor](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/)** · Medium
**Pattern:** Global via Local | **Companies:** Amazon, Google, Meta

**Hint:** Carry the minimum and maximum values seen on the path from the root **down** into each call. At every node the best answer through it is `max(|val - pathMin|, |val - pathMax|)` — update a global answer there. No return values needed: the state flows top-down. (The bottom-up version of this pattern is H1 · Binary Tree Maximum Path Sum.)

---

### M8 · Binary Tree Level Order Traversal II

**🔗 [LC 107 — Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)** · Medium
**Pattern:** BFS Level-Order | **Companies:** Amazon

**Hint:** Same BFS as M1. At the end, call `Collections.reverse(result)` or add each level to the front of a LinkedList.

---

### M9 · Populating Next Right Pointers in Each Node

**🔗 [LC 116 — Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)** · Medium
**Pattern:** BFS or O(1) space DFS | **Companies:** Amazon, Google, Microsoft

**Hint:** _Target: O(1) space._ Since it's a perfect BT, use the already-connected next pointers to traverse the next level without a queue. At each node: `node.left.next = node.right` and if `node.next` exists, `node.right.next = node.next.left`.

---

### M10 · Flatten Binary Tree to Linked List

**🔗 [LC 114 — Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)** · Medium
**Pattern:** DFS Postorder | **Companies:** Amazon, Microsoft, Google

**Hint:** _Target: O(1) space — Morris-like._ Process right → right subtree, then left subtree. For each node: find the rightmost node of the left subtree, attach right subtree to it, move left subtree to right, set left to null.

---

### M11 · House Robber III

**🔗 [LC 337 — House Robber III](https://leetcode.com/problems/house-robber-iii/)** · Medium
**Pattern:** DFS + DP on Tree | **Companies:** Amazon, Google, Airbnb

**Hint:** Each node returns a pair `[rob, skip]` = max money if we rob this node vs skip it. `rob = node.val + left.skip + right.skip`. `skip = max(left.rob, left.skip) + max(right.rob, right.skip)`.

---

### M12 · All Nodes Distance K in Binary Tree

**🔗 [LC 863 — All Nodes Distance K in Binary Tree](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/)** · Medium
**Pattern:** DFS + Parent Pointers (BFS) | **Companies:** Google, Amazon, Uber

**Hint:** First DFS to build a parent pointer map (treating the tree as undirected graph). Then BFS from the target node to distance K, using the parent map to traverse upward too.

---

### M13 · Delete Nodes And Return Forest

**🔗 [LC 1110 — Delete Nodes And Return Forest](https://leetcode.com/problems/delete-nodes-and-return-forest/)** · Medium
**Pattern:** Postorder DFS with Deletion | **Companies:** Google, Amazon, Meta

**Hint:** Put the values to delete in a set. The DFS returns the node, or `null` if it's deleted, so the parent can unlink it. A node becomes a new root when it's kept and its parent was deleted (or it's the root). Process children before deciding (postorder).

---

### M14 · Maximum Width of Binary Tree

**🔗 [LC 662 — Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/)** · Medium
**Pattern:** BFS Level-Order + Index arithmetic | **Companies:** Amazon, Google, Meta

**Hint:** Assign index to each node (root=1, left child=2i, right child=2i+1). Width of a level = last index - first index + 1. Use BFS; store `(node, index)` pairs. Normalise indices per level to prevent overflow.

---

## 🔴 Hard Tier (4 Problems)

_Problems where the return value and the global answer are two different things. Say out loud what each one is before you type._

### H1 · Binary Tree Maximum Path Sum

**🔗 [LC 124 — Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)** · Hard
**Pattern:** Global via Local | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** DFS returns max one-side gain from node = `max(0, leftGain, rightGain) + node.val`. Update global answer with `leftGain + node.val + rightGain` at each node.

**Why Hard?** Negative values, paths don't have to pass through root, combining two directions breaks the "return to parent" contract.

---

### H2 · Binary Tree Cameras

**🔗 [LC 968 — Binary Tree Cameras](https://leetcode.com/problems/binary-tree-cameras/)** · Hard
**Pattern:** DFS Postorder + Greedy | **Companies:** Google, Amazon

**Hint:** Each node returns a state: 0 = not covered, 1 = has camera, 2 = covered (no camera). Greedy: place cameras as deep as possible (bottom-up). If a child is not covered, the parent must have a camera.

---

### H3 · Height of Binary Tree After Subtree Removal Queries

**🔗 [LC 2458 — Height of Binary Tree After Subtree Removal Queries](https://leetcode.com/problems/height-of-binary-tree-after-subtree-removal-queries/)** · Hard
**Pattern:** Precomputed Heights + Euler Levels | **Companies:** Google, Amazon

**Hint:** Precompute each node's depth and subtree height. For each depth, keep the top two values of `depth + height` among its nodes. Removing a node leaves the best answer at its depth that doesn't use that node (the second best if it was the best). O(n + q).

---

### H4 · Vertical Order Traversal of a Binary Tree

**🔗 [LC 987 — Vertical Order Traversal of a Binary Tree](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)** · Hard
**Pattern:** DFS + Coordinate mapping | **Companies:** Meta, Amazon, Google

**Hint:** Assign each node `(col, row)` coordinates. Root is `(0, 0)`. Left child: `(col-1, row+1)`, right child: `(col+1, row+1)`. Collect all `(col, row, val)` tuples, sort by col → row → val, then group by col.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — any DFS traversal of a tree with n nodes

// Snippet 2
function height(node):
    if node = null: return 0
    return 1 + max(height(node.left), height(node.right))

// Snippet 3
function isBalanced(node):          // naive
    if node = null: return true
    if |height(node.left) - height(node.right)| > 1: return false
    return isBalanced(node.left) and isBalanced(node.right)

// Snippet 4 — level-order traversal with a queue

// Snippet 5 — recursive DFS on a completely skewed tree (a "linked list" tree)

// Snippet 6 — diameter, computed inside the height function
```

**Complexity Answers:**

1. **O(n)** time.
2. **O(n)** time, **O(h)** space.
3. **O(n²)** on a skewed tree, O(n log n) on a balanced one — height is recomputed at every node.
4. **O(n)** time, **O(w)** space where w is the widest level.
5. **O(n)** time and **O(n)** stack space.
6. **O(n)** — one post-order pass does both.

---

## 🔍 Self-Assessment — True / False

1. In-order, pre-order and post-order traversals are all O(n). → **True** — each visits every node once
2. Recursive DFS on a tree always uses O(log n) space. → **False** — O(h); a skewed tree has h = n
3. Level-order traversal uses a stack. → **False** — it uses a queue
4. A leaf is a node with no children. → **True**
5. The diameter of a tree always passes through the root. → **False** — it can lie entirely inside one subtree
6. Checking balance by calling height() at every node is O(n). → **False** — that is O(n log n) to O(n²); return height and balance together for O(n)

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The leap of faith:** State in one sentence what you assume `solve(node.left)` returns. Why is assuming it not circular?
2. **Traversal order:** Which of the three DFS orders gives sorted output on a BST, and why that one?
3. **Level size:** In BFS level-order, why must you capture `queue.size()` before the inner loop instead of checking it inside?
4. **Height vs depth:** Define both for the same node and say which one a post-order walk naturally returns.
5. **Global state:** Diameter is computed inside a function that returns height. Explain what each of the two values is for.
6. **Base case:** What should a tree recursion return for `null`, and what breaks if you return 0 for a maximum instead?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/), [Binary Tree Cameras](https://leetcode.com/problems/binary-tree-cameras/), [Height of Binary Tree After Subtree Removal Queries](https://leetcode.com/problems/height-of-binary-tree-after-subtree-removal-queries/), [All Nodes Distance K in Binary Tree](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/) |
| **Google**    | [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/), [Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/), [Delete Nodes And Return Forest](https://leetcode.com/problems/delete-nodes-and-return-forest/), [House Robber III](https://leetcode.com/problems/house-robber-iii/)                                                                                   |
| **Microsoft** | [Path Sum](https://leetcode.com/problems/path-sum/), [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/), [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/), [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)                                                         |
| **Meta**      | [Vertical Order Traversal of a Binary Tree](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/), [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/), [Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/), [Path Sum III](https://leetcode.com/problems/path-sum-iii/)                                                                   |
| **Bloomberg** | [Same Tree](https://leetcode.com/problems/same-tree/), [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/), [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/), [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)                                                                                                                     |

---

## ✅ Completion Checklist

- [ ] All 11 Easy problems solved
- [ ] All 14 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can write all three DFS traversals from memory
- [ ] I can write BFS level-order with a queue and explain the size loop
- [ ] I can tell a height-returning recursion from a global-state one on sight

---

**← [Lecture 17 · Matrix Problems](../Lecture17/Assignment.md)** &nbsp;·&nbsp; **[Lecture 19 · Trees II — BST, LCA & Construction](../Lecture19/Assignment.md) →**
