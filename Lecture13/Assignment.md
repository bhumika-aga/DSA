# 🗃️ Assignment 13 — HashMap & HashSet

> **Lecture:** 13 of 38 — HashMap & HashSet
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 4 days · **Total Problems:** 25 (7 Easy · 13 Medium · 5 Hard)
> **Goal:** Master the 5 core HashMap patterns: Frequency Map, Complement Lookup, Prefix Sum + Map, Group-by-Key, and Set Membership. Understand hashing internals, collision resolution, and cache design.

---

## 🗺️ Pattern Recognition — Read Before Starting

The HashMap is the single most-used data structure in FAANG coding interviews. It transforms O(n) linear scans into O(1) lookups. Understanding **when** to use it and **which pattern** to apply is the difference between a 30-minute solution and a 3-minute one.

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem             | Pattern              | Move                                        |
| --------------------------------- | -------------------- | ------------------------------------------- |
| "pair sums to target"             | Complement Lookup    | check `target - x` before storing `x`       |
| "count subarrays with sum k"      | Prefix Sum + HashMap | count earlier prefixes equal to `sum - k`   |
| "group items that are equivalent" | Canonical Key        | sorted string or count signature as the key |
| "longest consecutive run"         | HashSet Starts       | only expand from `x` when `x - 1` is absent |
| "one-to-one mapping"              | Bijection            | two maps, one per direction                 |
| "frequency of frequencies"        | Nested Counting      | count values, then count the counts         |

---

## 🟢 Easy Tier (7 Problems)

_Build confidence with the core HashMap API and the simplest pattern variants._

### E1 · Two Sum

