# 🗂️ Assignment 11 — Linked Lists

> **Lecture:** 14 of 45 — Linked Lists
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 6 days · **Total Problems:** 28 (9 Easy · 16 Medium · 3 Hard)
> **Goal:** Master pointer rerouting, Fast & Slow pointer paradigms, and complex cache design invariants (LRU/LFU).

---

## 🗺️ Pattern Recognition — Read Before Starting

Linked Lists are the foundational bridge between linear data structures (Arrays) and hierarchical ones (Trees). Mastering them requires a mental shift from "index-based access" to **"reference-based navigation"**.

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem             | Pattern                      | Move                                        |
| --------------------------------- | ---------------------------- | ------------------------------------------- |
| "middle", "cycle", "nth from end" | Fast & Slow Pointers         | one moves 2 steps, one moves 1              |
| "reverse" (all or part)           | In-place Reversal            | `prev`, `curr`, `next` — three pointers     |
| "head might change"               | Dummy Head                   | start from a sentinel node                  |
| "merge / sort lists"              | Merge Two Lists              | splice nodes, don't copy values             |
| "random pointer", "deep copy"     | Interweaving                 | insert copies between originals, then split |
| "O(1) get and put"                | HashMap + Doubly Linked List | map to nodes, move nodes on access          |

---

## 🟢 Easy Tier (9 Problems)

_Focus on traversing, basic manipulation, and the "Tortoise and Hare" strategy._

### E1 · Reverse Linked List

**🔗 [LC 206 — Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)** · Easy
**Pattern:** Reversal | **Companies:** Amazon, Microsoft, Meta, Apple

**Hint:** Iteratively keep `prev = null`, `curr = head`: save `next`, point `curr.next` at `prev`, then advance both. Recursively: reverse the rest, then set `head.next.next = head` and `head.next = null`.

---

### E2 · Middle of the Linked List

**🔗 [LC 876 — Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)** · Easy
**Pattern:** Fast & Slow | **Companies:** Amazon, Google, Microsoft

**Hint:** Fast moves two steps, slow moves one. When fast reaches the end, slow is at the middle — for even length, at the second middle node, which is what LeetCode wants.

---

### E3 · Linked List Cycle

**🔗 [LC 141 — Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)** · Easy
**Pattern:** Floyd's Detection | **Companies:** Amazon, Microsoft, Meta, Bloomberg

**Hint:** Floyd's algorithm: slow moves one step, fast moves two. If there's a cycle, fast eventually lands on slow; if fast hits `null`, there's none. O(1) space.

---

### E4 · Merge Two Sorted Lists

**🔗 [LC 21 — Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)** · Easy
**Pattern:** Dummy Head | **Companies:** Amazon, Apple, Microsoft

**Hint:** Start from a dummy node and a `tail` pointer. Repeatedly attach the smaller head and advance that list. At the end attach whichever list is left.

---

### E5 · Remove Linked List Elements

**🔗 [LC 203 — Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)** · Easy
**Pattern:** Dummy Head | **Companies:** Amazon, Google, Adobe

**Hint:** Put a dummy before `head` so deleting the first node isn't special. With `curr` at the dummy: if `curr.next.val == val`, unlink it (don't advance); otherwise advance.

---

### E6 · Palindrome Linked List

**🔗 [LC 234 — Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)** · Easy
**Pattern:** Composition | **Companies:** Amazon, Meta, Microsoft

**Hint:** Find the middle with fast and slow pointers, reverse the second half, and compare the two halves node by node. Restore the list afterwards if the caller needs it intact.

---

### E7 · Intersection of Two Linked Lists

**🔗 [LC 160 — Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)** · Easy
**Pattern:** Two Pointers (Switch Heads) | **Companies:** Amazon, Microsoft, Meta, Bloomberg

**Hint:** Walk pointers `a` and `b`; when one reaches the end, jump it to the other list's head. Both travel `lenA + lenB`, so they meet at the intersection — or both reach `null` together.

