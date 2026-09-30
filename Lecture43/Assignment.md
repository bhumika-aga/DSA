# 🛠️ Assignment 43 — Design Data Structures

> **Lecture:** 43 of 45 — Design Data Structures
> **Phase:** 6 — Interview Mastery
> **Estimated Time:** 5 days · **Total Problems:** 20 (2 Easy · 13 Medium · 5 Hard)
> **Goal:** Given a list of operations and the speed each one must run at, pick one structure per job, link them together, and keep them consistent through every update.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Requirement in the Problem                              | Structure                    | Move                                                     |
| ------------------------------------------------------- | ---------------------------- | -------------------------------------------------------- |
| Look up by key in O(1)                                  | HashMap                      | Key → the object, or → its position in another structure |
| Remove an arbitrary item in O(1) and pick one at random | Array + HashMap of indices   | Swap the item with the last one, then pop                |
| Order by recency, move to front in O(1)                 | Doubly linked list + HashMap | The map finds the node, the list reorders it             |
| Always hand out the smallest / best available           | Heap (or TreeSet)            | Put items back when they are freed                       |
| Priorities change, but the heap cannot update in place  | Heap + lazy deletion         | Push the new version; skip stale ones when they surface  |
| "Value at time t", "value at snapshot s"                | History list per key         | Append (time, value); binary search the time             |
| Ordered queries — cheapest, nearest, next free          | TreeMap / TreeSet            | Keep one ordered set per group you query                 |
| Return items one by one                                 | Iterator                     | Do the work in hasNext, lazily                           |

---

## 🟢 Easy Tier (2 Problems)

_Almost every free Easy design problem appears in earlier lectures (5, 6, 15 and 20). These two warm up the core habit: store the data the way the queries need it._

### E1 · Design HashSet

