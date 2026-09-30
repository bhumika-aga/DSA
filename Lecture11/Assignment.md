# 📋 Assignment 11 — Arrays & Strings

> **Lecture:** 11 of 45 — Arrays & Strings
> **Phase:** 2 — Core Data Structures
> **Estimated Time:** 7 days · **Total Problems:** 35 (10 Easy · 20 Medium · 5 Hard)
> **Goal:** Master in-place modifications, Kadane's algorithm, prefix sums, and frequency mappings without resorting to
> O(n²) or heavy HashMaps.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                | Pattern               | Move                           |
| ------------------------------------ | --------------------- | ------------------------------ |
| "sum of a subarray / range"          | Prefix Sum            | `prefix[r+1] - prefix[l]`      |
| "maximum subarray"                   | Kadane's Algorithm    | extend the run or restart it   |
| "in place", "O(1) extra space"       | Read / Write Pointers | one pointer reads, one writes  |
| "anagram", "same letters"            | Frequency Array       | `int[26]` counts               |
| "palindrome inside a string"         | Expand Around Center  | grow outward from every center |
| "rotate / reverse part of the array" | Reversal Trick        | reverse whole, then the parts  |

---

## 🟢 Easy Tier (10 Problems)

_Build the Foundation._

### E1 · Range Sum Query - Immutable

**🔗 [LC 303 — Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/)** · Easy
**Pattern:** Prefix Sum | **Companies:** Amazon, Meta, Google

**Hint:** Precompute `prefix[i + 1] = prefix[i] + nums[i]` in the constructor. Then `sumRange(l, r) = prefix[r + 1] - prefix[l]` in O(1). The extra leading 0 removes every edge case.

---

### E2 · Find Pivot Index

**🔗 [LC 724 — Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)** · Easy
**Pattern:** Prefix Sum · Left/Right Balance | **Companies:** Amazon, Google, Meta

**Hint:** Find the index where the sum of all numbers strictly to the left equals the sum to the right. Tip: `rightSum = totalSum - leftSum - nums[i]`. O(n) time, O(1) space.

---

### E3 · Valid Anagram

