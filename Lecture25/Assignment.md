# 🎯 Assignment 18 — Two Pointers & Sliding Window

> **Lecture:** 25 of 45 — Two Pointers & Sliding Window
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 6 days · **Total Problems:** 30 (9 Easy · 16 Medium · 5 Hard)
> **Goal:** Stop choosing an algorithm and start recognising a shape. Every problem below is one of five.

---

## 🗺️ Pattern Recognition — Read Before Starting

| Signal Phrase                         | Shape           | Move                                          |
| ------------------------------------- | --------------- | --------------------------------------------- |
| "sorted array" + find a pair / triple | Opposite Ends   | `lo = 0`, `hi = n-1`, move the one that helps |
| "subarray of size exactly k"          | Fixed Window    | add right, remove left, every step            |
| "longest subarray such that …"        | Variable Window | expand right, shrink left while invalid       |
| "shortest subarray such that …"       | Variable Window | same loop — record **inside** the shrink      |
| "in place, keep order, drop some"     | Same Direction  | `slow` writes, `fast` reads                   |
| "exactly k distinct"                  | At-Most Trick   | `atMost(k) - atMost(k-1)`                     |
| "maximum of every window"             | Monotonic Deque | deque of indices, decreasing by value         |

> ⚠️ **Precondition:** sliding windows need monotonicity — adding an element must never make an
> invalid window valid again. Negative numbers break this. Those are prefix-sum problems (Lecture 26).

---

---

## 🟢 Easy Tier (9 Problems)

_No Easy problems at this stage of the course._

### E1 · Valid Palindrome

**🔗 [LC 125 — Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)** · Easy
**Pattern:** Opposite Ends | **Companies:** Meta, Amazon, Microsoft

**Hint:** Two pointers converging, skipping any character that is not alphanumeric. Compare lowercase forms. The skipping happens inside the outer loop, not before it.

---

### E2 · Move Zeroes

