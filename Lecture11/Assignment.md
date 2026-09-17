# 🔗 Assignment 11 — Linked Lists

> **Lecture:** 11 of 38 — Linked Lists
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 6 days · **Total Problems:** 28 (10 Easy · 13 Medium · 5 Hard)
> **Goal:** Master pointer rerouting, Fast & Slow pointer paradigms, and complex cache design invariants (LRU/LFU).

---

## 📊 Topic Overview

Linked Lists are the foundational bridge between linear data structures (Arrays) and hierarchical ones (Trees). Mastering them requires a mental shift from "index-based access" to **"reference-based navigation"**.

- **Primary Patterns**: Fast & Slow Pointers, In-place Reversal, Sentinel Head (Dummy), Interweaving, Frequency Mapping.
- **Key Focus**: Maintaining pointer integrity during complex re-linking.

---

## 🟢 Easy Tier (Foundation & Floyd's)

_Focus on traversing, basic manipulation, and the "Tortoise and Hare" strategy._

1. **[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (LC 206)** — The fundamental iterative vs recursive question. `[Pattern: Reversal]` `[Companies: Amazon, Microsoft, Meta, Apple]`
2. **[Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) (LC 876)** — Standard Fast & Slow pointer application. `[Pattern: Fast & Slow]` `[Companies: Amazon, Google, Microsoft]`
3. **[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) (LC 141)** — Detecting cycles using meeting points. `[Pattern: Floyd's Detection]` `[Companies: Amazon, Microsoft, Meta, Bloomberg]`
4. **[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) (LC 21)** — Use a Dummy Head to simplify edge cases. `[Pattern: Dummy Head]` `[Companies: Amazon, Apple, Microsoft]`
5. **[Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/) (LC 237)** — The "O(1) Copy Value" interview trick. `[Pattern: Value Override]` `[Companies: Amazon, Apple, Microsoft]`
6. **[Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/) (LC 203)** — Clean deletion with Dummy Head. `[LC Easy]` `[Companies: Amazon, Google, Adobe]`
7. **[Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/) (LC 234)** — Combine Middle + Reverse + Compare. `[Pattern: Composition]` `[Companies: Amazon, Meta, Microsoft]`
8. **[Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/) (LC 160)** — Two pointers or length difference method. `[Companies: Amazon, Microsoft, Meta, Bloomberg]`
9. **[Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/) (LC 83)** — Standard traversal and pointer skipping. `[LC Easy]` `[Companies: Amazon, Microsoft, Adobe]`
10. **[Convert Binary Number in a Linked List to Integer](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/) (LC 1290)** — Horner's method for binary. `[LC Easy]` `[Companies: Amazon, Adobe]`

---

## 🟡 Medium Tier (Advanced Rerouting)

_Focus on multi-step logic and complex pointer state management._

1. **[Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) (LC 19)** — Use two pointers with a gap of N. `[Pattern: Gap Pointers]` `[Companies: Amazon, Meta, Google, Microsoft]`
2. **[Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) (LC 142)** — Find the start of the cycle using the $2x$ vs $1x$ math. `[Pattern: Floyd's]` `[Companies: Amazon, Microsoft, Meta]`
3. **[Reorder List](https://leetcode.com/problems/reorder-list/) (LC 143)** — Middle + Reverse + Alternating Merge. `[Companies: Amazon, Meta, Microsoft]`
4. **[Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/) (LC 328)** — Group nodes by index parity in $O(N)$ time. `[Pattern: Multi-Pointer]` `[Companies: Amazon, Microsoft, Bloomberg]`
5. **[Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) (LC 2)** — The classic "Full Adder" logic on lists. `[Companies: Amazon, Microsoft, Meta, Adobe]`
6. **[Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/) (LC 445)** — Handling reverse arithmetic using stacks. `[LC Medium]` `[Companies: Amazon, Microsoft, Meta]`
7. **[Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) (LC 138)** — Iterative $O(1)$ space "interweaving" strategy. `[Companies: Amazon, Meta, Microsoft, Bloomberg]`
8. **[Sort List](https://leetcode.com/problems/sort-list/) (LC 148)** — Implementing Merge Sort with $O(N \log N)$ stability. `[Pattern: Divide & Conquer]` `[Companies: Amazon, Google, Meta, Microsoft]`
9. **[Rotate List](https://leetcode.com/problems/rotate-list/) (LC 61)** — Shifting nodes based on $(k \pmod L)$ index. `[LC Medium]` `[Companies: Amazon, Microsoft, Bloomberg]`
10. **[Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/) (LC 1721)** — Efficient $O(N)$ node swapping. `[LC Medium]` `[Companies: Amazon, Google]`
11. **[Split Linked List in Parts](https://leetcode.com/problems/split-linked-list-in-parts/) (LC 725)** — Sub-list management and sizing. `[LC Medium]` `[Companies: Amazon, Google]`
12. **[Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/) (LC 430)** — Pointer manipulation on steroids. `[LC Medium]` `[Companies: Amazon, Meta, Bloomberg]`
13. **[Partition List](https://leetcode.com/problems/partition-list/) (LC 86)** — Using two separate dummy heads for sorting. `[Pattern: Two-Queue]` `[Companies: Amazon, Meta, Microsoft]`

---

## 🔴 Challenge Zone (Mastery & Design)

_Focus on cache design invariants and k-sized re-grouping._

1. **[Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) (LC 25)** — The ultimate test of pointer control and recursion. `[Pattern: Reversal]` `[Companies: Amazon, Meta, Microsoft, Google]`
2. **[Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) (LC 23)** — Use a Min-Heap/PriorityQueue for $O(N \log K)$. `[Pattern: Heap]` `[Companies: Amazon, Google, Meta, Uber]`
3. **[Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/) (LC 92)** — Reversing a bounded sub-segment in one pass. `[LC Medium/Hard]` `[Companies: Amazon, Meta, Microsoft]`
4. **[LRU Cache](https://leetcode.com/problems/lru-cache/) (LC 146)** — HashMap + Doubly Linked List for $O(1)$ access. `[Pattern: DLL]` `[Companies: Amazon, Microsoft, Meta, Google]`
5. **[LFU Cache](https://leetcode.com/problems/lfu-cache/) (LC 460)** — Least Frequently Used using multiple lists. `[Pattern: Freq Maps]` `[Companies: Google, Amazon, Uber]`

---

## 📊 Conceptual Check

1. **Space Trade-off**: Why is iterative reversal preferred over recursive in production?
2. **Infinite Loops**: What safety check prevents a cycle in a merged list?
3. **Dummy Head**: When is using a sentinel node actually detrimental?
4. **Complexity Check**: Why is random access $O(N)$ for LL but $O(1)$ for Arrays?

---

**Next Topic**: Topic 12 — Stacks & Queues →
