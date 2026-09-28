# 🔤 Assignment 29 — Tries (Prefix Trees)

> **Lecture:** 36 of 45 — Tries (Prefix Trees)
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 4 days · **Total Problems:** 18 (5 Easy · 9 Medium · 4 Hard)
> **Goal:** Write a trie from scratch and recognise the five shapes — plain, wildcard, grid-driven, binary and reversed — from the problem statement alone.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                        | Pattern                       | Move                                                          |
| -------------------------------------------- | ----------------------------- | ------------------------------------------------------------- |
| Does any word start with this prefix         | Plain trie                    | walk(prefix) ≠ null — arriving is the answer                  |
| Is this exact word stored                    | Plain trie, or a hash set     | Check isWord, not just the node                               |
| Pattern contains a wildcard                  | Trie + DFS                    | Branch into all 26 children at the dot                        |
| All words sharing a prefix, in order         | Trie + DFS, inserted sorted   | The prefix node roots the answer set                          |
| Many words hidden in a grid or text          | Trie drives the traversal     | One walk for the whole dictionary; prune dead branches        |
| Question is about endings, not beginnings    | Reversed trie                 | Insert reversed, read the input backwards                     |
| Maximum XOR, or a bitwise partner            | Binary trie, bit 31 down to 0 | Take the opposite bit whenever that child exists              |
| A constraint limits which elements are legal | Offline queries + trie        | Sort the queries, insert lazily, restore the order at the end |

---

## 🟢 Easy Tier (5 Problems)

_Prefix and substring warm-ups. Most of them pass with a direct scan — solve each twice, once directly and once with a trie, and notice which ones the trie actually helps._

### E1 · Check If String Is a Prefix of Array

