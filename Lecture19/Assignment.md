# 🌲 Assignment 19 — Trees II — BST, LCA & Construction

> **Lecture:** 19 of 45 — Trees II — BST, LCA & Construction
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 4 days · **Total Problems:** 16 (4 Easy · 10 Medium · 2 Hard)
> **Goal:** Use the BST ordering property deliberately, find lowest common ancestors in one pass, and rebuild a tree from its traversals.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                | Pattern                 | Move                                                               |
| ------------------------------------ | ----------------------- | ------------------------------------------------------------------ |
| Tree is a BST — exploit the ordering | Range check or in-order | Pass (min, max) down, or check the in-order sequence is increasing |
| k-th smallest / largest in a BST     | In-order with a counter | Stop the walk the moment the counter hits k                        |
| Find where two nodes diverge         | LCA                     | Return the node up the recursion; the first split is the answer    |
| LCA in a BST specifically            | Ordering shortcut       | Descend while both targets are on the same side                    |
| Rebuild a tree from traversals       | Divide and conquer      | Pre/post gives the root, in-order splits the subtrees              |
| O(1) extra space traversal           | Morris                  | Thread a temporary link to the in-order predecessor                |

---

## 🟢 Easy Tier (4 Problems)

_The BST property at its simplest — searching, summing a range, and building a balanced tree from sorted input._

### E1 · Search in a Binary Search Tree

**🔗 [LC 700 — Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/)** · Easy
**Pattern:** BST Property | **Companies:** Amazon, Google

**Hint:** If `node.val == val` return node. If `val < node.val` search left, else search right. Base case: null → return null.

---

### E2 · Range Sum of BST

**🔗 [LC 938 — Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)** · Easy
**Pattern:** BST Property | **Companies:** Amazon, Facebook

**Hint:** Use BST pruning — if node.val < low go right only; if node.val > high go left only; else add node.val and recurse both.

---

### E3 · Find Mode in Binary Search Tree