**🔗 [LC 1 — Two Sum](https://leetcode.com/problems/two-sum/)** · Easy
**Pattern:** Complement Lookup | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Map each value to its index. For `nums[i]`, check whether `target - nums[i]` is already in the map before inserting `nums[i]` — that stops an element pairing with itself.

---

### E2 · Roman to Integer

**🔗 [LC 13 — Roman to Integer](https://leetcode.com/problems/roman-to-integer/)** · Easy
**Pattern:** Character Map | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Map the symbols to values. A symbol smaller than the one after it is subtracted (as in `IV`). Scanning right to left: add the value if it's `>=` the previous value, otherwise subtract.

---

### E3 · Check if the Sentence Is Pangram

**🔗 [LC 1832 — Check if the Sentence Is Pangram](https://leetcode.com/problems/check-if-the-sentence-is-pangram/)** · Easy
**Pattern:** HashSet / Boolean Array | **Companies:** Amazon, Google

**Hint:** Add each character to a `boolean[26]` (or a set) and check all 26 are seen. Early exit once the count reaches 26.

---

### E4 · Contains Duplicate

**🔗 [LC 217 — Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)** · Easy
**Pattern:** Set Membership | **Companies:** Amazon, Google, Apple

**Hint:** Add elements to a `HashSet`; `add` returns `false` on a duplicate, so return `true` then. O(n) time, O(n) space — compare with the sort-first O(1)-space version.

---

### E5 · Ransom Note

**🔗 [LC 383 — Ransom Note](https://leetcode.com/problems/ransom-note/)** · Easy
**Pattern:** Frequency Map | **Companies:** Amazon, Google, Apple

**Hint:** Count the magazine's letters in `int[26]`, then walk the ransom note decrementing counts; if any count goes below zero, return false.

---

### E6 · Word Pattern

**🔗 [LC 290 — Word Pattern](https://leetcode.com/problems/word-pattern/)** · Easy
**Pattern:** Bijective Map | **Companies:** Google, Amazon, Uber

**Hint:** Split `s` into words (lengths must match the pattern's). Keep `char → word` and `word → char` maps and fail on any conflicting mapping in either direction.

---

### E7 · Isomorphic Strings

**🔗 [LC 205 — Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)** · Easy
**Pattern:** Bijective Map | **Companies:** Google, Amazon, LinkedIn

**Hint:** Map `s[i] → t[i]` and `t[i] → s[i]`. If either map already holds a different partner, the strings aren't isomorphic. Arrays of size 256 work as maps.

---

## 🟡 Medium Tier (13 Problems)

_Focus on multi-step HashMap reasoning and patterns within patterns._

### M1 · Group Anagrams

**🔗 [LC 49 — Group Anagrams](https://leetcode.com/problems/group-anagrams/)** · Medium
**Pattern:** Group-by-Key | **Companies:** Amazon, Meta, Uber, Google

**Hint:** Group by a canonical key: the sorted characters, or a 26-count signature like `"#1#0#2…"`, which avoids the `k log k` sort. `computeIfAbsent(key, x -> new ArrayList<>()).add(s)`.

---

### M2 · Display Table of Food Orders in a Restaurant

**🔗 [LC 1418 — Display Table of Food Orders in a Restaurant](https://leetcode.com/problems/display-table-of-food-orders-in-a-restaurant/)** · Medium
**Pattern:** Nested HashMaps | **Companies:** JPMorgan, Amazon

**Hint:** Map `table → (food → count)` with a `TreeMap` for tables (numeric order) and a `TreeSet` for food names. Build the header from the food set, then one row per table.

---

### M3 · Subarray Sum Equals K

**🔗 [LC 560 — Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)** · Medium
**Pattern:** Prefix Sum + Map | **Companies:** Meta, Amazon, Google

**Hint:** Keep a map of prefix sum → how many times it has appeared, starting with `{0: 1}`. At each step add `map.getOrDefault(sum - k, 0)` to the answer, then record the current sum. Negative numbers are why a sliding window fails here.

---

### M4 · Longest Consecutive Sequence

**🔗 [LC 128 — Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)** · Medium
**Pattern:** Set Membership | **Companies:** Google, Amazon, Meta

**Hint:** Put everything in a `HashSet`. Only start counting from `x` when `x - 1` is not in the set (a sequence start), then walk `x + 1, x + 2, …`. Each number is visited a constant number of times: O(n).

---

### M5 · 4Sum II

**🔗 [LC 454 — 4Sum II](https://leetcode.com/problems/4sum-ii/)** · Medium
**Pattern:** Complement Lookup | **Companies:** Amazon, Google

**Hint:** Count all sums `a + b` from the first two arrays in a map. For every `c + d`, add `map.getOrDefault(-(c + d), 0)`. O(n²) instead of O(n⁴).

---

### M6 · Contiguous Array

**🔗 [LC 525 — Contiguous Array](https://leetcode.com/problems/contiguous-array/)** · Medium
**Pattern:** Prefix Sum + Map | **Companies:** Meta, Amazon, Google

**Hint:** Treat 0 as -1; you now need the longest subarray with sum 0. Store the first index at which each prefix sum appears (with `0 → -1`); when a sum repeats at `i`, the candidate length is `i - first[sum]`.

---

### M7 · Repeated DNA Sequences

**🔗 [LC 187 — Repeated DNA Sequences](https://leetcode.com/problems/repeated-dna-sequences/)** · Medium
**Pattern:** Rolling Hash / Set of Substrings | **Companies:** Amazon, Google, LinkedIn

**Hint:** Slide a length-10 window. Put each substring (or its 20-bit encoding — 2 bits per letter) in `seen`; if it was already there, add it to `result` (also a set, to avoid duplicates).

---

### M8 · Divide Players Into Teams of Equal Skill

**🔗 [LC 2491 — Divide Players Into Teams of Equal Skill](https://leetcode.com/problems/divide-players-into-teams-of-equal-skill/)** · Medium
**Pattern:** Counting + Complement | **Companies:** Amazon, Google

**Hint:** The pair total must be `2 × sum / n`. Count skills in a map, and for each skill `x` pair it with `target - x`; if the counts don't match, return -1. Chemistry adds up `x × (target - x)`.

---

### M9 · Max Number of K-Sum Pairs

**🔗 [LC 1679 — Max Number of K-Sum Pairs](https://leetcode.com/problems/max-number-of-k-sum-pairs/)** · Medium
**Pattern:** Complement Counting | **Companies:** Amazon, Google, Meta

**Hint:** For each `x`, if `k - x` has a positive count in the map, form an operation and decrement it; otherwise increment the count of `x`. One pass, O(n).

---

### M10 · Brick Wall

**🔗 [LC 554 — Brick Wall](https://leetcode.com/problems/brick-wall/)** · Medium
**Pattern:** Frequency Map | **Companies:** Meta, Amazon

**Hint:** Count how many rows have a brick edge at each position (prefix widths, excluding the wall's end). Cutting at the most common edge crosses the fewest bricks: `rows - maxEdgeCount`.

---

### M11 · Number of Pairs of Interchangeable Rectangles

**🔗 [LC 2001 — Number of Pairs of Interchangeable Rectangles](https://leetcode.com/problems/number-of-pairs-of-interchangeable-rectangles/)** · Medium
**Pattern:** Group-by-Key | **Companies:** Amazon, Google

**Hint:** Two rectangles are interchangeable when `w / h` is equal. Use the reduced fraction `(w / g, h / g)` as the key (not a `double`). A group of size `c` contributes `c × (c - 1) / 2` pairs — or add the running count as you go.

---

### M12 · Max Sum of a Pair With Equal Sum of Digits

**🔗 [LC 2342 — Max Sum of a Pair With Equal Sum of Digits](https://leetcode.com/problems/max-sum-of-a-pair-with-equal-sum-of-digits/)** · Medium
**Pattern:** Group by Derived Key | **Companies:** Amazon, Google

**Hint:** Key each number by its digit sum. Keep only the largest value seen per key; when a new number shares a key, update the answer with `best[key] + x`, then update `best[key]`.

---

### M13 · Subarray Sums Divisible by K

**🔗 [LC 974 — Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)** · Medium
**Pattern:** Prefix Sum + Map | **Companies:** Amazon, Google, Meta

**Hint:** Count prefix sums modulo `k`, normalised to be non-negative (`((sum % k) + k) % k`), starting with `{0: 1}`. Two prefixes with equal remainders bound a divisible subarray, so add the current count before incrementing it.

---

## 🔴 Hard Tier (5 Problems)

_Focus on cache design, complex mapping invariants, and advanced grouping._

### H1 · LRU Cache

**🔗 [LC 146 — LRU Cache](https://leetcode.com/problems/lru-cache/)** · Medium
**Pattern:** HashMap + Doubly Linked List | **Companies:** Amazon, Microsoft, Meta, Google

**Hint:** A HashMap from key to node, plus a doubly linked list with head and tail sentinels in recency order. `get` moves the node to the front; `put` inserts or updates at the front and evicts `tail.prev` when over capacity. In Java, `LinkedHashMap` in access order with `removeEldestEntry` does the same.

---

### H2 · Maximum Equal Frequency

**🔗 [LC 1224 — Maximum Equal Frequency](https://leetcode.com/problems/maximum-equal-frequency/)** · Hard
**Pattern:** Frequency of Frequencies | **Companies:** Google, Amazon

**Hint:** Maintain `count[x]` and `freqOfCount[c]`. After each prefix, it's valid if: every count is 1; or one value has count 1 and the rest share a max count; or one value has max count `mx` and the rest have `mx - 1`.

---

### H3 · Longest Duplicate Substring

**🔗 [LC 1044 — Longest Duplicate Substring](https://leetcode.com/problems/longest-duplicate-substring/)** · Hard
**Pattern:** Rolling Hash + Binary Search | **Companies:** Google, Amazon

**Hint:** Binary search the length `L` (if a duplicate of length `L` exists, one of length `L - 1` does too). For each `L`, hash every substring with a rolling hash and check for repeats in a set — verify real matches to guard against collisions.

---

### H4 · All O`one Data Structure

**🔗 [LC 432 — All O`one Data Structure](https://leetcode.com/problems/all-oone-data-structure/)** · Hard
**Pattern:** HashMap + Frequency Bucket List | **Companies:** Google, Amazon, Meta

**Hint:** Keep a doubly linked list of buckets in increasing count order, each holding a set of keys, plus `key → bucket`. `inc` and `dec` move a key to the neighbouring bucket (creating or removing buckets as needed). `getMaxKey` and `getMinKey` read the list's ends in O(1).

---

### H5 · Palindrome Pairs

**🔗 [LC 336 — Palindrome Pairs](https://leetcode.com/problems/palindrome-pairs/)** · Hard
**Pattern:** Hashing Reversed Words | **Companies:** Google, Airbnb, Amazon

**Hint:** Map each reversed word to its index. For every word and split point, if the left part is a palindrome and the reversed right part is in the map (a different index), you've found a pair — and symmetrically for the right part.

---

## 🧠 Conceptual Check

Answer these without looking at code:

1. **Load Factor**: Java's HashMap doubles capacity when load factor exceeds 0.75. Why 0.75 specifically? What are the tradeoffs of 0.5 vs 0.99?
2. **hashCode() contract**: If two objects are `equals()`, what must be true of their `hashCode()`? What about the reverse?
3. **Treeification**: Why does Java 8's HashMap convert a linked list bucket to a Red-Black tree when chain length > 8? What's the worst-case complexity improvement?
4. **int[] vs HashMap**: For character frequency counting on lowercase alpha strings, why is `int[26]` preferable to `HashMap<Character, Integer>`?
5. **LinkedHashMap**: Explain how `removeEldestEntry` works. How does access-order mode differ from insertion-order mode?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                  |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [LRU Cache](https://leetcode.com/problems/lru-cache/), [Maximum Equal Frequency](https://leetcode.com/problems/maximum-equal-frequency/), [Longest Duplicate Substring](https://leetcode.com/problems/longest-duplicate-substring/), [All O`one Data Structure](https://leetcode.com/problems/all-oone-data-structure/) |
| **Google**    | [LRU Cache](https://leetcode.com/problems/lru-cache/), [Maximum Equal Frequency](https://leetcode.com/problems/maximum-equal-frequency/), [Longest Duplicate Substring](https://leetcode.com/problems/longest-duplicate-substring/), [All O`one Data Structure](https://leetcode.com/problems/all-oone-data-structure/) |
| **Meta**      | [LRU Cache](https://leetcode.com/problems/lru-cache/), [All O`one Data Structure](https://leetcode.com/problems/all-oone-data-structure/), [Group Anagrams](https://leetcode.com/problems/group-anagrams/), [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)                               |
| **Microsoft** | [LRU Cache](https://leetcode.com/problems/lru-cache/), [Two Sum](https://leetcode.com/problems/two-sum/), [Roman to Integer](https://leetcode.com/problems/roman-to-integer/)                                                                                                                                           |
| **Apple**     | [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/), [Ransom Note](https://leetcode.com/problems/ransom-note/)                                                                                                                                                                                      |

---

## ✅ Completion Checklist

- [ ] All 7 Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] All 5 conceptual questions answered out loud
- [ ] I can explain load factor, collisions and treeification in Java's HashMap
- [ ] I can choose between `int[26]` and a HashMap for counting

---

**← [Lecture 12 · Stacks & Queues](../Lecture12/Assignment.md)** &nbsp;·&nbsp; **[Lecture 14 · Matrix Problems](../Lecture14/Assignment.md) →**
