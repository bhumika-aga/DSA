# 🔗 Assignment 11 — Linked Lists

> **Lecture:** Topic 11 — Linked Lists Foundations
> **Topic Count:** 11 of 30 — Phase 2 Core Data Structures
> **Duration:** 6 Days
> **Core Problems:** 28 (10 Easy · 13 Medium · 5 Hard)
> **Goal:** Master pointer rerouting, Fast & Slow pointer paradigms, and complex cache design invariants (LRU/LFU).

---

## 📊 Topic Overview

Linked Lists are the foundational bridge between linear data structures (Arrays) and hierarchical ones (Trees). Mastering them requires a mental shift from "index-based access" to **"reference-based navigation"**.

- **Primary Patterns**: Fast & Slow Pointers, In-place Reversal, Sentinel Head (Dummy), Interweaving, Frequency Mapping.
- **Key Focus**: Maintaining pointer integrity during complex re-linking.

---

## 🟢 Easy Tier (Foundation & Floyd's)

_Focus on traversing, basic manipulation, and the "Tortoise and Hare" strategy._

1. **Reverse Linked List (LC 206)** — The fundamental iterative vs recursive question. `[Pattern: Reversal]`
2. **Middle of the Linked List (LC 876)** — Standard Fast & Slow pointer application. `[Pattern: Fast & Slow]`
3. **Linked List Cycle (LC 141)** — Detecting cycles using meeting points. `[Pattern: Floyd's Detection]`
4. **Merge Two Sorted Lists (LC 21)** — Use a Dummy Head to simplify edge cases. `[Pattern: Dummy Head]`
5. **Delete Node in a Linked List (LC 237)** — The "O(1) Copy Value" interview trick. `[Pattern: Value Override]`
6. **Remove Linked List Elements (LC 203)** — Clean deletion with Dummy Head. `[LC Easy]`
7. **Palindrome Linked List (LC 234)** — Combine Middle + Reverse + Compare. `[Pattern: Composition]`
8. **Intersection of Two Linked Lists (LC 160)** — Two pointers or length difference method. `[Company: Amazon]`
9. **Remove Duplicates from Sorted List (LC 83)** — Standard traversal and pointer skipping. `[LC Easy]`
10. **Convert Binary Number in a Linked List to Integer (LC 1290)** — Horner's method for binary. `[LC Easy]`

---

## 🟡 Medium Tier (Advanced Rerouting)

_Focus on multi-step logic and complex pointer state management._

1. **Remove Nth Node From End (LC 19)** — Use two pointers with a gap of N. `[Pattern: Gap Pointers]`
2. **Linked List Cycle II (LC 142)** — Find the start of the cycle using the $2x$ vs $1x$ math. `[Pattern: Floyd's]`
3. **Reorder List (LC 143)** — Middle + Reverse + Alternating Merge. `[Company: Microsoft]`
4. **Odd Even Linked List (LC 328)** — Group nodes by index parity in $O(N)$ time. `[Pattern: Multi-Pointer]`
5. **Add Two Numbers (LC 2)** — The classic "Full Adder" logic on lists. `[Company: Google]`
6. **Add Two Numbers II (LC 445)** — Handling reverse arithmetic using stacks. `[LC Medium]`
7. **Copy List with Random Pointer (LC 138)** — Iterative $O(1)$ space "interweaving" strategy. `[Company: Meta]`
8. **Sort List (LC 148)** — Implementing Merge Sort with $O(N \log N)$ stability. `[Pattern: Divide & Conquer]`
9. **Rotate List (LC 61)** — Shifting nodes based on $(k \pmod L)$ index. `[LC Medium]`
10. **Swapping Nodes in a Linked List (LC 1721)** — Efficient $O(N)$ node swapping. `[LC Medium]`
11. **Split Linked List in Parts (LC 725)** — Sub-list management and sizing. `[LC Medium]`
12. **Flatten a Multilevel Doubly Linked List (LC 430)** — Pointer manipulation on steroids. `[LC Medium]`
13. **Partition List (LC 86)** — Using two separate dummy heads for sorting. `[Pattern: Two-Queue]`

---

## 🔴 Challenge Zone (Mastery & Design)

_Focus on cache design invariants and k-sized re-grouping._

1. **Reverse Nodes in k-Group (LC 25)** — The ultimate test of pointer control and recursion. `[Pattern: Reversal]`
2. **Merge k Sorted Lists (LC 23)** — Use a Min-Heap/PriorityQueue for $O(N \log K)$. `[Pattern: Heap]`
3. **Reverse Linked List II (LC 92)** — Reversing a bounded sub-segment in one pass. `[LC Medium/Hard]`
4. **LRU Cache Implementation (LC 146)** — HashMap + Doubly Linked List for $O(1)$ access. `[Pattern: DLL]`
5. **LFU Cache Implementation (LC 460)** — Least Frequently Used using multiple lists. `[Pattern: Freq Maps]`

---

## 📊 Conceptual Check

1. **Space Trade-off**: Why is iterative reversal preferred over recursive in production?
2. **Infinite Loops**: What safety check prevents a cycle in a merged list?
3. **Dummy Head**: When is using a sentinel node actually detrimental?
4. **Complexity Check**: Why is random access $O(N)$ for LL but $O(1)$ for Arrays?

---

**Next Topic**: Topic 12 — Stacks & Queues →
