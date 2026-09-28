# 🔡 Assignment 39 — String Algorithms (KMP, Z, Rabin-Karp, Manacher)

> **Lecture:** 39 of 45 — String Algorithms (KMP, Z, Rabin-Karp, Manacher)
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 5 days · **Total Problems:** 20 (3 Easy · 10 Medium · 7 Hard)
> **Goal:** Match patterns and find palindromes in linear time, and choose between KMP, rolling hashes, the Z-array and Manacher from a problem’s wording.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                      | Pattern                 | Move                                       |
| ---------------------------------------------------------- | ----------------------- | ------------------------------------------ |
| Find a pattern in a text, n up to 10⁵                      | KMP                     | Failure table, then one pass               |
| Longest prefix that is also a suffix; repeated blocks      | KMP failure table       | Read lps[n − 1]                            |
| Compare many substrings with each other                    | Rolling hash            | O(1) per comparison; verify or double-hash |
| Longest substring with a property that shrinks with length | Binary search + hashing | Check each length with a set of hashes     |
| How far each suffix matches the start                      | Z-array                 | Exactly what it stores                     |
| Longest palindrome, n ≤ 1000                               | Expand around centre    | O(n²), simple                              |
| Longest palindrome, or every centre’s radius, n ≈ 10⁵      | Manacher                | O(n)                                       |

---

## 🟢 Easy Tier (3 Problems)

_KMP and its failure table on friendly inputs, plus a palindrome warm-up. Write KMP in full, even where a built-in search would pass._

### E1 · Find the Index of the First Occurrence in a String

**🔗 [LC 28 — Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)** · Easy
**Pattern:** KMP | **Companies:** Google, Amazon, Microsoft

**Hint:** Write KMP end to end: failure table, then one forward pass. Say why the naive search is O(n · m).

---

### E2 · Repeated Substring Pattern

