# 🌳 Assignment 15 — Trees (Binary Trees & BST)

> **Lecture:** Topic 15 — Trees (Binary Trees & BST)
> **Phase:** 2 — Core Data Structures · **Topic:** 15 of 30
> **Estimated Time:** 10 Days · **Total Problems:** 45 (12 Easy · 23 Medium · 10 Hard)
> **Goal:** Master the 6 tree patterns — DFS, BFS Level-Order, Height Recursion, Global via Local, BST Property, and LCA — and apply them to the most frequently asked FAANG tree problems.

---

## 🗺️ Pattern Recognition — Read Before Starting

| Signal Phrase in Problem                                | Pattern           | Core Technique                    |
| ------------------------------------------------------- | ----------------- | --------------------------------- |
| "traversal", "visit in order", "print nodes"            | DFS (Pre/In/Post) | Recursion / Explicit Stack        |
| "level by level", "row", "width", "right view"          | BFS Level-Order   | Queue + `int size` snapshot       |
| "depth", "height", "balanced", "diameter"               | Height Recursion  | Return int, combine with max      |
| "max path", "longest path", "diameter through any node" | Global via Local  | Global var + DFS returning height |
| "BST", "search", "kth smallest", "validate"             | BST Property      | Range check or inorder            |
| "common ancestor", "LCA", "split point"                 | LCA               | Return node, split detection      |

---

## 🟢 Easy Tier — Build Fluency (12 Problems)

---

### E1 · Maximum Depth of Binary Tree