**🔗 [LC 283 — Move Zeroes](https://leetcode.com/problems/move-zeroes/)** · Easy
**Pattern:** Same Direction | **Companies:** Meta, Amazon, Microsoft

**Hint:** `slow` is a write cursor, `fast` a read cursor. Copy every non-zero forward, then fill the tail with zeros. Order of the non-zeros must be preserved.

---

### E3 · Remove Duplicates from Sorted Array

**🔗 [LC 26 — Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)** · Easy
**Pattern:** Same Direction | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Duplicates are adjacent because the array is sorted. Write a value only when it differs from `a[slow]`. Return `slow + 1`.

---

### E4 · Remove Element

**🔗 [LC 27 — Remove Element](https://leetcode.com/problems/remove-element/)** · Easy
**Pattern:** Same Direction | **Companies:** Amazon, Adobe

**Hint:** Same read/write cursors as Move Zeroes, but the keep-test is `a[fast] != val`. Order does not matter here, so a swap-with-end variant also works.

---

### E5 · Reverse String II

**🔗 [LC 541 — Reverse String II](https://leetcode.com/problems/reverse-string-ii/)** · Easy
**Pattern:** Opposite Ends in Blocks | **Companies:** Amazon, Microsoft

**Hint:** Step `i` by `2k`; reverse the chars in `[i, min(i + k, n) - 1]` with two pointers. Don't special-case the tail — the `min` handles it.

---

### E6 · Squares of a Sorted Array

**🔗 [LC 977 — Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)** · Easy
**Pattern:** Opposite Ends | **Companies:** Amazon, Meta, Google

**Hint:** The largest square is at one of the two ends, never in the middle. Fill the output array **backwards** from the larger of the two.

---

### E7 · Maximum Average Subarray I

**🔗 [LC 643 — Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)** · Easy
**Pattern:** Fixed Window | **Companies:** Amazon, Google

**Hint:** Build the first k elements, then roll: `sum += a[r] - a[r-k]`. Never rebuild the window from scratch.

---

### E8 · Substrings of Size Three with Distinct Characters

**🔗 [LC 1876 — Substrings of Size Three with Distinct Characters](https://leetcode.com/problems/substrings-of-size-three-with-distinct-characters/)** · Easy
**Pattern:** Fixed Window | **Companies:** Amazon, Adobe

**Hint:** Window size is fixed at 3, so you can check distinctness directly. Good warm-up for keeping counts in sync as the window rolls.

---

### E9 · Defuse the Bomb

**🔗 [LC 1652 — Defuse the Bomb](https://leetcode.com/problems/defuse-the-bomb/)** · Easy
**Pattern:** Fixed Window | **Companies:** Amazon, Google

**Hint:** A circular fixed window. Use modular indexing `(i + j) % n` rather than physically rotating the array, and handle `k < 0` by walking the other way.

---

## 🟡 Medium Tier (16 Problems)

_Core Interview Patterns._

### M1 · Two Sum II - Input Array Is Sorted

**🔗 [LC 167 — Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)** · Medium
**Pattern:** Opposite Ends | **Companies:** Amazon, Google, Adobe

**Hint:** Sorted input is the clue. Start at both ends; move `lo` right when the sum is too small, `hi` left when it is too big. O(1) space — no HashMap needed.

---

### M2 · Container With Most Water

**🔗 [LC 11 — Container With Most Water](https://leetcode.com/problems/container-with-most-water/)** · Medium
**Pattern:** Opposite Ends | **Companies:** Google, Amazon, Meta, Bloomberg

**Hint:** Area is width × the **shorter** wall. Width only shrinks as you converge, so always move the shorter side — moving the taller one can never improve the answer.

---

### M3 · 3Sum

**🔗 [LC 15 — 3Sum](https://leetcode.com/problems/3sum/)** · Medium
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Meta, Google, Adobe

**Hint:** Sort, fix an anchor, run converging pointers on the rest. The difficulty is deduplication: skip repeated anchors before the inner loop, and repeated `lo`/`hi` only after recording a hit.

---

### M4 · 3Sum Closest

**🔗 [LC 16 — 3Sum Closest](https://leetcode.com/problems/3sum-closest/)** · Medium
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Google, Meta

**Hint:** Same skeleton as 3Sum, but instead of testing equality you track the smallest `abs(sum - target)` seen so far. No deduplication needed.

---

### M5 · 4Sum

**🔗 [LC 18 — 4Sum](https://leetcode.com/problems/4sum/)** · Medium
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Google, Adobe

**Hint:** Two nested anchors then a converging pair — O(n³). Watch integer overflow on the sum: use `long`. Deduplicate at both anchor levels.

---

### M6 · Longest Substring Without Repeating Characters

**🔗 [LC 3 — Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)** · Medium
**Pattern:** Variable Window | **Companies:** Amazon, Google, Meta, Bloomberg

**Hint:** Store the last index of each character. On a repeat, jump `left` forward to just past the previous copy — use `Math.max` so a stale duplicate never drags `left` backwards.

---

### M7 · Longest Repeating Character Replacement

**🔗 [LC 424 — Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)** · Medium
**Pattern:** Variable Window | **Companies:** Google, Amazon, Meta

**Hint:** A window is valid when `length - maxFreq <= k`. You do not need to recompute `maxFreq` when shrinking; letting it go stale only under-estimates, which never yields a wrong maximum.

---

### M8 · Minimum Size Subarray Sum

**🔗 [LC 209 — Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)** · Medium
**Pattern:** Variable Window (shortest) | **Companies:** Amazon, Google, Meta

**Hint:** All values are positive, so growing the window only increases the sum. Expand to reach the target, then shrink from the left while it still qualifies — record **inside** the shrink loop.

---

### M9 · Fruit Into Baskets

**🔗 [LC 904 — Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)** · Medium
**Pattern:** Variable Window | **Companies:** Google, Amazon

**Hint:** This is 'longest subarray with at most 2 distinct values' in disguise. Keep a frequency map; shrink while the map holds more than two keys.

---

### M10 · Permutation in String

**🔗 [LC 567 — Permutation in String](https://leetcode.com/problems/permutation-in-string/)** · Medium
**Pattern:** Fixed Window | **Companies:** Meta, Amazon, Microsoft

**Hint:** A permutation means identical character counts. Slide a window of size `s1.length()` over `s2` and compare two 26-slot arrays — or track a single `matches` counter for O(1) checks.

---

### M11 · Find All Anagrams in a String

**🔗 [LC 438 — Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)** · Medium
**Pattern:** Fixed Window | **Companies:** Amazon, Meta, Google

**Hint:** Identical to Permutation in String, but you record every start index instead of returning on the first hit.

---

### M12 · Max Consecutive Ones III

**🔗 [LC 1004 — Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)** · Medium
**Pattern:** Variable Window | **Companies:** Amazon, Google, Meta

**Hint:** Reframe it: the longest window containing at most k zeros. Count zeros in the window and shrink while that count exceeds k.

---

### M13 · Subarray Product Less Than K

**🔗 [LC 713 — Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/)** · Medium
**Pattern:** Variable Window + counting | **Companies:** Amazon, Google

**Hint:** Shrink while the product is ≥ k, then add `right - left + 1` — every subarray ending at `right` inside the window qualifies. Guard `k <= 1` as an early return.

---

### M14 · Maximum Number of Vowels in a Substring of Given Length

**🔗 [LC 1456 — Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)** · Medium
**Pattern:** Fixed Window | **Companies:** Amazon, Microsoft

**Hint:** Classic roll: add the incoming character's vowel-ness, subtract the outgoing one. No map required, just an integer.

---

### M15 · Interval List Intersections

**🔗 [LC 986 — Interval List Intersections](https://leetcode.com/problems/interval-list-intersections/)** · Medium
**Pattern:** Two Pointers on two arrays | **Companies:** Meta, Amazon, Google

**Hint:** One pointer per list. The intersection is `[max(starts), min(ends)]`; it is real only when that start ≤ that end. Advance whichever interval ends first.

---

### M16 · Valid Triangle Number

**🔗 [LC 611 — Valid Triangle Number](https://leetcode.com/problems/valid-triangle-number/)** · Medium
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Google

**Hint:** Sort, fix the **largest** side at index `i`, then converge `lo`/`hi` below it. When `a[lo] + a[hi] > a[i]`, every index between `lo` and `hi` also works — add `hi - lo` at once.

---

## 🔴 Hard Tier (5 Problems)

_FAANG Mastery._

### H1 · Minimum Window Substring

**🔗 [LC 76 — Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)** · Hard
**Pattern:** Variable Window (shortest) | **Companies:** Meta, Amazon, Google, Uber

**Hint:** Keep a `need` map and a single `missing` counter so validity is O(1). Record the answer **inside** the shrink loop, before moving `left`. Characters outside `t` go negative and are ignored by the `> 0` guards.

---

### H2 · Trapping Rain Water

**🔗 [LC 42 — Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)** · Hard
**Pattern:** Opposite Ends | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Water above a bar is `min(leftMax, rightMax) - height`. Converge from both ends: whichever side is shorter is the binding constraint, so its water is already decided — settle it and step inwards. O(1) space.

---

### H3 · Subarrays with K Different Integers

**🔗 [LC 992 — Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/)** · Hard
**Pattern:** At-Most Trick | **Companies:** Google, Amazon, Meta

**Hint:** 'Exactly k' is not monotonic, so a window cannot answer it directly. Use `exactly(k) = atMost(k) - atMost(k-1)` and write the at-most window once.

---

### H4 · Minimum Number of K Consecutive Bit Flips

**🔗 [LC 995 — Minimum Number of K Consecutive Bit Flips](https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips/)** · Hard
**Pattern:** Sliding Window of Flips | **Companies:** Google, Amazon

**Hint:** Greedy left to right: if the current bit, after the flips affecting it, is 0, you must start a flip here. Track active flips with a queue or a difference array, and expire flips that started `k` positions ago.

---

### H5 · Substring with Concatenation of All Words

**🔗 [LC 30 — Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)** · Hard
**Pattern:** Fixed Window on word blocks | **Companies:** Amazon, Meta, Google

**Hint:** Slide in steps of one **word length**, not one character, and run `wordLen` separate passes so every alignment is covered. Each pass is an ordinary variable window over whole words.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — two pointers from both ends of a sorted array

// Snippet 2
for i from 0 to n - 1:
    for j from i to n - 1:
        check window [i, j]

// Snippet 3 — variable-size sliding window (expand right, shrink left)

// Snippet 4 — fixed-size window of k, recomputing each window's sum

// Snippet 5 — fixed-size window of k, updating the sum as it slides

// Snippet 6 — 3Sum: sort, then two pointers for each element
```

**Complexity Answers:**

1. **O(n)** — each pointer moves at most n times.
2. **O(n²)** windows.
3. **O(n)** — each index enters and leaves the window once.
4. **O(n · k)**.
5. **O(n)**.
6. **O(n²)** — O(n log n) sort plus n passes of O(n).

---

## 🔍 Self-Assessment — True / False

1. A sliding window with a nested while loop is O(n²). → **False** — each element is added once and removed once: O(n)
2. Two pointers from both ends need a sorted array (or a similar monotonic property). → **True** — that is what makes moving one pointer safe
3. A sliding window works for "longest subarray with sum ≤ k" even with negative numbers. → **False** — negatives break the shrinking rule; use prefix sums
4. "Exactly k" can be computed as "at most k" minus "at most k − 1". → **True** — the at-most trick
5. Fast and slow pointers can remove duplicates in place in O(1) space. → **True**
6. A fixed-size window must recompute its sum each step. → **False** — add the new element, subtract the one leaving

---

## 🧠 Conceptual Check

1. **Why is the expand/shrink template O(n) despite two nested loops?**
2. **Longest vs shortest:** where does the answer get recorded in each, and why?
3. **Why must the shrink step be a `while` and not an `if`?**
4. **Why does `exactly(k) = atMost(k) - atMost(k-1)` work?** What property of "at most" makes it windowable?
5. **Why do sliding windows fail on arrays containing negatives?** What replaces them?
6. **In Container With Most Water, why is moving the taller wall provably useless?**
7. **In 3Sum, why must the array be sorted before deduplicating?**

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Minimum Number of K Consecutive Bit Flips](https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips/), [Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/), [Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/), [Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/) |
| **Google**    | [Valid Triangle Number](https://leetcode.com/problems/valid-triangle-number/), [Defuse the Bomb](https://leetcode.com/problems/defuse-the-bomb/), [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/), [Minimum Number of K Consecutive Bit Flips](https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips/)                                                                               |
| **Meta**      | [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/), [Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/), [Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/), [3Sum Closest](https://leetcode.com/problems/3sum-closest/)                                                             |
| **Microsoft** | [Reverse String II](https://leetcode.com/problems/reverse-string-ii/), [Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/), [Permutation in String](https://leetcode.com/problems/permutation-in-string/), [Move Zeroes](https://leetcode.com/problems/move-zeroes/)                                                                             |
| **Adobe**     | [Remove Element](https://leetcode.com/problems/remove-element/), [Substrings of Size Three with Distinct Characters](https://leetcode.com/problems/substrings-of-size-three-with-distinct-characters/), [4Sum](https://leetcode.com/problems/4sum/), [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)                                                                                 |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 7 conceptual questions answered out loud
- [ ] I can write the variable-window template from memory
- [ ] I can name the shape for any new problem within 30 seconds

---

**← [Lecture 24 · Backtracking — Systematic Search](../Lecture24/Assignment.md)** &nbsp;·&nbsp; **[Lecture 26 · Prefix Sums & Difference Arrays](../Lecture26/Assignment.md) →**