**🔗 [LC 705 — Design HashSet](https://leetcode.com/problems/design-hashset/)** · Easy
**Pattern:** Buckets with chaining | **Companies:** Amazon, Microsoft

**Hint:** An array of about 1000 buckets, each a small list; key % 1000 picks the bucket. A boolean array of size 10⁶ + 1 also passes — say why a real hash set cannot do that.

---

### E2 · Design Neighbor Sum Service

**🔗 [LC 3242 — Design Neighbor Sum Service](https://leetcode.com/problems/design-neighbor-sum-service/)** · Easy
**Pattern:** Precompute positions | **Companies:** Amazon

**Hint:** Values are distinct, so store value → (row, column) once in the constructor. Each query then adds up four neighbours in O(1).

---

## 🟡 Medium Tier (13 Problems)

_The everyday interview design question: two or three structures kept in step._

### M1 · Snapshot Array

**🔗 [LC 1146 — Snapshot Array](https://leetcode.com/problems/snapshot-array/)** · Medium
**Pattern:** History list per index | **Companies:** Google, Amazon

**Hint:** Copying the array on every snap is O(n) each time. Store, for each index, a list of (snapId, value) changes; a get binary-searches for the last change at or before the snapshot.

---

### M2 · Seat Reservation Manager

**🔗 [LC 1845 — Seat Reservation Manager](https://leetcode.com/problems/seat-reservation-manager/)** · Medium
**Pattern:** Min-heap of free items | **Companies:** Amazon, Dropbox

**Hint:** Keep a min-heap of unreserved seats. Even better: a counter for "every seat above this is free" plus a heap only for seats that were given back.

---

### M3 · Iterator for Combination

**🔗 [LC 1286 — Iterator for Combination](https://leetcode.com/problems/iterator-for-combination/)** · Medium
**Pattern:** Iterator over combinations | **Companies:** Google, Amazon

**Hint:** Keep the current combination as indices. For next, find the rightmost index that can still move right, move it, and reset every index after it to follow it directly.

---

### M4 · Flatten Nested List Iterator

**🔗 [LC 341 — Flatten Nested List Iterator](https://leetcode.com/problems/flatten-nested-list-iterator/)** · Medium
**Pattern:** Lazy iterator with a stack | **Companies:** Meta, Google, LinkedIn

**Hint:** Keep a stack of items still to visit. hasNext unpacks lists on top of the stack until an integer is on top (or the stack is empty); next pops it.

---

### M5 · Design Memory Allocator

**🔗 [LC 2502 — Design Memory Allocator](https://leetcode.com/problems/design-memory-allocator/)** · Medium
**Pattern:** Array scan for a free run | **Companies:** Amazon

**Hint:** With n ≤ 1000, an array of owner ids is enough: allocate scans for the first run of `size` zeros; freeMemory clears every cell with that id and returns how many it cleared.

---

### M6 · Throne Inheritance

**🔗 [LC 1600 — Throne Inheritance](https://leetcode.com/problems/throne-inheritance/)** · Medium
**Pattern:** Tree + preorder traversal | **Companies:** Amazon, Google

**Hint:** The order of inheritance is a preorder traversal of the family tree with children in birth order. Deaths just go into a set that the traversal skips — never delete nodes.

---

### M7 · Design Bitset

**🔗 [LC 2166 — Design Bitset](https://leetcode.com/problems/design-bitset/)** · Medium
**Pattern:** Lazy flip flag | **Companies:** Google, Amazon

**Hint:** Flipping every bit would be O(n). Keep a `flipped` flag and a count of ones instead: a stored bit b means b XOR flipped, and after a flip the count becomes size − count.

---

### M8 · Design Task Manager

**🔗 [LC 3408 — Design Task Manager](https://leetcode.com/problems/design-task-manager/)** · Medium
**Pattern:** Heap + lazy deletion | **Companies:** Amazon, Google

**Hint:** A map taskId → (userId, priority) is the truth; a max-heap of (priority, taskId) is only a hint. Edits push a new entry; execTop pops until the top still matches the map.

---

### M9 · Find Consecutive Integers from a Data Stream

**🔗 [LC 2526 — Find Consecutive Integers from a Data Stream](https://leetcode.com/problems/find-consecutive-integers-from-a-data-stream/)** · Medium
**Pattern:** Keep only what the query needs | **Companies:** Amazon

**Hint:** You do not need the last k numbers — only how many of the most recent ones in a row equal `value`. Reset the counter on anything else.

---

### M10 · Design an ATM Machine

**🔗 [LC 2241 — Design an ATM Machine](https://leetcode.com/problems/design-an-atm-machine/)** · Medium
**Pattern:** Plan first, then commit | **Companies:** Amazon, Google

**Hint:** Take as many of the largest note as possible, then the next, and so on. Work on a copy of the counts; change the real counts only if the full amount can be paid.

---

### M11 · Product of the Last K Numbers

**🔗 [LC 1352 — Product of the Last K Numbers](https://leetcode.com/problems/product-of-the-last-k-numbers/)** · Medium
**Pattern:** Prefix products with a reset | **Companies:** Google, Amazon

**Hint:** Keep prefix products and divide two of them, like prefix sums. A zero ruins division, so on a zero clear the list: if k reaches back past the last zero, the answer is 0.

---

### M12 · Detect Squares

**🔗 [LC 2013 — Detect Squares](https://leetcode.com/problems/detect-squares/)** · Medium
**Pattern:** Count map + enumerate one corner | **Companies:** Google, Amazon

**Hint:** Store a count for every point. For a query point, each stored point on a diagonal from it fixes one square; multiply the counts of the other two corners.

---

### M13 · Design Spreadsheet

**🔗 [LC 3484 — Design Spreadsheet](https://leetcode.com/problems/design-spreadsheet/)** · Medium
**Pattern:** HashMap of cells | **Companies:** Amazon

**Hint:** Store only the cells that were set, in a map from "A1" to value; a missing cell is 0. To evaluate "=X+Y", split at "+" and read each side as a cell name or a number.

---

## 🔴 Hard Tier (5 Problems)

_Several structures that must all agree after every call — the part interviewers actually test._

### H1 · Insert Delete GetRandom O(1) - Duplicates allowed

**🔗 [LC 381 — Insert Delete GetRandom O(1) - Duplicates allowed](https://leetcode.com/problems/insert-delete-getrandom-o1-duplicates-allowed/)** · Hard
**Pattern:** Array + map of index sets | **Companies:** Amazon, Meta, LinkedIn

**Hint:** Map each value to the set of positions it occupies in an array. To remove, move the last element into the freed position and fix that element's index set before popping.

---

### H2 · Dinner Plate Stacks

**🔗 [LC 1172 — Dinner Plate Stacks](https://leetcode.com/problems/dinner-plate-stacks/)** · Hard
**Pattern:** List of stacks + heap of non-full ones | **Companies:** Amazon

**Hint:** Push needs the leftmost non-full stack: keep a min-heap of their indices and discard stale entries lazily. Pop needs the rightmost non-empty stack: trim empty stacks off the end first.

---

### H3 · Design Movie Rental System

**🔗 [LC 1912 — Design Movie Rental System](https://leetcode.com/problems/design-movie-rental-system/)** · Hard
**Pattern:** One ordered set per query | **Companies:** Amazon, Flipkart

**Hint:** A map (shop, movie) → price; per movie a TreeSet of unrented (price, shop); one TreeSet of rented (price, shop, movie). Rent and drop move an entry from one set to the other.

---

### H4 · Encrypt and Decrypt Strings

**🔗 [LC 2227 — Encrypt and Decrypt Strings](https://leetcode.com/problems/encrypt-and-decrypt-strings/)** · Hard
**Pattern:** Precompute in the constructor | **Companies:** Google, Amazon

**Hint:** Decryption is ambiguous, so do not decrypt at all. Encrypt every dictionary word once and count the results; decrypt(word) is simply that count.

---

### H5 · Design Graph With Shortest Path Calculator

**🔗 [LC 2642 — Design Graph With Shortest Path Calculator](https://leetcode.com/problems/design-graph-with-shortest-path-calculator/)** · Hard
**Pattern:** Adjacency list + Dijkstra per query | **Companies:** Google, Amazon

**Hint:** addEdge only appends to an adjacency list; shortestPath runs Dijkstra from Lecture 22. With few queries and a changing graph, recomputing on demand is the right trade.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — LRU get / put with a HashMap and a doubly linked list

// Snippet 2 — remove(val) in an array + HashMap-of-indices set (swap with last)

// Snippet 3 — Snapshot Array: get(index, snapId) with h changes stored for that index

// Snippet 4 — a heap with lazy deletion: total cost of u updates and q pops

// Snippet 5 — flip() on a bitset of size n, done naively, then with a flag

// Snippet 6 — Flatten Nested List Iterator: all hasNext / next calls over N integers and L lists
```

**Complexity Answers:**

1. **O(1)** each.
2. **O(1)** average.
3. **O(log h)** — binary search in that index's history.
4. **O((u + q) log(u + q))** — each pushed entry is popped at most once.
5. **O(n)** naively, **O(1)** with a flag.
6. **O(N + L)** in total — every item is pushed and popped once, so each call is O(1) amortised.

---

## 🔍 Self-Assessment — True / False

1. An LRU cache can use a singly linked list and still remove a node in O(1). → **False** — removing needs the previous node; that is why it is doubly linked
2. Removing from the middle of an array is O(1) if the order does not matter. → **True** — swap it with the last element and pop
3. Java's PriorityQueue can change an element's priority in O(log n). → **False** — remove(x) is O(n); push a new entry and skip stale ones instead
4. Lazy deletion can leave the heap larger than the number of live items. → **True** — stale entries wait until they reach the top
5. An iterator should do all of its work in the constructor. → **False** — lazy iterators do the work in hasNext / next, so unused parts cost nothing
6. When two structures describe the same data, every operation must update both. → **True** — that invariant is the whole design

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Method**: Walk through the five design steps for "a set with insert, remove and getRandom in O(1)".
2. **Linking**: In an LRU cache, what exactly does the HashMap store, and why is storing the value not enough?
3. **Swap-with-last**: Why must the moved element's index be updated _before_ the last slot is popped?
4. **Lazy deletion**: How do you recognise a stale heap entry? What is the worst case for memory?
5. **History**: Why is binary search valid on one index's change list in Snapshot Array?
6. **Follow-ups**: How would you make your LRU cache safe to use from several threads?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company      | Problems to Prioritise                                                                                                                                                                                                                                                                                                                               |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**   | [Design Movie Rental System](https://leetcode.com/problems/design-movie-rental-system/), [Dinner Plate Stacks](https://leetcode.com/problems/dinner-plate-stacks/), [Design Task Manager](https://leetcode.com/problems/design-task-manager/), [Design Memory Allocator](https://leetcode.com/problems/design-memory-allocator/)                     |
| **Google**   | [Snapshot Array](https://leetcode.com/problems/snapshot-array/), [Encrypt and Decrypt Strings](https://leetcode.com/problems/encrypt-and-decrypt-strings/), [Detect Squares](https://leetcode.com/problems/detect-squares/), [Design Graph With Shortest Path Calculator](https://leetcode.com/problems/design-graph-with-shortest-path-calculator/) |
| **Meta**     | [Flatten Nested List Iterator](https://leetcode.com/problems/flatten-nested-list-iterator/), [Insert Delete GetRandom O(1) - Duplicates allowed](https://leetcode.com/problems/insert-delete-getrandom-o1-duplicates-allowed/)                                                                                                                       |
| **LinkedIn** | [Insert Delete GetRandom O(1) - Duplicates allowed](https://leetcode.com/problems/insert-delete-getrandom-o1-duplicates-allowed/), [Flatten Nested List Iterator](https://leetcode.com/problems/flatten-nested-list-iterator/)                                                                                                                       |
| **Dropbox**  | [Seat Reservation Manager](https://leetcode.com/problems/seat-reservation-manager/)                                                                                                                                                                                                                                                                  |
| **Flipkart** | [Design Movie Rental System](https://leetcode.com/problems/design-movie-rental-system/)                                                                                                                                                                                                                                                              |

---

## ✅ Completion Checklist

- [ ] Both Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] For every design, I wrote down the invariant that links its structures before coding
- [ ] I re-solved LRU Cache (Lecture 16) and LFU Cache (Lecture 14) from memory

---

**← [Lecture 42 · Advanced Math & Game Theory](../Lecture42/Assignment.md)** &nbsp;·&nbsp; **[Lecture 44 · Company Pattern Drills](../Lecture44/Assignment.md) →**