---

### E8 · Remove Duplicates from Sorted List

**🔗 [LC 83 — Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)** · Easy
**Pattern:** Pointer Skipping | **Companies:** Amazon, Microsoft, Adobe

**Hint:** The list is sorted, so duplicates are adjacent. While `curr.next` has the same value, skip it (`curr.next = curr.next.next`); otherwise advance `curr`.

---

### E9 · Convert Binary Number in a Linked List to Integer

**🔗 [LC 1290 — Convert Binary Number in a Linked List to Integer](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)** · Easy
**Pattern:** Traversal + Accumulation | **Companies:** Amazon, Adobe

**Hint:** Horner's method: start at 0 and for each node do `value = value * 2 + node.val` (or `(value << 1) | node.val`).

---

## 🟡 Medium Tier (16 Problems)

_Focus on multi-step logic and complex pointer state management._

### M1 · Delete Node in a Linked List

**🔗 [LC 237 — Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)** · Medium
**Pattern:** Value Override | **Companies:** Amazon, Apple, Microsoft

**Hint:** You don't have access to the previous node, so copy the next node's value into this node, then skip the next node: `node.val = node.next.val; node.next = node.next.next`.

---

### M2 · Remove Nth Node From End of List

**🔗 [LC 19 — Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)** · Medium
**Pattern:** Gap Pointers | **Companies:** Amazon, Meta, Google, Microsoft

**Hint:** Dummy head, then move `fast` `n + 1` steps ahead of `slow`. Advance both until `fast` is null — `slow` now sits just before the node to delete. One pass.

---

### M3 · Linked List Cycle II

**🔗 [LC 142 — Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)** · Medium
**Pattern:** Floyd's | **Companies:** Amazon, Microsoft, Meta

**Hint:** After slow and fast meet inside the cycle, reset one pointer to `head` and move both one step at a time. They meet at the cycle's entry, because the distance from the head equals the distance from the meeting point (mod cycle length).

---

### M4 · Reorder List