**🔗 [LC 104](https://leetcode.com/problems/maximum-depth-of-binary-tree/)**
**Pattern:** Height Recursion | **Companies:** Amazon, Google, Microsoft

**Hint:** `maxDepth(node) = 1 + max(maxDepth(left), maxDepth(right))`. Base case: null returns 0. 3 lines total.

---

### E2 · Invert Binary Tree

**🔗 [LC 226](https://leetcode.com/problems/invert-binary-tree/)**
**Pattern:** DFS Preorder | **Companies:** Amazon, Apple, Google

**Hint:** Swap left and right children, then recursively invert both subtrees. Or use BFS — swap children as you dequeue each node.

---

### E3 · Symmetric Tree

**🔗 [LC 101](https://leetcode.com/problems/symmetric-tree/)**
**Pattern:** DFS (Two-pointer on tree) | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** A tree is symmetric if its left subtree is a mirror of its right subtree. Helper: `isMirror(left, right)` — check that `left.val == right.val` and `isMirror(left.left, right.right)` and `isMirror(left.right, right.left)`.

---

### E4 · Path Sum I

**🔗 [LC 112](https://leetcode.com/problems/path-sum/)**
**Pattern:** DFS Preorder | **Companies:** Amazon, Microsoft

**Hint:** Subtract the current node's value from `targetSum` as you go down. At a leaf, check if `targetSum - leaf.val == 0`.

---

### E5 · Merge Two Binary Trees

**🔗 [LC 617](https://leetcode.com/problems/merge-two-binary-trees/)**
**Pattern:** DFS Preorder | **Companies:** Amazon, Google

**Hint:** If either node is null, return the other. Otherwise create a new node with `t1.val + t2.val` and recurse on both children.

---

### E6 · Search in a Binary Search Tree

**🔗 [LC 700](https://leetcode.com/problems/search-in-a-binary-search-tree/)**
**Pattern:** BST Property | **Companies:** Amazon, Google

**Hint:** If `node.val == val` return node. If `val < node.val` search left, else search right. Base case: null → return null.

---

### E7 · Range Sum of BST

**🔗 [LC 938](https://leetcode.com/problems/range-sum-of-bst/)**
**Pattern:** BST Property | **Companies:** Amazon, Facebook

**Hint:** Use BST pruning — if node.val < low go right only; if node.val > high go left only; else add node.val and recurse both.

---

### E8 · Minimum Depth of Binary Tree

**🔗 [LC 111](https://leetcode.com/problems/minimum-depth-of-binary-tree/)**
**Pattern:** Height Recursion / BFS | **Companies:** Amazon, Google

**Hint:** BFS is simpler — the first leaf you reach is the minimum depth. For DFS: be careful — if a node has only one child, you can't use `min(leftDepth, rightDepth)` directly (null child would incorrectly give 0).

---

### E9 · Same Tree

**🔗 [LC 100](https://leetcode.com/problems/same-tree/)**
**Pattern:** DFS | **Companies:** Bloomberg, Amazon

**Hint:** Two trees are the same if their roots have the same value AND their left subtrees are the same AND their right subtrees are the same. Base cases: both null → true, one null → false.

---

### E10 · Count Nodes in Complete Binary Tree

**🔗 [LC 222](https://leetcode.com/problems/count-complete-tree-nodes/)**
**Pattern:** Height Recursion | **Companies:** Amazon, Google

**Hint (O(log²n)):** Measure leftmost depth and rightmost depth. If equal → perfect subtree: return `2^h - 1`. Else recurse on both halves. This beats O(n).

---

### E11 · Find Mode in Binary Search Tree

**🔗 [LC 501](https://leetcode.com/problems/find-mode-in-binary-search-tree/)**
**Pattern:** BST Inorder | **Companies:** Microsoft

**Hint:** Inorder traversal gives sorted order. Track current number and its count; update modes when count hits max.

---

### E12 · Convert Sorted Array to BST

**🔗 [LC 108](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)**
**Pattern:** DFS + Divide & Conquer | **Companies:** Amazon, Google

**Hint:** The middle element of the sorted array is the root (ensures balanced). Recurse on left half for left subtree, right half for right subtree.

---

## 🟡 Medium Tier — Core Interview Patterns (23 Problems)

---

### M1 · Binary Tree Level Order Traversal

**🔗 [LC 102](https://leetcode.com/problems/binary-tree-level-order-traversal/)**
**Pattern:** BFS Level-Order | **Companies:** Amazon, Microsoft, Google, Bloomberg

**Hint:** Queue + `int size = q.size()` before inner loop. Process exactly `size` nodes per level, add children for next level.

---

### M2 · Binary Tree Zigzag Level Order Traversal

**🔗 [LC 103](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)**
**Pattern:** BFS Level-Order | **Companies:** Amazon, Google, Bloomberg

**Hint:** Same as M1 but track a boolean `leftToRight`. When false, add level elements using `addFirst()` on a `LinkedList` to reverse direction.

---

### M3 · Binary Tree Right Side View

**🔗 [LC 199](https://leetcode.com/problems/binary-tree-right-side-view/)**
**Pattern:** BFS Level-Order | **Companies:** Facebook, Amazon, Google

**Hint:** BFS — the last node dequeued in each level is the rightmost visible node. Add it to results.

---

### M4 · Average of Levels in Binary Tree

**🔗 [LC 637](https://leetcode.com/problems/average-of-levels-in-binary-tree/)**
**Pattern:** BFS Level-Order | **Companies:** Google, Amazon

**Hint:** Same BFS template. Sum all values in a level and divide by `size`.

---

### M5 · Diameter of Binary Tree

**🔗 [LC 543](https://leetcode.com/problems/diameter-of-binary-tree/)**
**Pattern:** Global via Local | **Companies:** Google, Facebook, Amazon

**Hint:** DFS returns height. At each node update global `max = max(max, leftH + rightH)`. The diameter passes through this node.

---

### M6 · Balanced Binary Tree

**🔗 [LC 110](https://leetcode.com/problems/balanced-binary-tree/)**
**Pattern:** Height Recursion | **Companies:** Amazon, Google, Bloomberg

**Hint:** Return -1 as a sentinel for "unbalanced". At each node, if `|leftH - rightH| > 1` return -1. Short-circuit if either child returns -1. O(n) single pass.

---

### M7 · Path Sum II

**🔗 [LC 113](https://leetcode.com/problems/path-sum-ii/)**
**Pattern:** DFS + Backtracking | **Companies:** Amazon, Google

**Hint:** DFS while maintaining a current path list. At a leaf, if remaining sum equals the leaf value, add a copy of the path to results. Backtrack by removing the last element after returning.

---

### M8 · Path Sum III

**🔗 [LC 437](https://leetcode.com/problems/path-sum-iii/)**
**Pattern:** DFS + Prefix Sum HashMap | **Companies:** Amazon, Google, Facebook

**Hint:** The classic "subarray sum = k" approach applied to trees. Store prefix sums in a map. At each node, check if `prefixSum - targetSum` exists in map. Backtrack by decrementing the map count on return.

---

### M9 · Binary Tree Maximum Path Sum ⭐ (Pattern 4 Boss)

**🔗 [LC 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/)**
**Pattern:** Global via Local | **Companies:** Google, Amazon, Facebook, Microsoft

**Hint:** DFS returns max gain from one branch (can't use both branches — that would "fork" the path). Global variable tracks the best path through any node = `leftGain + node.val + rightGain`. Gains can be negative, so use `max(0, childGain)` to drop bad branches.

---

### M10 · Validate Binary Search Tree

**🔗 [LC 98](https://leetcode.com/problems/validate-binary-search-tree/)**
**Pattern:** BST Property | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** Pass a valid range `[min, max]` down. Use `Long` to avoid edge cases with `Integer.MIN_VALUE`/`MAX_VALUE`. Going left: `max` becomes `node.val`. Going right: `min` becomes `node.val`.

---

### M11 · Kth Smallest Element in a BST

**🔗 [LC 230](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)**
**Pattern:** BST Inorder | **Companies:** Amazon, Google, Bloomberg, Uber

**Hint:** Inorder of a BST = sorted order. Count nodes during inorder. When count hits k, record the answer. Use a class-level counter and result variable.

---

### M12 · Insert into a Binary Search Tree

**🔗 [LC 701](https://leetcode.com/problems/insert-into-a-binary-search-tree/)**
**Pattern:** BST Property | **Companies:** Amazon, Google

**Hint:** Navigate left/right like BST search. When you hit null, create a new node there. Recursively: if val < node.val, `node.left = insert(node.left, val)`, else `node.right = insert(node.right, val)`.

---

### M13 · Delete Node in a BST

**🔗 [LC 450](https://leetcode.com/problems/delete-node-in-a-bst/)**
**Pattern:** BST Property | **Companies:** Amazon, Microsoft

**Hint:** 3 cases: (1) node is a leaf → return null. (2) node has one child → return that child. (3) node has two children → find inorder successor (smallest in right subtree), copy its value, delete the successor.

---

### M14 · Lowest Common Ancestor of a Binary Tree

**🔗 [LC 236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)**
**Pattern:** LCA | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Return node when null/p/q found. If both left and right return non-null → split here → current is LCA. Else bubble up whichever side is non-null.

---

### M15 · Lowest Common Ancestor of a BST

**🔗 [LC 235](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)**
**Pattern:** BST Property + LCA | **Companies:** Amazon, Google, Facebook

**Hint:** Simpler than LC 236. If both p and q are less than node.val → go left. If both greater → go right. Otherwise → this IS the LCA (split point).

---

### M16 · Construct Binary Tree from Preorder and Inorder

**🔗 [LC 105](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)**
**Pattern:** DFS + Divide & Conquer | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Preorder[0] is always the root. Find that value in inorder — everything to its left is the left subtree, everything to its right is the right subtree. Use a HashMap for O(1) inorder index lookup. Recurse with adjusted index bounds.

---

### M17 · Construct Binary Tree from Inorder and Postorder

**🔗 [LC 106](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)**
**Pattern:** DFS + Divide & Conquer | **Companies:** Amazon, Microsoft

**Hint:** Same as M16 but root is at `postorder[last]`. Process postorder from right to left. Build right subtree before left subtree.

---

### M18 · Binary Tree Level Order Traversal II

**🔗 [LC 107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)**
**Pattern:** BFS Level-Order | **Companies:** Amazon

**Hint:** Same BFS as M1. At the end, call `Collections.reverse(result)` or add each level to the front of a LinkedList.

---

### M19 · Populating Next Right Pointers

**🔗 [LC 116](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)**
**Pattern:** BFS or O(1) space DFS | **Companies:** Amazon, Google, Microsoft

**Hint (O(1) space):** Since it's a perfect BT, use the already-connected next pointers to traverse the next level without a queue. At each node: `node.left.next = node.right` and if `node.next` exists, `node.right.next = node.next.left`.

---

### M20 · Binary Search Tree Iterator

**🔗 [LC 173](https://leetcode.com/problems/binary-search-tree-iterator/)**
**Pattern:** BST Inorder (Lazy) | **Companies:** Amazon, Microsoft, Facebook

**Hint:** Use an explicit stack for iterative inorder. `next()` = pop from stack, push right child and its leftmost chain. `hasNext()` = check stack is not empty. Amortized O(1) per call, O(h) space.

---

### M21 · Flatten Binary Tree to Linked List

**🔗 [LC 114](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)**
**Pattern:** DFS Postorder | **Companies:** Amazon, Microsoft, Google

**Hint (O(1) space — Morris-like):** Process right → right subtree, then left subtree. For each node: find the rightmost node of the left subtree, attach right subtree to it, move left subtree to right, set left to null.

---

### M22 · House Robber III

**🔗 [LC 337](https://leetcode.com/problems/house-robber-iii/)**
**Pattern:** DFS + DP on Tree | **Companies:** Amazon, Google, Airbnb

**Hint:** Each node returns a pair `[rob, skip]` = max money if we rob this node vs skip it. `rob = node.val + left.skip + right.skip`. `skip = max(left.rob, left.skip) + max(right.rob, right.skip)`.

---

### M23 · All Nodes Distance K in Binary Tree

**🔗 [LC 863](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/)**
**Pattern:** DFS + Parent Pointers (BFS) | **Companies:** Google, Amazon, Uber

**Hint:** First DFS to build a parent pointer map (treating the tree as undirected graph). Then BFS from the target node to distance K, using the parent map to traverse upward too.

---

## 🔴 Hard Tier — FAANG Mastery (10 Problems)

---

### H1 · Binary Tree Maximum Path Sum

**🔗 [LC 124](https://leetcode.com/problems/binary-tree-maximum-path-sum/)**
**Pattern:** Global via Local | **Companies:** Google, Amazon, Facebook, Microsoft

**Hint:** DFS returns max one-side gain from node = `max(0, leftGain, rightGain) + node.val`. Update global answer with `leftGain + node.val + rightGain` at each node.

**Why Hard?** Negative values, paths don't have to pass through root, combining two directions breaks the "return to parent" contract.

---

### H2 · Serialize and Deserialize Binary Tree

**🔗 [LC 297](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)**
**Pattern:** DFS Preorder | **Companies:** Google, Amazon, Facebook, Microsoft, Uber

**Hint:** Serialize using preorder DFS — write node value, then left, then right; write "null" for null nodes. Deserialize using a queue of tokens — poll the front, create a node, recurse for left and right.

**Why Hard?** Requires careful null handling and understanding of how preorder uniquely reconstructs a tree.

---

### H3 · Binary Tree Cameras

**🔗 [LC 968](https://leetcode.com/problems/binary-tree-cameras/)**
**Pattern:** DFS Postorder + Greedy | **Companies:** Google, Amazon

**Hint:** Each node returns a state: 0 = not covered, 1 = has camera, 2 = covered (no camera). Greedy: place cameras as deep as possible (bottom-up). If a child is not covered, the parent must have a camera.

---

### H4 · Recover Binary Search Tree

**🔗 [LC 99](https://leetcode.com/problems/recover-binary-search-tree/)**
**Pattern:** BST Inorder | **Companies:** Amazon, Google, Microsoft

**Hint:** Inorder should be sorted. Find the two nodes that are out of order (first: where `prev.val > curr.val` first time; second: where it happens second time). Swap their values. O(1) space using Morris traversal.

---

### H5 · Count of Smaller Numbers After Self

**🔗 [LC 315](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)**
**Pattern:** BST + Rank | **Companies:** Google, Amazon, Uber

**Hint:** Process array from right to left, inserting into a BST. Each node tracks count of nodes in its left subtree. Use this to compute rank (count of smaller elements).

---

### H6 · Vertical Order Traversal of a Binary Tree

**🔗 [LC 987](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)**
**Pattern:** DFS + Coordinate mapping | **Companies:** Facebook, Amazon, Google

**Hint:** Assign each node `(col, row)` coordinates. Root is `(0, 0)`. Left child: `(col-1, row+1)`, right child: `(col+1, row+1)`. Collect all `(col, row, val)` tuples, sort by col → row → val, then group by col.

---

### H7 · Binary Tree Right Side View (Hard follow-up: left AND right AND top AND bottom)

**🔗 [LC 199](https://leetcode.com/problems/binary-tree-right-side-view/)** + boundary view
**Pattern:** BFS + DFS boundary | **Companies:** Amazon, Adobe, Samsung

**Hint for full boundary view:** Collect left boundary (excluding leaves) top-down, then all leaves left-to-right, then right boundary (excluding leaves) bottom-up.

---

### H8 · Largest BST Subtree

**🔗 [LC 333](https://leetcode.com/problems/largest-bst-subtree/)**
**Pattern:** DFS Postorder + Range check | **Companies:** Amazon, Google

**Hint:** Each node returns `(size, min, max)` for its subtree. A subtree is a valid BST if `node.val > left.max && node.val < right.min`. Propagate the largest valid BST size seen globally.

---

### H9 · Morris Inorder Traversal

**🔗 [LC 94 — O(1) space variant](https://leetcode.com/problems/binary-tree-inorder-traversal/)**
**Pattern:** Morris Traversal | **Companies:** Google, Apple

**Hint:** Threaded binary tree. For each node: if no left child → process and go right. Else find inorder predecessor (rightmost node of left subtree). If predecessor's right is null → thread it to current, go left. If already threaded → unthread, process current, go right.

**Why Hard?** O(1) space with no stack or recursion. Temporarily modifies tree structure.

---

### H10 · Maximum Width of Binary Tree

**🔗 [LC 662](https://leetcode.com/problems/maximum-width-of-binary-tree/)**
**Pattern:** BFS Level-Order + Index arithmetic | **Companies:** Amazon, Google, Facebook

**Hint:** Assign index to each node (root=1, left child=2i, right child=2i+1). Width of a level = last index - first index + 1. Use BFS; store `(node, index)` pairs. Normalize indices per level to prevent overflow.

---

## 🧠 Conceptual Check — Answer Without Looking at Code

1. **Traversal choice:** If a problem says "return the sum of all root-to-leaf paths where each path is treated as a number," which traversal order do you use and why?

2. **Stack overflow risk:** A BST is built by inserting a sorted array in order. What is the height of this BST? Why is this dangerous for recursive solutions?

3. **Inorder + BST:** Why does inorder traversal of a BST produce a sorted sequence? Prove it using the BST property definition.

4. **Global via Local:** In the Diameter problem, the DFS function returns `height`, NOT `diameter`. Why? If it returned diameter instead, what would break?

5. **LCA correctness:** In the `lowestCommonAncestor` function, what does it mean when `left != null && right != null`? Why does this guarantee the current node is the LCA?

6. **Morris Traversal:** What is the space complexity of Morris inorder traversal and why? What does it do to the tree structure during traversal?

---

## 🏢 Company Focus Table

| Company       | Must-Know Problems                                                                                                           |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | Diameter (LC 543), Max Path Sum (LC 124), Serialize/Deserialize (LC 297), Vertical Order (LC 987), All Nodes Dist K (LC 863) |
| **Amazon**    | Level Order (LC 102), Validate BST (LC 98), Construct BT (LC 105), LCA (LC 236), Path Sum III (LC 437)                       |
| **Meta**      | Right Side View (LC 199), LCA (LC 236), Zigzag (LC 103), BST Iterator (LC 173)                                               |
| **Microsoft** | Symmetric Tree (LC 101), Flatten BT (LC 114), Delete in BST (LC 450), Validate BST (LC 98)                                   |
| **Apple**     | Morris Traversal (LC 94 O(1)), Count Complete Nodes (LC 222)                                                                 |

---

## ✅ Completion Checklist

- [ ] Completed all 12 Easy problems
- [ ] Completed all 23 Medium problems
- [ ] Attempted all 10 Hard problems
- [ ] Can answer all 6 Conceptual Check questions verbally
- [ ] Can write all 3 DFS traversals recursively and inorder iteratively from memory
- [ ] Can write the BFS level-order template from memory
- [ ] Can implement LCA for both BT (LC 236) and BST (LC 235) from memory
- [ ] Can identify the correct pattern within 30 seconds for any tree problem

---

**← Topic 14: Matrix Problems** &nbsp;&nbsp;|&nbsp;&nbsp; **Topic 16: Heaps & Priority Queues →**
