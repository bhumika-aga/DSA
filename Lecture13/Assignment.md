# 🗃️ Assignment 13 — HashMap & HashSet Deep Dive

> **Lecture:** Topic 13 — HashMap & HashSet
> **Topic Count:** 13 of 30 — Phase 2 Core Data Structures
> **Duration:** 4 Days
> **Core Problems:** 25 (7 Easy · 13 Medium · 5 Hard)
> **Goal:** Master the 5 core HashMap patterns: Frequency Map, Complement Lookup, Prefix Sum + Map, Group-by-Key, and Set Membership. Understand hashing internals, collision resolution, and cache design.

---

## 📊 Topic Overview

The HashMap is the single most-used data structure in FAANG coding interviews. It transforms O(n) linear scans into O(1) lookups. Understanding **when** to use it and **which pattern** to apply is the difference between a 30-minute solution and a 3-minute one.

- **Primary Patterns**: Complement Lookup (Two-Sum family), Frequency Map, Prefix Sum + Map, Group-by-Key, Set Membership (consecutive sequences).
- **Key Focus**: Recognising the pattern from the problem statement before writing a single line of code.

---

## 🟢 Easy Tier (Foundations)

_Build confidence with the core HashMap API and the simplest pattern variants._

1. **[Two Sum](https://leetcode.com/problems/two-sum/) (LC 1)** — The quintessential complement lookup. `[Pattern: Complement Lookup]`
2. **[Roman to Integer](https://leetcode.com/problems/roman-to-integer/) (LC 13)** — Build a Character-to-int map, scan right to left. `[Pattern: Character Map]`
3. **[Valid Anagram](https://leetcode.com/problems/valid-anagram/) (LC 242)** — Frequency arrays (int[26]) vs HashMap — explain the tradeoff. `[Pattern: Frequency Map]`
4. **[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) (LC 217)** — HashSet membership check. `[Pattern: Set Membership]`
5. **[Ransom Note](https://leetcode.com/problems/ransom-note/) (LC 383)** — Frequency count magazine chars, subtract for ransom. `[Pattern: Frequency Map]`
6. **[Word Pattern](https://leetcode.com/problems/word-pattern/) (LC 290)** — Two-way bijection between pattern chars and words. `[Pattern: Bijective Map]`
7. **[Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/) (LC 205)** — Two-way character mapping invariant. `[Pattern: Bijective Map]`

---

## 🟡 Medium Tier (Advanced Patterns)

_Focus on multi-step HashMap reasoning and patterns within patterns._

1. **[Group Anagrams](https://leetcode.com/problems/group-anagrams/) (LC 49)** — Sort-key grouping. Bonus: frequency-array key variant. `[Pattern: Group-by-Key]`
2. **[Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) (LC 347)** — Freq map + min-heap of size K. `[Pattern: Frequency Map + Heap]`
3. **[Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) (LC 560)** — The canonical prefix sum + map problem. `[Pattern: Prefix Sum + Map]`
4. **[Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) (LC 128)** — HashSet + sequence start trick → O(n). `[Pattern: Set Membership]`
5. **[Four Sum II](https://leetcode.com/problems/4sum-ii/) (LC 454)** — Count pairs from A+B whose negation appears in C+D map. `[Pattern: Complement Lookup]`
6. **[Contiguous Array](https://leetcode.com/problems/contiguous-array/) (LC 525)** — Longest subarray with equal 0s and 1s using prefix sum. `[Pattern: Prefix Sum + Map]`
7. **[Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) (LC 76)** — Sliding window + two frequency maps. `[Company: Google] [Pattern: Sliding Window + Map]`
8. **[Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/) (LC 438)** — Fixed-window frequency comparison. `[Pattern: Sliding Window + Map]`
9. **[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) (LC 3)** — HashSet + two-pointer sliding window. `[Company: Amazon]`
10. **[Brick Wall](https://leetcode.com/problems/brick-wall/) (LC 554)** — Count edge frequencies with a map. `[Pattern: Frequency Map]`
11. **[Number of Pairs of Interchangeable Rectangles](https://leetcode.com/problems/number-of-pairs-of-interchangeable-rectangles/) (LC 2001)** — Ratio as map key + combinatorics. `[Pattern: Group-by-Key]`
12. **[Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) (LC 138)** — HashMap as old-to-new node pointer store. `[Company: Meta]`
13. **[Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/) (LC 974)** — Prefix sum modulo K + frequency map. `[Pattern: Prefix Sum + Map]`

---

## 🔴 Challenge Zone (Mastery)

_Focus on cache design, complex mapping invariants, and advanced grouping._

1. **[LRU Cache](https://leetcode.com/problems/lru-cache/) (LC 146)** — LinkedHashMap OR HashMap + Doubly Linked List. Both O(1). `[Company: Amazon · Google · Meta]`
2. **[LFU Cache](https://leetcode.com/problems/lfu-cache/) (LC 460)** — HashMap + freq map + multiple doubly linked lists. `[Company: Google]`
3. **[Longest Duplicate Substring](https://leetcode.com/problems/longest-duplicate-substring/) (LC 1044)** — Rolling Hash (Rabin-Karp) + binary search on length. `[Company: Google]`
4. **[All O'one Data Structure](https://leetcode.com/problems/all-oone-data-structure/) (LC 432)** — DLL of frequency buckets + two maps. `[Company: Google]`
5. **[Design Twitter](https://leetcode.com/problems/design-twitter/) (LC 355)** — HashMap + PriorityQueue merge of per-user tweet lists. `[Company: Amazon]`

---

## 📊 Conceptual Check

Answer these without looking at code:

1. **Load Factor**: Java's HashMap doubles capacity when load factor exceeds 0.75. Why 0.75 specifically? What are the tradeoffs of 0.5 vs 0.99?
2. **hashCode() contract**: If two objects are `equals()`, what must be true of their `hashCode()`? What about the reverse?
3. **Treeification**: Why does Java 8's HashMap convert a linked list bucket to a Red-Black tree when chain length > 8? What's the worst-case complexity improvement?
4. **int[] vs HashMap**: For character frequency counting on lowercase alpha strings, why is `int[26]` preferable to `HashMap<Character, Integer>`?
5. **LinkedHashMap**: Explain how `removeEldestEntry` works. How does access-order mode differ from insertion-order mode?

---

## 🏢 Company Focus

| Company       | Key Problem(s)                                                                                                                                                                                                                          |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/), [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/), [LFU Cache](https://leetcode.com/problems/lfu-cache/) |
| **Amazon**    | [Two Sum](https://leetcode.com/problems/two-sum/), [LRU Cache](https://leetcode.com/problems/lru-cache/), [Longest Substring Without Repeating](https://leetcode.com/problems/longest-substring-without-repeating-characters/)          |
| **Meta**      | [Group Anagrams](https://leetcode.com/problems/group-anagrams/), [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/), [LRU Cache](https://leetcode.com/problems/lru-cache/)                   |
| **Microsoft** | [Roman to Integer](https://leetcode.com/problems/roman-to-integer/), [Find All Anagrams](https://leetcode.com/problems/find-all-anagrams-in-a-string/)                                                                                  |
| **Bloomberg** | [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/), [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)                                                                        |

---

**Next Topic**: Topic 14 — Matrix Problems →