**🔗 [LC 459 — Repeated Substring Pattern](https://leetcode.com/problems/repeated-substring-pattern/)** · Easy
**Pattern:** KMP failure table | **Companies:** Amazon, Google

**Hint:** With L = lps[n − 1], the string is a repeated block exactly when L > 0 and n is divisible by n − L. (Or: s is in (s + s) with the first and last characters removed.)

---

### E3 · Lexicographically Smallest Palindrome

**🔗 [LC 2697 — Lexicographically Smallest Palindrome](https://leetcode.com/problems/lexicographically-smallest-palindrome/)** · Easy
**Pattern:** Two pointers on a palindrome | **Companies:** Amazon

**Hint:** Compare s[i] and s[n − 1 − i]; when they differ, set both to the smaller letter.

---

## 🟡 Medium Tier (10 Problems)

_Searching, hashing and palindromes in combination. Before coding, say which of the four algorithms each one needs._

### M1 · Repeated String Match

**🔗 [LC 686 — Repeated String Match](https://leetcode.com/problems/repeated-string-match/)** · Medium
**Pattern:** Search after repeating | **Companies:** Google, Amazon

**Hint:** Repeat a until the result is at least as long as b, then try one more copy. Search each with KMP or a rolling hash.

---

### M2 · Remove All Occurrences of a Substring

**🔗 [LC 1910 — Remove All Occurrences of a Substring](https://leetcode.com/problems/remove-all-occurrences-of-a-substring/)** · Medium
**Pattern:** KMP state on a stack | **Companies:** Amazon, Google

**Hint:** Removing the leftmost occurrence repeatedly is O(n · m) done naively. Push characters onto a stack along with the KMP state after each; on a full match, pop m characters and resume from the state below.

---

### M3 · Find Beautiful Indices in the Given Array I

**🔗 [LC 3006 — Find Beautiful Indices in the Given Array I](https://leetcode.com/problems/find-beautiful-indices-in-the-given-array-i/)** · Medium
**Pattern:** KMP twice, then two pointers | **Companies:** Google, Amazon

**Hint:** Find every occurrence of a and of b with KMP. Both lists come out sorted, so a moving pointer (or binary search) finds a b-index within k of each a-index.

---

### M4 · Minimum Time to Revert Word to Initial State I

**🔗 [LC 3029 — Minimum Time to Revert Word to Initial State I](https://leetcode.com/problems/minimum-time-to-revert-word-to-initial-state-i/)** · Medium
**Pattern:** Z-array | **Companies:** Google

**Hint:** After t seconds the unchanged part is word[t·k ..]. It is back to the start as soon as that suffix is a prefix of word: the smallest t with t·k ≥ n or Z[t·k] = n − t·k.

---

### M5 · Check If a String Contains All Binary Codes of Size K

**🔗 [LC 1461 — Check If a String Contains All Binary Codes of Size K](https://leetcode.com/problems/check-if-a-string-contains-all-binary-codes-of-size-k/)** · Medium
**Pattern:** Rolling a k-bit number | **Companies:** Google, Amazon

**Hint:** All 2ᵏ codes are present exactly when there are 2ᵏ distinct length-k substrings. Slide a k-bit number: shift, add the new bit, mask.

---

### M6 · Maximum Number of Occurrences of a Substring

**🔗 [LC 1297 — Maximum Number of Occurrences of a Substring](https://leetcode.com/problems/maximum-number-of-occurrences-of-a-substring/)** · Medium
**Pattern:** Fixed-length windows | **Companies:** Amazon, Google

**Hint:** Only minSize matters: any longer qualifying substring contains a qualifying one of length minSize that occurs at least as often. Count length-minSize windows with at most maxLetters distinct characters.

---

### M7 · Split Two Strings to Make Palindrome

**🔗 [LC 1616 — Split Two Strings to Make Palindrome](https://leetcode.com/problems/split-two-strings-to-make-palindrome/)** · Medium
**Pattern:** Greedy match from both ends | **Companies:** Google

**Hint:** Match a’s prefix against b’s reversed suffix from the outside in. Where they stop matching, the remaining middle of either a or b must itself be a palindrome. Try both orders.

---

### M8 · Longest Palindrome by Concatenating Two Letter Words

**🔗 [LC 2131 — Longest Palindrome by Concatenating Two Letter Words](https://leetcode.com/problems/longest-palindrome-by-concatenating-two-letter-words/)** · Medium
**Pattern:** Palindrome by pairing | **Companies:** Google, Amazon

**Hint:** Pair each word with its reverse; words like "gg" pair with themselves, and one leftover such word can sit in the middle.

---

### M9 · Break a Palindrome

**🔗 [LC 1328 — Break a Palindrome](https://leetcode.com/problems/break-a-palindrome/)** · Medium
**Pattern:** Palindrome reasoning | **Companies:** Amazon, Google

**Hint:** Change the first non-a in the first half to a. If there is none, change the last character to b. A single character cannot be fixed: return "".

---

### M10 · Unique Length-3 Palindromic Subsequences

**🔗 [LC 1930 — Unique Length-3 Palindromic Subsequences](https://leetcode.com/problems/unique-length-3-palindromic-subsequences/)** · Medium
**Pattern:** First and last occurrence | **Companies:** Amazon, Google

**Hint:** For each letter c, take its first and last positions; the answer counts the distinct letters strictly between them.

---

## 🔴 Hard Tier (7 Problems)

_Each Hard problem is one array from this lecture — lps, Z, hashes or Manacher radii — plus one well-chosen loop._

### H1 · Longest Happy Prefix

**🔗 [LC 1392 — Longest Happy Prefix](https://leetcode.com/problems/longest-happy-prefix/)** · Hard
**Pattern:** KMP failure table | **Companies:** Google, Amazon

**Hint:** The answer is the prefix of length lps[n − 1] — the failure table’s last entry is exactly the longest proper prefix that is also a suffix.

---

### H2 · Sum of Scores of Built Strings

**🔗 [LC 2223 — Sum of Scores of Built Strings](https://leetcode.com/problems/sum-of-scores-of-built-strings/)** · Hard
**Pattern:** Z-array | **Companies:** Google, Amazon

**Hint:** Each intermediate string is a suffix of s, and its score is Z at its start. The answer is n plus the sum of the Z-array.

---

### H3 · Find Substring With Given Hash Value

**🔗 [LC 2156 — Find Substring With Given Hash Value](https://leetcode.com/problems/find-substring-with-given-hash-value/)** · Hard
**Pattern:** Rolling hash, right to left | **Companies:** Google, Amazon

**Hint:** The weights grow to the right, so rolling left to right needs division, which may not exist mod m. Roll from the right: multiply by p, add the new character, subtract the one leaving with weight pᵏ.

---

### H4 · Distinct Echo Substrings

**🔗 [LC 1316 — Distinct Echo Substrings](https://leetcode.com/problems/distinct-echo-substrings/)** · Hard
**Pattern:** Rolling hash + set | **Companies:** Google, Amazon

**Hint:** For each half-length L and start i, compare the hash of text[i..i+L) with text[i+L..i+2L). Put matching substrings’ hashes (plus L) in a set to count distinct ones.

---

### H5 · Maximum Product of the Length of Two Palindromic Substrings

**🔗 [LC 1960 — Maximum Product of the Length of Two Palindromic Substrings](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-substrings/)** · Hard
**Pattern:** Manacher + best before / after | **Companies:** Google, Amazon

**Hint:** Manacher gives each centre’s odd palindrome. Spread "longest ending here" inwards by 2 per step, take prefix maxima, do the mirror for starts, and multiply across every split point.

---

### H6 · Longest Common Subpath

**🔗 [LC 1923 — Longest Common Subpath](https://leetcode.com/problems/longest-common-subpath/)** · Hard
**Pattern:** Binary search + rolling hash | **Companies:** Google, Amazon

**Hint:** A common subpath of length L means one of length L − 1 too, so binary search L. For each L, hash every length-L window of each path and intersect the sets; use two moduli.

---

### H7 · Number of Subarrays That Match a Pattern II

**🔗 [LC 3036 — Number of Subarrays That Match a Pattern II](https://leetcode.com/problems/number-of-subarrays-that-match-a-pattern-ii/)** · Hard
**Pattern:** Encode, then KMP | **Companies:** Google, Amazon

**Hint:** Turn nums into a sequence of 1, 0, −1 for each adjacent pair, then count occurrences of pattern in it with KMP or the Z-array.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — naive search for a pattern of length m in a text of length n

// Snippet 2 — building the KMP failure table for a pattern of length m

// Snippet 3 — KMP search, text n, pattern m

// Snippet 4 — Rabin-Karp with no collisions; and in the worst case, verifying every hash match

// Snippet 5 — Z-array of a string of length n

// Snippet 6 — longest palindrome by expanding around every centre; then by Manacher
```

**Complexity Answers:**

1. **O(n · m)** worst case.
2. **O(m)** — len rises by at most one per step, so the fall-backs are bounded in total.
3. **O(n + m)**.
4. **O(n + m)** expected; **O(n · m)** if every window collides and must be verified.
5. **O(n)**.
6. **O(n²)** and **O(n)**.

---

## 🔍 Self-Assessment — True / False

1. KMP ever moves the text pointer backwards. → **False** — only the pattern pointer falls back
2. lps[i] can equal i + 1. → **False** — the prefix-suffix must be proper — shorter than the whole prefix
3. Equal rolling hashes prove two substrings are equal. → **False** — different strings can collide; verify or use two moduli
4. Z[i] is how many characters starting at i match the start of the string. → **True**
5. Manacher’s # separators make even-length palindromes look like odd-length ones. → **True**
6. A rolling hash is always the best choice for a single pattern search. → **False** — KMP gives the same speed with no collision risk

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Failure table**: Build lps for "aabaaab" by hand and explain the value at each position.
2. **Linear time**: Why is KMP O(n + m) even though its inner loop is a while loop?
3. **Collisions**: What is a hash collision, and what are two ways to protect against one?
4. **Direction**: Why is Find Substring With Given Hash Value solved by rolling from the right?
5. **Z versus KMP**: Both are linear. Name a question each answers more directly than the other.
6. **Mirror**: Explain in words why a centre inside a known palindrome can copy its mirror image’s radius, and when it must still expand.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | [Minimum Time to Revert Word to Initial State I](https://leetcode.com/problems/minimum-time-to-revert-word-to-initial-state-i/), [Split Two Strings to Make Palindrome](https://leetcode.com/problems/split-two-strings-to-make-palindrome/), [Distinct Echo Substrings](https://leetcode.com/problems/distinct-echo-substrings/), [Find Substring With Given Hash Value](https://leetcode.com/problems/find-substring-with-given-hash-value/) |
| **Amazon**    | [Lexicographically Smallest Palindrome](https://leetcode.com/problems/lexicographically-smallest-palindrome/), [Longest Common Subpath](https://leetcode.com/problems/longest-common-subpath/), [Longest Happy Prefix](https://leetcode.com/problems/longest-happy-prefix/), [Maximum Product of the Length of Two Palindromic Substrings](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-substrings/)         |
| **Microsoft** | [Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)                                                                                                                                                                                                                                                                                                        |

---

## ✅ Completion Checklist

- [ ] All 3 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 7 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name the algorithm for each problem from its wording alone
- [ ] I wrote KMP and the Z-array from memory at least once

---

**← [Lecture 38 · Square Root Decomposition & Mo's Algorithm](../Lecture38/Assignment.md)** &nbsp;·&nbsp; **[Lecture 40 · Advanced Graph Algorithms](../Lecture40/Assignment.md) →**