**🔗 [LC 143 — Reorder List](https://leetcode.com/problems/reorder-list/)** · Medium
**Pattern:** Middle + Reverse + Merge | **Companies:** Amazon, Meta, Microsoft

**Hint:** Three steps: find the middle, reverse the second half, then weave the halves together, alternating one node from each. Cut the first half's tail to avoid a cycle.

---

### M5 · Odd Even Linked List

**🔗 [LC 328 — Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)** · Medium
**Pattern:** Multi-Pointer | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** Keep `odd = head`, `even = head.next`, and remember `evenHead`. Repeatedly link `odd.next = even.next` and `even.next = odd.next`, advancing each. Finally attach `evenHead` after the last odd node.

---

### M6 · Add Two Numbers

**🔗 [LC 2 — Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)** · Medium
**Pattern:** Carry Propagation | **Companies:** Amazon, Microsoft, Meta, Adobe

**Hint:** The digits are stored in reverse, so add from the heads with a carry: `sum = a + b + carry`, create a node with `sum % 10`, and set `carry = sum / 10`. Loop while either list or `carry` remains.

---

### M7 · Add Two Numbers II

**🔗 [LC 445 — Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/)** · Medium
**Pattern:** Reverse or Stack + Carry | **Companies:** Amazon, Microsoft, Meta

**Hint:** The digits are stored most-significant first. Push both lists onto stacks (or reverse them), then add from the top with a carry, inserting each new node at the front of the result.

---

### M8 · Copy List with Random Pointer

**🔗 [LC 138 — Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)** · Medium
**Pattern:** Interweaving | **Companies:** Amazon, Meta, Microsoft, Bloomberg

**Hint:** Three passes: insert a copy after each original node (`A → A' → B → B'`), set `copy.random = orig.random.next`, then separate the two lists. O(1) extra space. (A `HashMap<orig, copy>` version is simpler.)

---

### M9 · Sort List

**🔗 [LC 148 — Sort List](https://leetcode.com/problems/sort-list/)** · Medium
**Pattern:** Divide & Conquer | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Merge sort on a list: split at the middle with slow and fast pointers (cut `prev.next = null`), sort each half recursively, and merge two sorted lists. O(n log n) time, O(log n) stack.

---

### M10 · Rotate List

**🔗 [LC 61 — Rotate List](https://leetcode.com/problems/rotate-list/)** · Medium
**Pattern:** Close into a Ring, Then Cut | **Companies:** Amazon, Microsoft, Bloomberg

**Hint:** Find the length `L` and the tail, then reduce `k %= L`. Connect the tail to the head to form a ring, walk `L - k - 1` steps to the new tail, and cut there.

---

### M11 · Swapping Nodes in a Linked List

**🔗 [LC 1721 — Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)** · Medium
**Pattern:** Gap Pointers | **Companies:** Amazon, Google

**Hint:** Move `fast` `k - 1` steps to find the k-th node from the start, then move `slow` from the head and `fast` to the end together — `slow` lands on the k-th node from the end. Swap their values.

---

### M12 · Split Linked List in Parts

**🔗 [LC 725 — Split Linked List in Parts](https://leetcode.com/problems/split-linked-list-in-parts/)** · Medium
**Pattern:** Length + Split | **Companies:** Amazon, Google

**Hint:** Count the length `L`. Each part gets `L / k` nodes, and the first `L % k` parts get one extra. Walk and cut each part, filling `null` for any empty parts.

---

### M13 · Flatten a Multilevel Doubly Linked List

**🔗 [LC 430 — Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)** · Medium
**Pattern:** DFS on Child Pointers | **Companies:** Amazon, Meta, Bloomberg

**Hint:** DFS: whenever a node has a child, flatten the child, splice it between the node and its `next` (fixing both `prev` pointers), and set `child = null`. Keep track of the flattened child's tail so the splice is O(1).

---

### M14 · Partition List

**🔗 [LC 86 — Partition List](https://leetcode.com/problems/partition-list/)** · Medium
**Pattern:** Two-Queue | **Companies:** Amazon, Meta, Microsoft

**Hint:** Use two dummy lists: `less` for nodes `< x` and `greater` for the rest, appending in order. Join `less` to `greater.next` and terminate `greater`'s tail with `null`.

---

### M15 · Reverse Linked List II

**🔗 [LC 92 — Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)** · Medium
**Pattern:** In-place Reversal (Sub-list) | **Companies:** Amazon, Meta, Microsoft

**Hint:** Walk to the node before position `left`. Then do head insertion `right - left` times: take the node after the current segment start and move it to the front of the segment. One pass, O(1) space.

---

### M16 · Design Front Middle Back Queue

**🔗 [LC 1670 — Design Front Middle Back Queue](https://leetcode.com/problems/design-front-middle-back-queue/)** · Medium
**Pattern:** Doubly Linked List Design | **Companies:** Amazon, Google

**Hint:** Use a doubly linked list with sentinels plus a pointer to the middle node (or two deques kept balanced so `left.size()` is `right.size()` or one less). After every push or pop, rebalance the middle.

---

## 🔴 Hard Tier (3 Problems)

_Focus on cache design invariants and k-sized re-grouping._

### H1 · Reverse Nodes in k-Group

**🔗 [LC 25 — Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)** · Hard
**Pattern:** Reversal | **Companies:** Amazon, Meta, Microsoft, Google

**Hint:** Check that `k` nodes remain; if not, leave them as they are. Reverse exactly `k` nodes, connect the previous group's tail to the new head, and move on (iterative, O(1) space) — or recurse on the rest first.

---

### H2 · Design Skiplist

**🔗 [LC 1206 — Design Skiplist](https://leetcode.com/problems/design-skiplist/)** · Hard
**Pattern:** Linked Levels (Skiplist) | **Companies:** Google, Amazon

**Hint:** Each node has `next[]` pointers, one per level. To search, start at the top level and move right while the next value is smaller, then drop a level. Insert with a random height (coin flips), recording the predecessor at each level.

---

### H3 · LFU Cache

**🔗 [LC 460 — LFU Cache](https://leetcode.com/problems/lfu-cache/)** · Hard
**Pattern:** Freq Maps | **Companies:** Google, Amazon, Uber

**Hint:** Keep `key → node`, `freq → doubly linked list of nodes` and `minFreq`. On access, move the node from its frequency list to the next one (updating `minFreq` if its old list empties). To evict, remove the tail of the `minFreq` list. Everything is O(1).

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1
cur ← head
while cur ≠ null:
    cur ← cur.next

// Snippet 2 — get the i-th node for every i
for i from 0 to n - 1:
    node ← getNode(head, i)

// Snippet 3 — reverse iteratively
prev ← null;  cur ← head
while cur ≠ null:
    nxt ← cur.next;  cur.next ← prev
    prev ← cur;  cur ← nxt

// Snippet 4 — reverse recursively (what does it cost in SPACE?)

// Snippet 5 — slow and fast pointers to find the middle

// Snippet 6 — merge two sorted lists of lengths n and m
```

**Complexity Answers:**

1. **O(n)** time, O(1) space.
2. **O(n²)** — each getNode walks from the head.
3. **O(n)** time, **O(1)** space.
4. **O(n)** time and **O(n)** stack space — one frame per node.
5. **O(n)** time, O(1) space — fast covers the list once.
6. **O(n + m)** time, O(1) extra space.

---

## 🔍 Self-Assessment — True / False

1. Accessing the k-th node of a linked list is O(1). → **False** — you must walk k steps: O(k)
2. Inserting at the head of a singly linked list is O(1). → **True** — point the new node at the old head
3. Floyd's fast-and-slow pointers detect a cycle using O(1) extra space. → **True** — only two pointers
4. A dummy head node is only needed when the list is empty. → **False** — it removes the special case whenever the real head might change
5. Reversing a list recursively uses O(1) extra space. → **False** — the call stack holds n frames
6. Deleting a node you have a reference to is always O(1) in a singly linked list. → **False** — you need its predecessor, unless you copy the next node's value into it

---

## 🧠 Conceptual Check

1. **Space Trade-off**: Why is iterative reversal preferred over recursive in production?
2. **Infinite Loops**: What safety check prevents a cycle in a merged list?
3. **Dummy Head**: When is using a sentinel node actually detrimental?
4. **Complexity Check**: Why is random access O(n) for a linked list but O(1) for an array?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                 |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Convert Binary Number in a Linked List to Integer](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/), [Design Front Middle Back Queue](https://leetcode.com/problems/design-front-middle-back-queue/), [Design Skiplist](https://leetcode.com/problems/design-skiplist/), [LFU Cache](https://leetcode.com/problems/lfu-cache/)                       |
| **Microsoft** | [Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/), [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/), [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/), [Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)                 |
| **Meta**      | [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/), [Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/), [Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/), [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)                                             |
| **Google**    | [Split Linked List in Parts](https://leetcode.com/problems/split-linked-list-in-parts/), [Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/), [Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/), [Design Front Middle Back Queue](https://leetcode.com/problems/design-front-middle-back-queue/) |
| **Bloomberg** | [Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/), [Rotate List](https://leetcode.com/problems/rotate-list/), [Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/), [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)                               |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 4 conceptual questions answered out loud
- [ ] I can reverse a list iteratively and recursively without drawing it
- [ ] I can find a cycle's entry point and explain why Floyd's algorithm works

---

**← [Lecture 13 · Searching Algorithms](../Lecture13/Assignment.md)** &nbsp;·&nbsp; **[Lecture 15 · Stacks & Queues](../Lecture15/Assignment.md) →**
