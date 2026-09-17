# 🎯 Assignment 18 — Two Pointers & Sliding Window

> **Lecture:** 18 of 38 — Two Pointers & Sliding Window
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 6 days · **Total Problems:** 30 (10 Easy · 15 Medium · 5 Hard)
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
> invalid window valid again. Negative numbers break this. Those are prefix-sum problems (Lecture 19).

---

## 🟢 Easy Tier (10 Problems)

### E1 · Two Sum II — Input Array Is Sorted

**🔗 [LC 167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)**
**Pattern:** Opposite Ends | **Companies:** Amazon, Google, Adobe

**Hint:** Sorted input is the clue. Start at both ends; move `lo` right when the sum is too small, `hi` left when it is too big. O(1) space — no HashMap needed.

---

### E2 · Valid Palindrome

**🔗 [LC 125](https://leetcode.com/problems/valid-palindrome/)**
**Pattern:** Opposite Ends | **Companies:** Meta, Amazon, Microsoft

**Hint:** Two pointers converging, skipping any character that is not alphanumeric. Compare lowercase forms. The skipping happens inside the outer loop, not before it.

---

### E3 · Move Zeroes

**🔗 [LC 283](https://leetcode.com/problems/move-zeroes/)**
**Pattern:** Same Direction | **Companies:** Meta, Amazon, Microsoft

**Hint:** `slow` is a write cursor, `fast` a read cursor. Copy every non-zero forward, then fill the tail with zeros. Order of the non-zeros must be preserved.

---

### E4 · Remove Duplicates from Sorted Array

**🔗 [LC 26](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)**
**Pattern:** Same Direction | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Duplicates are adjacent because the array is sorted. Write a value only when it differs from `a[slow]`. Return `slow + 1`.

---

### E5 · Remove Element

**🔗 [LC 27](https://leetcode.com/problems/remove-element/)**
**Pattern:** Same Direction | **Companies:** Amazon, Adobe

**Hint:** Same read/write cursors as Move Zeroes, but the keep-test is `a[fast] != val`. Order does not matter here, so a swap-with-end variant also works.

---

### E6 · Reverse String

**🔗 [LC 344](https://leetcode.com/problems/reverse-string/)**
**Pattern:** Opposite Ends | **Companies:** Amazon, Microsoft, Apple

**Hint:** The simplest converging-pointer problem there is: swap `a[lo]` and `a[hi]`, step both inwards, stop when they meet.

---

### E7 · Squares of a Sorted Array

**🔗 [LC 977](https://leetcode.com/problems/squares-of-a-sorted-array/)**
**Pattern:** Opposite Ends | **Companies:** Amazon, Meta, Google

**Hint:** The largest square is at one of the two ends, never in the middle. Fill the output array **backwards** from the larger of the two.

---

### E8 · Maximum Average Subarray I

**🔗 [LC 643](https://leetcode.com/problems/maximum-average-subarray-i/)**
**Pattern:** Fixed Window | **Companies:** Amazon, Google

**Hint:** Build the first k elements, then roll: `sum += a[r] - a[r-k]`. Never rebuild the window from scratch.

---

### E9 · Substrings of Size Three with Distinct Characters

**🔗 [LC 1876](https://leetcode.com/problems/substrings-of-size-three-with-distinct-characters/)**
**Pattern:** Fixed Window | **Companies:** Amazon, Adobe

**Hint:** Window size is fixed at 3, so you can check distinctness directly. Good warm-up for keeping counts in sync as the window rolls.

---

### E10 · Defuse the Bomb

**🔗 [LC 1652](https://leetcode.com/problems/defuse-the-bomb/)**
**Pattern:** Fixed Window | **Companies:** Amazon, Google

**Hint:** A circular fixed window. Use modular indexing `(i + j) % n` rather than physically rotating the array, and handle `k < 0` by walking the other way.

---

## 🟡 Medium Tier — Core Interview Patterns (15 Problems)

### M1 · Container With Most Water

**🔗 [LC 11](https://leetcode.com/problems/container-with-most-water/)**
**Pattern:** Opposite Ends | **Companies:** Google, Amazon, Meta, Bloomberg

**Hint:** Area is width × the **shorter** wall. Width only shrinks as you converge, so always move the shorter side — moving the taller one can never improve the answer.

---

### M2 · 3Sum

**🔗 [LC 15](https://leetcode.com/problems/3sum/)**
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Meta, Google, Adobe

**Hint:** Sort, fix an anchor, run converging pointers on the rest. The difficulty is deduplication: skip repeated anchors before the inner loop, and repeated `lo`/`hi` only after recording a hit.

---

### M3 · 3Sum Closest

**🔗 [LC 16](https://leetcode.com/problems/3sum-closest/)**
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Google, Meta

**Hint:** Same skeleton as 3Sum, but instead of testing equality you track the smallest `abs(sum - target)` seen so far. No deduplication needed.

---

### M4 · 4Sum

**🔗 [LC 18](https://leetcode.com/problems/4sum/)**
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Google, Adobe

**Hint:** Two nested anchors then a converging pair — O(n³). Watch integer overflow on the sum: use `long`. Deduplicate at both anchor levels.

---

### M5 · Longest Substring Without Repeating Characters

**🔗 [LC 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/)**
**Pattern:** Variable Window | **Companies:** Amazon, Google, Meta, Bloomberg

**Hint:** Store the last index of each character. On a repeat, jump `left` forward to just past the previous copy — use `Math.max` so a stale duplicate never drags `left` backwards.

---

### M6 · Longest Repeating Character Replacement

**🔗 [LC 424](https://leetcode.com/problems/longest-repeating-character-replacement/)**
**Pattern:** Variable Window | **Companies:** Google, Amazon, Meta

**Hint:** A window is valid when `length - maxFreq <= k`. You do not need to recompute `maxFreq` when shrinking; letting it go stale only under-estimates, which never yields a wrong maximum.

---

### M7 · Minimum Size Subarray Sum

**🔗 [LC 209](https://leetcode.com/problems/minimum-size-subarray-sum/)**
**Pattern:** Variable Window (shortest) | **Companies:** Amazon, Google, Meta

**Hint:** All values are positive, so growing the window only increases the sum. Expand to reach the target, then shrink from the left while it still qualifies — record **inside** the shrink loop.

---

### M8 · Fruit Into Baskets

**🔗 [LC 904](https://leetcode.com/problems/fruit-into-baskets/)**
**Pattern:** Variable Window | **Companies:** Google, Amazon

**Hint:** This is 'longest subarray with at most 2 distinct values' in disguise. Keep a frequency map; shrink while the map holds more than two keys.

---

### M9 · Permutation in String

**🔗 [LC 567](https://leetcode.com/problems/permutation-in-string/)**
**Pattern:** Fixed Window | **Companies:** Meta, Amazon, Microsoft

**Hint:** A permutation means identical character counts. Slide a window of size `s1.length()` over `s2` and compare two 26-slot arrays — or track a single `matches` counter for O(1) checks.

---

### M10 · Find All Anagrams in a String

**🔗 [LC 438](https://leetcode.com/problems/find-all-anagrams-in-a-string/)**
**Pattern:** Fixed Window | **Companies:** Amazon, Meta, Google

**Hint:** Identical to Permutation in String, but you record every start index instead of returning on the first hit.

---

### M11 · Max Consecutive Ones III

**🔗 [LC 1004](https://leetcode.com/problems/max-consecutive-ones-iii/)**
**Pattern:** Variable Window | **Companies:** Amazon, Google, Meta

**Hint:** Reframe it: the longest window containing at most k zeros. Count zeros in the window and shrink while that count exceeds k.

---

### M12 · Subarray Product Less Than K

**🔗 [LC 713](https://leetcode.com/problems/subarray-product-less-than-k/)**
**Pattern:** Variable Window + counting | **Companies:** Amazon, Google

**Hint:** Shrink while the product is ≥ k, then add `right - left + 1` — every subarray ending at `right` inside the window qualifies. Guard `k <= 1` as an early return.

---

### M13 · Maximum Number of Vowels in a Substring of Given Length

**🔗 [LC 1456](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)**
**Pattern:** Fixed Window | **Companies:** Amazon, Microsoft

**Hint:** Classic roll: add the incoming character's vowel-ness, subtract the outgoing one. No map required, just an integer.

---

### M14 · Interval List Intersections

**🔗 [LC 986](https://leetcode.com/problems/interval-list-intersections/)**
**Pattern:** Two Pointers on two arrays | **Companies:** Meta, Amazon, Google

**Hint:** One pointer per list. The intersection is `[max(starts), min(ends)]`; it is real only when that start ≤ that end. Advance whichever interval ends first.

---

### M15 · Valid Triangle Number

**🔗 [LC 611](https://leetcode.com/problems/valid-triangle-number/)**
**Pattern:** Anchor + Converging Pair | **Companies:** Amazon, Google

**Hint:** Sort, fix the **largest** side at index `i`, then converge `lo`/`hi` below it. When `a[lo] + a[hi] > a[i]`, every index between `lo` and `hi` also works — add `hi - lo` at once.

---

## 🔴 Hard Tier — FAANG Mastery (5 Problems)

### H1 · Minimum Window Substring

**🔗 [LC 76](https://leetcode.com/problems/minimum-window-substring/)**
**Pattern:** Variable Window (shortest) | **Companies:** Meta, Amazon, Google, Uber

**Hint:** Keep a `need` map and a single `missing` counter so validity is O(1). Record the answer **inside** the shrink loop, before moving `left`. Characters outside `t` go negative and are ignored by the `> 0` guards.

---

### H2 · Trapping Rain Water

**🔗 [LC 42](https://leetcode.com/problems/trapping-rain-water/)**
**Pattern:** Opposite Ends | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Water above a bar is `min(leftMax, rightMax) - height`. Converge from both ends: whichever side is shorter is the binding constraint, so its water is already decided — settle it and step inwards. O(1) space.

---

### H3 · Subarrays with K Different Integers

**🔗 [LC 992](https://leetcode.com/problems/subarrays-with-k-different-integers/)**
**Pattern:** At-Most Trick | **Companies:** Google, Amazon, Meta

**Hint:** 'Exactly k' is not monotonic, so a window cannot answer it directly. Use `exactly(k) = atMost(k) - atMost(k-1)` and write the at-most window once.

---

### H4 · Sliding Window Maximum

**🔗 [LC 239](https://leetcode.com/problems/sliding-window-maximum/)**
**Pattern:** Monotonic Deque | **Companies:** Google, Amazon, Meta, Uber

**Hint:** A heap gives O(n log k). For O(n) keep a deque of indices in decreasing value order: pop smaller values from the back — they can never win again — and pop the front once it falls out of the window.

---

### H5 · Substring with Concatenation of All Words

**🔗 [LC 30](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)**
**Pattern:** Fixed Window on word blocks | **Companies:** Amazon, Meta, Google

**Hint:** Slide in steps of one **word length**, not one character, and run `wordLen` separate passes so every alignment is covered. Each pass is an ordinary variable window over whole words.

---

## 🧠 Conceptual Check — Answer Without Looking at Code

1. **Why is the expand/shrink template O(n) despite two nested loops?**
2. **Longest vs shortest:** where does the answer get recorded in each, and why?
3. **Why must the shrink step be a `while` and not an `if`?**
4. **Why does `exactly(k) = atMost(k) - atMost(k-1)` work?** What property of "at most" makes it windowable?
5. **Why do sliding windows fail on arrays containing negatives?** What replaces them?
6. **In Container With Most Water, why is moving the taller wall provably useless?**
7. **In 3Sum, why must the array be sorted before deduplicating?**

---

## 🏢 Company Focus

| Company   | Most Likely From This Lecture                                                    |
| --------- | -------------------------------------------------------------------------------- |
| Google    | Trapping Rain Water, Subarrays with K Different Integers, Sliding Window Maximum |
| Amazon    | 3Sum, Longest Substring Without Repeating, Minimum Size Subarray Sum             |
| Meta      | Minimum Window Substring, Valid Palindrome, Find All Anagrams                    |
| Microsoft | Permutation in String, Move Zeroes, Sliding Window Maximum                       |
| Uber      | Minimum Window Substring, Sliding Window Maximum                                 |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 5 Hard problems solved
- [ ] I can write the variable-window template from memory
- [ ] I can name the shape for any new problem within 30 seconds
- [ ] All 7 conceptual questions answered out loud