**🔗 [LC 1961 — Check If String Is a Prefix of Array](https://leetcode.com/problems/check-if-string-is-a-prefix-of-array/)** · Easy
**Pattern:** Prefix matching | **Companies:** Amazon

**Hint:** Concatenate words until you match or overshoot — no trie needed, but it is the same walk.

---

### E2 · Count Prefixes of a Given String

**🔗 [LC 2255 — Count Prefixes of a Given String](https://leetcode.com/problems/count-prefixes-of-a-given-string/)** · Easy
**Pattern:** Prefix counting | **Companies:** Amazon · Google

**Hint:** One startsWith per word; write it once with a trie and once without, and compare.

---

### E3 · Count Prefix and Suffix Pairs I

**🔗 [LC 3042 — Count Prefix and Suffix Pairs I](https://leetcode.com/problems/count-prefix-and-suffix-pairs-i/)** · Easy
**Pattern:** Prefix + suffix pair | **Companies:** Google · Amazon

**Hint:** Brute force is fine at n ≤ 50; think about what a trie of reversed words would buy you.

---

### E4 · String Matching in an Array

**🔗 [LC 1408 — String Matching in an Array](https://leetcode.com/problems/string-matching-in-an-array/)** · Easy
**Pattern:** Substring matching | **Companies:** Amazon

**Hint:** Every pair check is O(L²) here — then ask what a suffix structure would do instead.

---

### E5 · Number of Strings That Appear as Substrings in Word

**🔗 [LC 1967 — Number of Strings That Appear as Substrings in Word](https://leetcode.com/problems/number-of-strings-that-appear-as-substrings-in-word/)** · Easy
**Pattern:** Substring counting | **Companies:** Google

**Hint:** A direct scan passes; note which of these easy problems a trie would actually speed up.

---

## 🟡 Medium Tier (9 Problems)

_The working set. You build the structure, then bend it: wildcards, stored values, autocomplete, path segments. One of them is deliberately not a trie problem — spot it._

### M1 · Implement Trie (Prefix Tree)

**🔗 [LC 208 — Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)** · Medium
**Pattern:** Trie fundamentals | **Companies:** Google · Amazon · Microsoft

**Hint:** Two fields per node. Factor the shared walk out of search and startsWith.

---

### M2 · Design Add and Search Words Data Structure

**🔗 [LC 211 — Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)** · Medium
**Pattern:** Trie + DFS (wildcards) | **Companies:** Meta · Google · Amazon

**Hint:** A letter takes one step; a dot recurses into all 26 children.

---

### M3 · Replace Words

**🔗 [LC 648 — Replace Words](https://leetcode.com/problems/replace-words/)** · Medium
**Pattern:** Trie + prefix replace | **Companies:** Amazon · Google

**Hint:** Insert the roots, then walk each word and cut at the first node marked as a root.

---

### M4 · Map Sum Pairs

**🔗 [LC 677 — Map Sum Pairs](https://leetcode.com/problems/map-sum-pairs/)** · Medium
**Pattern:** Trie with values | **Companies:** Amazon · Google

**Hint:** Store the value at the end node; sum the subtree under the prefix, and handle re-inserted keys.

---

### M5 · Search Suggestions System

**🔗 [LC 1268 — Search Suggestions System](https://leetcode.com/problems/search-suggestions-system/)** · Medium
**Pattern:** Trie + DFS (autocomplete) | **Companies:** Amazon · Google

**Hint:** Sort first so a DFS in a–z order meets the three answers in the right order.

---

### M6 · Longest Word in Dictionary

**🔗 [LC 720 — Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)** · Medium
**Pattern:** Trie + DFS (build-up) | **Companies:** Google · Amazon

**Hint:** A word only counts if every prefix of it is also a word — check that on the way down.

---

### M7 · Short Encoding of Words

**🔗 [LC 820 — Short Encoding of Words](https://leetcode.com/problems/short-encoding-of-words/)** · Medium
**Pattern:** Reversed trie | **Companies:** Amazon · Google

**Hint:** A word that is a suffix of another costs nothing. Insert reversed and count the leaf depths.

---

### M8 · Remove Sub-Folders from the Filesystem

**🔗 [LC 1233 — Remove Sub-Folders from the Filesystem](https://leetcode.com/problems/remove-sub-folders-from-the-filesystem/)** · Medium
**Pattern:** Trie on path segments | **Companies:** Amazon · Google

**Hint:** The alphabet is folder names, not letters. Stop the walk at the first node marked as a folder.

---

### M9 · Camelcase Matching

**🔗 [LC 1023 — Camelcase Matching](https://leetcode.com/problems/camelcase-matching/)** · Medium
**Pattern:** Greedy two pointers | **Companies:** Google

**Hint:** Not a trie at all — match the pattern greedily and reject any extra uppercase letter.

---

## 🔴 Hard Tier (4 Problems)

_The four interview favourites: the grid dictionary, the binary trie with a constraint, the double-ended trie, and the streaming one._

### H1 · Word Search II

**🔗 [LC 212 — Word Search II](https://leetcode.com/problems/word-search-ii/)** · Hard
**Pattern:** Trie + grid DFS | **Companies:** Google · Amazon · Airbnb

**Hint:** Store the word on its end node, blank it after the first find, and unlink exhausted branches.

---

### H2 · Maximum XOR With an Element From Array

**🔗 [LC 1707 — Maximum XOR With an Element From Array](https://leetcode.com/problems/maximum-xor-with-an-element-from-array/)** · Hard
**Pattern:** Binary trie + offline queries | **Companies:** Google · Amazon

**Hint:** Sort nums and sort the queries by their limit; insert numbers only as the limit grows past them.

---

### H3 · Prefix and Suffix Search

**🔗 [LC 745 — Prefix and Suffix Search](https://leetcode.com/problems/prefix-and-suffix-search/)** · Hard
**Pattern:** Double trie (prefix + suffix) | **Companies:** Google · Amazon

**Hint:** Insert every suffix + "{" + word, so one lookup answers both halves at once.

---

### H4 · Stream of Characters

**🔗 [LC 1032 — Stream of Characters](https://leetcode.com/problems/stream-of-characters/)** · Hard
**Pattern:** Reversed trie | **Companies:** Google · Amazon

**Hint:** Insert the words reversed and walk the stream backwards, no further than the longest word.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — insert a word of length L into a trie

// Snippet 2 — insert n words of average length L

// Snippet 3 — search with d wildcard dots

// Snippet 4 — maximum XOR pair with a binary trie

// Snippet 5 — Word Search II on an m × n board, words up to length L

// Snippet 6 — space for a trie of n words, alphabet of size Σ
```

**Complexity Answers:**

1. **O(L)**.
2. **O(n · L)**.
3. **O(26ᵈ · L)** in the worst case.
4. **O(32 · n)**.
5. **O(m · n · 4 · 3ᴸ⁻¹)**.
6. **O(n · L · Σ)** in the worst case.

---

## 🔍 Self-Assessment — True / False

1. Trie lookup time depends on how many words are stored. → **False** — it depends only on the word length
2. A trie can answer "does any word start with this prefix?" and a hash set cannot, efficiently. → **True**
3. A trie needs an end-of-word flag. → **True** — otherwise "app" and a prefix of "apple" look the same
4. A binary trie for 32-bit numbers has depth 32. → **True**
5. Tries always use less memory than a hash set of the same words. → **False** — often more: an array of children per node
6. Wildcard search in a trie is always O(L). → **False** — each dot may branch into every child

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The flag:** Why does a TrieNode need `isWord` when the path to it already spells something? Give an input that breaks without it.
2. **Versus a hash set:** Both insert and search are O(L). So what does a trie actually buy you, and what does it cost?
3. **Array or map:** When would you choose a `Map<Character, TrieNode>` over a 26-slot array, and what do you give up?
4. **Wildcards:** Where does the `26^d` in the wildcard complexity come from, and why are leading dots the worst case?
5. **Word Search II:** Explain why the trie version beats running the single-word search once per word. Where exactly is the saving?
6. **Pruning:** What input punishes an unpruned Word Search II, and what does unlinking exhausted nodes do to it?
7. **Greedy bits:** Why is it safe to take the opposite bit greedily in a binary trie? Name the property of binary place value you are using.
8. **Bit order:** What goes wrong if you insert numbers into a binary trie starting from bit 0?
9. **Reversal:** How does reversing the stored words turn an "ends with" question into a "starts with" one? What bound keeps each query cheap?
10. **Offline queries:** What does it mean to answer queries offline, and what must you remember to do before returning the answers?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Check If String Is a Prefix of Array](https://leetcode.com/problems/check-if-string-is-a-prefix-of-array/), [String Matching in an Array](https://leetcode.com/problems/string-matching-in-an-array/), [Maximum XOR With an Element From Array](https://leetcode.com/problems/maximum-xor-with-an-element-from-array/), [Prefix and Suffix Search](https://leetcode.com/problems/prefix-and-suffix-search/) |
| **Google**    | [Camelcase Matching](https://leetcode.com/problems/camelcase-matching/), [Number of Strings That Appear as Substrings in Word](https://leetcode.com/problems/number-of-strings-that-appear-as-substrings-in-word/), [Stream of Characters](https://leetcode.com/problems/stream-of-characters/), [Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)                     |
| **Airbnb**    | [Word Search II](https://leetcode.com/problems/word-search-ii/)                                                                                                                                                                                                                                                                                                                                              |
| **Meta**      | [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)                                                                                                                                                                                                                                                                                      |
| **Microsoft** | [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)                                                                                                                                                                                                                                                                                                                    |

---

## ✅ Completion Checklist

- [ ] All 5 Easy problems solved
- [ ] All 9 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 10 conceptual questions answered out loud
- [ ] I can write a trie from scratch with no reference
- [ ] I can name the trie variant a new problem needs within 30 seconds
- [ ] I can state the memory cost honestly and say when a hash set or a sorted array is better
- [ ] I can write the wildcard DFS and the grid DFS without confusing their states
- [ ] I can build a binary trie and explain the greedy argument
- [ ] I revisited every problem I needed a hint for

---

**← [Lecture 35 · Dynamic Programming IV — Interval, Tree, Bitmask & Digit](../Lecture35/Assignment.md)** &nbsp;·&nbsp; **[Lecture 37 · Segment Trees & Fenwick Trees](../Lecture37/Assignment.md) →**