**🔗 [LC 501 — Find Mode in Binary Search Tree](https://leetcode.com/problems/find-mode-in-binary-search-tree/)** · Easy
**Pattern:** BST Inorder | **Companies:** Microsoft

**Hint:** Inorder traversal gives sorted order. Track current number and its count; update modes when count hits max.

---

### E4 · Convert Sorted Array to Binary Search Tree

**🔗 [LC 108 — Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)** · Easy
**Pattern:** DFS + Divide & Conquer | **Companies:** Amazon, Google

**Hint:** The middle element of the sorted array is the root (ensures balanced). Recurse on left half for left subtree, right half for right subtree.

---

## 🟡 Medium Tier (10 Problems)

_The working set: validating, ordering, inserting, deleting, finding ancestors, and rebuilding from traversals._

### M1 · Validate Binary Search Tree

**🔗 [LC 98 — Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)** · Medium
**Pattern:** BST Property | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** Pass a valid range `[min, max]` down. Use `Long` to avoid edge cases with `Integer.MIN_VALUE`/`MAX_VALUE`. Going left: `max` becomes `node.val`. Going right: `min` becomes `node.val`.

---

### M2 · Kth Smallest Element in a BST

**🔗 [LC 230 — Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)** · Medium
**Pattern:** BST Inorder | **Companies:** Amazon, Google, Bloomberg, Uber

**Hint:** Inorder of a BST = sorted order. Count nodes during inorder. When count hits k, record the answer. Use a class-level counter and result variable.

---

### M3 · Insert into a Binary Search Tree

**🔗 [LC 701 — Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/)** · Medium
**Pattern:** BST Property | **Companies:** Amazon, Google

**Hint:** Navigate left/right like BST search. When you hit null, create a new node there. Recursively: if val < node.val, `node.left = insert(node.left, val)`, else `node.right = insert(node.right, val)`.

---

### M4 · Delete Node in a BST

**🔗 [LC 450 — Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/)** · Medium
**Pattern:** BST Property | **Companies:** Amazon, Microsoft

**Hint:** 3 cases: (1) node is a leaf → return null. (2) node has one child → return that child. (3) node has two children → find inorder successor (smallest in right subtree), copy its value, delete the successor.

---

### M5 · Lowest Common Ancestor of a Binary Tree

**🔗 [LC 236 — Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)** · Medium
**Pattern:** LCA | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Return node when null/p/q found. If both left and right return non-null → split here → current is LCA. Else bubble up whichever side is non-null.

---

### M6 · Lowest Common Ancestor of a Binary Search Tree

**🔗 [LC 235 — Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)** · Medium
**Pattern:** BST Property + LCA | **Companies:** Amazon, Google, Facebook

**Hint:** Simpler than LC 236. If both p and q are less than node.val → go left. If both greater → go right. Otherwise → this IS the LCA (split point).

---

### M7 · Construct Binary Tree from Preorder and Inorder Traversal

**🔗 [LC 105 — Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)** · Medium
**Pattern:** DFS + Divide & Conquer | **Companies:** Amazon, Google, Facebook, Microsoft

**Hint:** Preorder[0] is always the root. Find that value in inorder — everything to its left is the left subtree, everything to its right is the right subtree. Use a HashMap for O(1) inorder index lookup. Recurse with adjusted index bounds.

---

### M8 · Construct Binary Tree from Inorder and Postorder Traversal

**🔗 [LC 106 — Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)** · Medium
**Pattern:** DFS + Divide & Conquer | **Companies:** Amazon, Microsoft

**Hint:** Same as M16 but root is at `postorder[last]`. Process postorder from right to left. Build right subtree before left subtree.

---

### M9 · Binary Search Tree Iterator

**🔗 [LC 173 — Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/)** · Medium
**Pattern:** BST Inorder (Lazy) | **Companies:** Amazon, Microsoft, Facebook

**Hint:** Use an explicit stack for iterative inorder. `next()` = pop from stack, push right child and its leftmost chain. `hasNext()` = check stack is not empty. Amortised O(1) per call, O(h) space.

---

### M10 · Recover Binary Search Tree

**🔗 [LC 99 — Recover Binary Search Tree](https://leetcode.com/problems/recover-binary-search-tree/)** · Medium
**Pattern:** BST Inorder | **Companies:** Amazon, Google, Microsoft

**Hint:** Inorder should be sorted. Find the two nodes that are out of order (first: where `prev.val > curr.val` first time; second: where it happens second time). Swap their values. O(1) space using Morris traversal.

---

## 🔴 Hard Tier (2 Problems)

_Two problems that combine the ordering property with a post-order walk that must return several values at once._

### H1 · Serialize and Deserialize Binary Tree

**🔗 [LC 297 — Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)** · Hard
**Pattern:** DFS Preorder | **Companies:** Google, Amazon, Facebook, Microsoft, Uber

**Hint:** Serialize using preorder DFS — write node value, then left, then right; write "null" for null nodes. Deserialize using a queue of tokens — poll the front, create a node, recurse for left and right.

**Why Hard?** Requires careful null handling and understanding of how preorder uniquely reconstructs a tree.

---

### H2 · Maximum Sum BST in Binary Tree

**🔗 [LC 1373 — Maximum Sum BST in Binary Tree](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/)** · Hard
**Pattern:** Postorder DFS — Return a Tuple | **Companies:** Amazon, Google

**Hint:** Each node returns `(isBST, min, max, sum)` for its subtree. The subtree is a BST if both children are BSTs and `left.max < node.val < right.min`. If it is, update the global best with its sum. Empty children return `(true, +∞, -∞, 0)`.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — search a BST of height h

// Snippet 2 — search a BST built by inserting 1, 2, 3, …, n in order

// Snippet 3 — validate a BST by passing (min, max) bounds down

// Snippet 4 — LCA in a general binary tree

// Snippet 5 — LCA in a BST

// Snippet 6 — build a tree from pre-order + in-order, searching the in-order array for each root
```

**Complexity Answers:**

1. **O(h)** time.
2. **O(n)** — the tree is a straight line, so h = n.
3. **O(n)** time, O(h) space.
4. **O(n)** time.
5. **O(h)** time — walk down one path.
6. **O(n²)** — each root search is O(n); an index map makes it O(n).

---

## 🔍 Self-Assessment — True / False

1. BST search is always O(log n). → **False** — O(h); a skewed BST has h = n
2. An in-order walk of a valid BST gives sorted order. → **True**
3. Checking each node against only its parent is enough to validate a BST. → **False** — a deeper node can violate an ancestor's bound
4. Pre-order plus in-order uniquely determine a binary tree with distinct values. → **True**
5. Pre-order plus post-order uniquely determine any binary tree. → **False** — a single child could be left or right
6. Morris traversal uses O(1) extra space. → **True** — it borrows null pointers temporarily

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The real property:** Why is "left child < parent < right child" not enough to validate a BST? Give a three-node counterexample.
2. **Range check:** What min and max do you pass into the left and right child, and what are the values at the root?
3. **In-order proof:** Explain why an in-order walk of a valid BST is sorted, from the property alone.
4. **LCA in one pass:** In the general-tree LCA, what does a non-null return from both children mean?
5. **BST shortcut:** Why is LCA on a BST O(height) with no recursion into both sides?
6. **Which two traversals:** Pre+in and post+in both rebuild a tree. Why does pre+post fail?
7. **Morris cost:** What does Morris traversal do to the tree while it runs, and what is the price of O(1) space?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Maximum Sum BST in Binary Tree](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/), [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/), [Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/), [Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/) |
| **Google**    | [Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/), [Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/), [Maximum Sum BST in Binary Tree](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/), [Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/)             |
| **Microsoft** | [Find Mode in Binary Search Tree](https://leetcode.com/problems/find-mode-in-binary-search-tree/), [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/), [Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/), [Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/)         |
| **Facebook**  | [Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/), [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/), [Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator/), [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)                             |
| **Bloomberg** | [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/), [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)                                                                                                                                                                                                                                                   |

---

## ✅ Completion Checklist

- [ ] All 4 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 2 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 7 conceptual questions answered out loud
- [ ] I can validate a BST with a range check and explain why the local check fails
- [ ] I can write LCA for a general tree and for a BST, and say why they differ
- [ ] I can rebuild a tree from pre-order + in-order without slicing arrays

---

**← [Lecture 18 · Trees I — Traversals & Recursion](../Lecture18/Assignment.md)** &nbsp;·&nbsp; **[Lecture 20 · Heaps & Priority Queues](../Lecture20/Assignment.md) →**