**🔗 [LC 242 — Valid Anagram](https://leetcode.com/problems/valid-anagram/)** · Easy
**Pattern:** Frequency Array | **Companies:** Amazon, Meta, Bloomberg

**Hint:** Return true if `t` is an anagram of `s`. Do NOT use `HashMap`. Use an `int[26]` frequency array. O(n) time, O(1) space.

---

### E4 · Replace Elements with Greatest Element on Right Side

**🔗 [LC 1299 — Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/)** · Easy
**Pattern:** Right-to-Left Scan | **Companies:** Amazon, Google

**Hint:** Walk from the right, carrying `maxRight` (starting at -1). At each index, store `maxRight`, then update it with the old value. One pass, in place.

---

### E5 · First Unique Character in a String

**🔗 [LC 387 — First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)** · Easy
**Pattern:** Frequency Array | **Companies:** Amazon, Google, Microsoft

**Hint:** Return the index of the first non-repeating character in a string. Use a frequency array to count occurrences before a second pass to find the answer. O(n) time.

---

### E6 · Majority Element

**🔗 [LC 169 — Majority Element](https://leetcode.com/problems/majority-element/)** · Easy
**Pattern:** Boyer-Moore Voting Algorithm | **Companies:** Amazon, Google, Adobe

**Hint:** Find the element appearing > n/2 times. Maintain a candidate and count to solve in O(n) time and O(1) space.

---

### E7 · Rotate String

**🔗 [LC 796 — Rotate String](https://leetcode.com/problems/rotate-string/)** · Easy
**Pattern:** String Concatenation Trick | **Companies:** Google, Amazon

**Hint:** Check if string `s` can become `t` after some number of shifts. Hint: Is `t` a substring of `s + s`?

---

### E8 · Check If Two String Arrays are Equivalent

**🔗 [LC 1662 — Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)** · Easy
**Pattern:** Two-Level Pointers | **Companies:** Amazon, Meta

**Hint:** Concatenating is easy. The O(1)-space version keeps two pointers per side (word index, char index) and compares character by character.

---

### E9 · Add Strings

**🔗 [LC 415 — Add Strings](https://leetcode.com/problems/add-strings/)** · Easy
**Pattern:** Digit-by-Digit Addition | **Companies:** Meta, Google, Amazon

**Hint:** Walk both strings from the end with a carry, appending `(a + b + carry) % 10` to a `StringBuilder`, then reverse it. Keep looping while either string has digits left or `carry > 0`.

---

### E10 · Best Time to Buy and Sell Stock

**🔗 [LC 121 — Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)** · Easy
**Pattern:** Kadane’s Cousin | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** (Wait, this is often Easy, but we'll include it here for continuity). Track `minPrice` to find the maximum possible profit.

---

## 🟡 Medium Tier (20 Problems)

_Core Pattern Mastery._

### M1 · Maximum Subarray

**🔗 [LC 53 — Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)** · Medium
**Pattern:** Kadane's Algorithm | **Companies:** Google, Amazon, LinkedIn, Microsoft

**Hint:** Find the contiguous subarray which has the largest sum. Key insight: If `currentMax` becomes negative, reset it. O(n) time, O(1) space.

---

### M2 · Number of Ways to Split Array

**🔗 [LC 2270 — Number of Ways to Split Array](https://leetcode.com/problems/number-of-ways-to-split-array/)** · Medium
**Pattern:** Prefix Sum | **Companies:** Amazon, Google

**Hint:** Total sum once, then a running left sum. Split `i` is valid when `left >= total - left`. Use `long` — the sums overflow `int`.

---

### M3 · Rearrange Array Elements by Sign

**🔗 [LC 2149 — Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/)** · Medium
**Pattern:** Two Write Pointers | **Companies:** Amazon, Microsoft

**Hint:** Allocate the result array, then place positives at even indices and negatives at odd ones with two pointers `pos = 0`, `neg = 1` moving in steps of 2. Relative order is preserved.

---

### M4 · Rotate Array

**🔗 [LC 189 — Rotate Array](https://leetcode.com/problems/rotate-array/)** · Medium
**Pattern:** In-Place Reversals | **Companies:** Amazon, Microsoft, Google

**Hint:** Rotate an array to the right by `k` steps in O(1) extra space using the reversal trick: reverse all → reverse first k → reverse rest.

---

### M5 · Next Permutation

**🔗 [LC 31 — Next Permutation](https://leetcode.com/problems/next-permutation/)** · Medium
**Pattern:** Array Scanning / Math | **Companies:** Google, Amazon, Meta, Microsoft

**Hint:** Find the next lexicographically greater permutation. Trace backwards to find the first dip, swap, and reverse the tail. O(n) time.

---

### M6 · Product of Array Except Self

**🔗 [LC 238 — Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)** · Medium
**Pattern:** Prefix / Suffix Products | **Companies:** Amazon, Meta, Microsoft

**Hint:** Return an array where `answer[i]` is the product of all elements except `nums[i]`, without using the division operator. O(n) time.

---

### M7 · Maximum Sum Circular Subarray

**🔗 [LC 918 — Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)** · Medium
**Pattern:** Advanced Kadane's | **Companies:** Amazon, Google, Meta

**Hint:** Max sub-sum is either `Kadane_Max(nums)` or `Total_Sum - Kadane_Min(nums)`. Be careful when all numbers are negative!

---

### M8 · Determine if Two Strings Are Close

**🔗 [LC 1657 — Determine if Two Strings Are Close](https://leetcode.com/problems/determine-if-two-strings-are-close/)** · Medium
**Pattern:** Frequency Arrays | **Companies:** Amazon, Google, Microsoft

**Hint:** The two operations mean both strings must use the same set of letters, and their sorted frequency lists must match. Compare the presence of each letter, then sort both `int[26]` count arrays and compare.

---

### M9 · Rotating the Box

**🔗 [LC 1861 — Rotating the Box](https://leetcode.com/problems/rotating-the-box/)** · Medium
**Pattern:** Matrix Rotation + Gravity | **Companies:** Amazon, Google

**Hint:** First apply gravity in each row: scan right to left keeping the lowest free slot, moving stones there and resetting at obstacles. Then rotate 90° clockwise: `result[j][m - 1 - i] = box[i][j]`.

---

### M10 · Range Sum Query 2D - Immutable

**🔗 [LC 304 — Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/)** · Medium
**Pattern:** 2D Prefix Sums | **Companies:** Google, Amazon, Meta

**Hint:** Precompute a 2D prefix sum to answer any sub-rectangle query in O(1) using the `+ - - +` formula.

---

### M11 · Insert Interval

**🔗 [LC 57 — Insert Interval](https://leetcode.com/problems/insert-interval/)** · Medium
**Pattern:** Array Iteration / Intersections | **Companies:** Google, Amazon, Meta, LinkedIn

**Hint:** Insert an interval into a sorted array of non-overlapping intervals and merge if necessary. O(n) time.

---

### M12 · Reorder Data in Log Files

**🔗 [LC 937 — Reorder Data in Log Files](https://leetcode.com/problems/reorder-data-in-log-files/)** · Medium
**Pattern:** Custom String Comparator | **Companies:** Amazon

**Hint:** Split each log once into an identifier and content. Letter-logs come first, sorted by content then identifier; digit-logs keep their original order. A stable sort with a comparator does it.

---

### M13 · Make Sum Divisible by P

**🔗 [LC 1590 — Make Sum Divisible by P](https://leetcode.com/problems/make-sum-divisible-by-p/)** · Medium
**Pattern:** Prefix Sum Modulo + Map | **Companies:** Amazon, Google

**Hint:** Let `need = total % p`. Scan prefix sums mod p, storing the last index of each remainder. At index `i`, look up remainder `(cur - need + p) % p` to find the shortest subarray to remove. Don't remove the whole array.

---

### M14 · Majority Element II

**🔗 [LC 229 — Majority Element II](https://leetcode.com/problems/majority-element-ii/)** · Medium
**Pattern:** Boyer-Moore Voting Extension | **Companies:** Amazon, Google, Meta

**Hint:** Find all elements that appear more than `⌊ n/3 ⌋` times using two counters. O(n) time, O(1) space.

---

### M15 · Optimal Partition of String

**🔗 [LC 2405 — Optimal Partition of String](https://leetcode.com/problems/optimal-partition-of-string/)** · Medium
**Pattern:** Greedy Scan with a Seen Mask | **Companies:** Amazon, Google

**Hint:** Walk the string keeping the letters in the current part (a 26-bit mask or boolean array). When a letter repeats, start a new part and clear the set. Greedy cutting is optimal.

---

### M16 · Change Minimum Characters to Satisfy One of Three Conditions

**🔗 [LC 1737 — Change Minimum Characters to Satisfy One of Three Conditions](https://leetcode.com/problems/change-minimum-characters-to-satisfy-one-of-three-conditions/)** · Medium
**Pattern:** Prefix Counts over the Alphabet | **Companies:** Google

**Hint:** Count letters of `a` and `b` in `int[26]`. For conditions 1 and 2, try every split letter `c` from 'b' to 'z': the cost is the letters of `a` that are `>= c` plus the letters of `b` that are `< c` (prefix sums over counts), and the same the other way round. For condition 3, the cost is `len(a) + len(b) - max(countA[x] + countB[x])`.

---

### M17 · Longest Mountain in Array

**🔗 [LC 845 — Longest Mountain in Array](https://leetcode.com/problems/longest-mountain-in-array/)** · Medium
**Pattern:** Up / Down Run Counting | **Companies:** Google, Amazon

**Hint:** Track `up` and `down` lengths. Reset both at a plateau, or when you start going up again after a descent. A mountain exists when both are > 0, with length `up + down + 1`.

---

### M18 · Longest Palindromic Substring

**🔗 [LC 5 — Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)** · Medium
**Pattern:** Expand Around Center | **Companies:** Amazon, Microsoft, Google

**Hint:** Every palindrome has a center — a character or the gap between two. Expand outward from all `2n - 1` centers while the ends match, and keep the longest. O(n²) time, O(1) space.

---

### M19 · String Compression

**🔗 [LC 443 — String Compression](https://leetcode.com/problems/string-compression/)** · Medium
**Pattern:** Read / Write Pointers | **Companies:** Microsoft, Amazon, Goldman Sachs

**Hint:** `read` scans each run of equal chars; `write` writes the char, then the run length's digits if it's > 1. Everything happens in place, and you return `write`.

---

### M20 · Decrease Elements To Make Array Zigzag

**🔗 [LC 1144 — Decrease Elements To Make Array Zigzag](https://leetcode.com/problems/decrease-elements-to-make-array-zigzag/)** · Medium
**Pattern:** Try Both Parities | **Companies:** Google

**Hint:** Try both shapes: odd indices are valleys, or even indices are valleys. For each valley, the cost is `max(0, nums[i] - min(neighbours) + 1)`. Return the cheaper of the two totals.

---

## 🔴 Hard Tier (5 Problems)

_10 Advanced Problems._

### H1 · Candy

**🔗 [LC 135 — Candy](https://leetcode.com/problems/candy/)** · Hard
**Pattern:** Two-Pass Prefix / Suffix | **Companies:** Amazon, Google, Microsoft

**Hint:** Left pass: `candy[i] = candy[i-1] + 1` if the rating goes up. Right pass: `candy[i] = max(candy[i], candy[i+1] + 1)` if the rating goes down. Sum the result.

---

### H2 · Text Justification

**🔗 [LC 68 — Text Justification](https://leetcode.com/problems/text-justification/)** · Hard
**Pattern:** String Simulation | **Companies:** Google, Amazon, Microsoft

**Hint:** Greedily take as many words as fit with single spaces. Spread the extra spaces left-heavy: `extra / gaps` in each gap, with the first `extra % gaps` gaps getting one more. The last line and single-word lines are left-justified.

---

### H3 · Max Sum of Rectangle No Larger Than K

**🔗 [LC 363 — Max Sum of Rectangle No Larger Than K](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)** · Hard
**Pattern:** Kadane's on 2D + Sorted Prefix Sums | **Companies:** Google, Amazon

**Hint:** Fix a pair of rows (or columns), collapse the columns between them into a 1D array of sums, and find the best subarray sum ≤ k using a `TreeSet` of prefix sums (`ceiling(prefix - k)`). Unconstrained, this is 2D Kadane's.

---

### H4 · Shortest Palindrome

**🔗 [LC 214 — Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/)** · Hard
**Pattern:** Rolling Hash / KMP | **Companies:** Google, Amazon, Meta

**Hint:** The answer is `reverse(suffix) + s`, where the kept prefix is the longest palindromic prefix of `s`. Find it with KMP: build the failure function of `s + "#" + reverse(s)`; its last value is that prefix's length.

---

### H5 · Valid Number

**🔗 [LC 65 — Valid Number](https://leetcode.com/problems/valid-number/)** · Hard
**Pattern:** Parsing / State Tracking | **Companies:** LinkedIn, Meta, Amazon

**Hint:** Scan once with flags `seenDigit`, `seenDot`, `seenExp`. A sign is only legal at the start or right after `e`. A dot can't come after `e`. After `e` you must see digits again.

---

## 📊 Complexity Analysis Exercises

Determine **Time** and **Space** complexity for each. Answers below.

```pseudocode
// Snippet A — Sorting colors
counts ← [0, 0, 0]
for x in nums: counts[x] ← counts[x] + 1
i ← 0
for c from 0 to 2:
    repeat counts[c] times:
        nums[i] ← c
        i ← i + 1

// Snippet B — Matrix operations
for i from 0 to n - 1:
    for j from i + 1 to n - 1:
        swap matrix[i][j], matrix[j][i]

// Snippet C — String build
res ← ""                              // immutable string
for i from 0 to n - 1:
    res ← res + s[i]                  // creates a new string each time

// Snippet D — Sliding window
l ← 0;  sum ← 0
for r from 0 to n - 1:
    sum ← sum + nums[r]
    while sum > k:
        sum ← sum - nums[l]
        l ← l + 1

// Snippet E — Prefix lookup
map ← empty map;  curr ← 0;  res ← 0
for x in nums:
    curr ← curr + x
    if (curr - k) in map: res ← res + map[curr - k]
    map[curr] ← (map[curr] if curr in map, else 0) + 1
```

**Answers:**

| Snippet | Time  | Space | Key Insight                                                         |
| :------ | :---- | :---- | :------------------------------------------------------------------ |
| **A**   | O(N)  | O(1)  | Two passes (counting and filling); fixed size 3 aux array.          |
| **B**   | O(N²) | O(1)  | Nested loops over n\*n/2 elements.                                  |
| **C**   | O(N²) | O(N)  | String immutability leads to object copying in every iteration.     |
| **D**   | O(N)  | O(1)  | Both pointers `l` and `r` traverse each element at most once.       |
| **E**   | O(N)  | O(N)  | HashMap operations are O(1) avg; O(N) space for unique prefix sums. |

---

## 🔍 Self-Assessment — True / False

1. `arr[mid] - 'a'` is a valid way to map lowercase English characters to integers 0–25. → **True**
2. Kadane's algorithm is only applicable if the array contains at least one positive number. → **False** (It works for
   all-negative arrays by tracking max directly).
3. `StringBuilder` is faster than `String` concatenations because it avoids repeated object copies. → **True**
4. Rolling hash allows us to update the hash of a sliding window in O(1) time. → **True**
5. A 2D Prefix Sum array requires an additional O(N²) space. → **True**
6. Finding the majority element using Boyer-Moore requires sorting the array first. → **False** (One pass, O(1) space).

---

## 🧠 Conceptual Check

1. Explain the "baggage reset" intuition in Kadane’s algorithm. When do we decide to start a new subarray?
2. Compare a mapping using `int[26]` and `HashMap<Character, Integer>`. When is the array strictly better?
3. Why does swapping a `2` with the `high` index in Sort Colors (DNF) NOT allow us to increment the `mid` pointer
   immediately?
4. How do prefix sums convert O(N) range queries into O(1) operations? What is the tradeoff?
5. Describe the "Reversal Trick" for rotating an array. Why does it work?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Reorder Data in Log Files](https://leetcode.com/problems/reorder-data-in-log-files/), [Longest Mountain in Array](https://leetcode.com/problems/longest-mountain-in-array/), [Max Sum of Rectangle No Larger Than K](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/), [String Compression](https://leetcode.com/problems/string-compression/)                                                                                           |
| **Google**    | [Change Minimum Characters to Satisfy One of Three Conditions](https://leetcode.com/problems/change-minimum-characters-to-satisfy-one-of-three-conditions/), [Decrease Elements To Make Array Zigzag](https://leetcode.com/problems/decrease-elements-to-make-array-zigzag/), [Make Sum Divisible by P](https://leetcode.com/problems/make-sum-divisible-by-p/), [Number of Ways to Split Array](https://leetcode.com/problems/number-of-ways-to-split-array/) |
| **Meta**      | [Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/), [Valid Anagram](https://leetcode.com/problems/valid-anagram/), [Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/), [Valid Number](https://leetcode.com/problems/valid-number/)                                                                                                                                   |
| **Microsoft** | [Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/), [String Compression](https://leetcode.com/problems/string-compression/), [Candy](https://leetcode.com/problems/candy/), [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)                                                                                                                                     |
| **LinkedIn**  | [Valid Number](https://leetcode.com/problems/valid-number/), [Insert Interval](https://leetcode.com/problems/insert-interval/), [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)                                                                                                                                                                                                                                                            |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 20 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can explain why `StringBuilder` beats `String +=` inside a loop
- [ ] I can build a prefix-sum array and answer range queries in O(1)

---

**← [Lecture 10 · Mathematics for DSA](../Lecture10/Assignment.md)** &nbsp;·&nbsp; **[Lecture 12 · Sorting Algorithms](../Lecture12/Assignment.md) →**
