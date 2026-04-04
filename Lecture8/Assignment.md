# 📝 Assignment 08 — Arrays & Strings

> **Lecture:** Topic 8 — Arrays & Strings
> **Topic Count:** 8 of 30 — Phase 2 Data Structures
> **Duration:** 6 Days
> **Core Problems:** 35 (10 Easy · 15 Medium · 10 Challenge) + 5 Complexity Exercises
> **Goal:** Master in-place modifications, Kadane's algorithm, prefix sums, and frequency mappings without resorting to O(n²) or heavy HashMaps.

---

## 🟢 Easy Tier — 10 Problems (Build the Foundation)

---

### Problem 01 — Running Sum of 1d Array

> 🔗 **LeetCode:** [1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)
> **`[Pattern: Prefix Sum Basics]` `[Amazon] [Microsoft]` `[Easy]`**
> Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`. Return the running sum of `nums`. Modify the array in-place for O(1) space. O(n) time.

### Problem 02 — Find Pivot Index

> 🔗 **LeetCode:** [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)
> **`[Pattern: Prefix Sum · Left/Right Balance]` `[Amazon] [Apple]` `[Easy]`**
> Find the index where the sum of all numbers strictly to the left equals the sum to the right. Tip: `rightSum = totalSum - leftSum - nums[i]`. O(n) time, O(1) space.

### Problem 03 — Valid Anagram

> 🔗 **LeetCode:** [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)
> **`[Pattern: Frequency Array]` `[Google] [Amazon] [Microsoft]` `[Easy]`**
> Return true if `t` is an anagram of `s`. Do NOT use `HashMap`. Use an `int[26]` frequency array. O(n) time, O(1) space.

### Problem 04 — Move Zeroes

> 🔗 **LeetCode:** [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)
> **`[Pattern: In-Place Swaps (Two Pointers)]` `[Facebook] [Apple]` `[Easy]`**
> Move all 0's to the end while maintaining the relative order of non-zero elements. Use a write-pointer to place non-zeros sequentially. O(n) time, O(1) space.

### Problem 05 — First Unique Character in a String

> 🔗 **LeetCode:** [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
> **`[Pattern: Frequency Array]` `[Amazon] [Microsoft]` `[Easy]`**
> Return the index of the first non-repeating character in a string. Use a frequency array to count occurrences before a second pass to find the answer. O(n) time.

### Problem 06 — Maximum Subarray (Kadane's intro)

> 🔗 **LeetCode:** [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
> **`[Pattern: Kadane's Algorithm]` `[Amazon] [Google]` `[Easy-Medium]`**
> Find the contiguous subarray which has the largest sum. Key insight: If `currentMax` becomes negative, reset it. O(n) time, O(1) space.

### Problem 07 — Majority Element

> 🔗 **LeetCode:** [169. Majority Element](https://leetcode.com/problems/majority-element/)
> **`[Pattern: Boyer-Moore Voting Algorithm]` `[Amazon] [Apple] [Easy]`**
> Find the element appearing > n/2 times. Maintain a candidate and count to solve in O(n) time and O(1) space.

### Problem 08 — Rotate String

> 🔗 **LeetCode:** [796. Rotate String](https://leetcode.com/problems/rotate-string/)
> **`[Pattern: String Concatenation Trick]` `[LinkedIn] [Easy]`**
> Check if string `s` can become `t` after some number of shifts. Hint: Is `t` a substring of `s + s`?

### Problem 09 — Shuffle the Array

> 🔗 **LeetCode:** [1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)
> **`[Pattern: Index Arithmetic]` `[Easy]`**
> Interleave an array like [x1, x2, ..., y1, y2, ...] → [x1, y1, x2, y2, ...]. Solve in O(n) time.

### Problem 10 — Plus One

> 🔗 **LeetCode:** [66. Plus One](https://leetcode.com/problems/plus-one/)
> **`[Pattern: Carry Propagation]` `[Google] [Amazon] [Easy]`**
> Add one to a number represented as a digit array. Handle the carry propagation and the edge case where an extra digit is needed (e.g., [9, 9] -> [1, 0, 0]).

---

## 🟡 Medium Tier — 15 Problems (Core Pattern Mastery)

---

### Problem 11 — Subarray Sum Equals K

> 🔗 **LeetCode:** [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
> **`[Pattern: Prefix Sum + HashMap Cache]` `[Facebook] [Amazon] [Google] [Medium]`**
> Return the total number of continuous subarrays whose sum equals to `k`. Store past prefix sums and their frequencies in a map. O(n) time.

### Problem 12 — Sort Colors (Dutch National Flag)

> 🔗 **LeetCode:** [75. Sort Colors](https://leetcode.com/problems/sort-colors/)
> **`[Pattern: Three Pointers (Dutch National Flag)]` `[Microsoft] [Amazon] [Medium]`**
> Sort an array with 0s, 1s, and 2s in-place in a single pass using `low`, `mid`, and `high` pointers. O(n) time, O(1) space.

### Problem 13 — Rotate Array

> 🔗 **LeetCode:** [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
> **`[Pattern: In-Place Reversals]` `[Amazon] [Microsoft] [Medium]`**
> Rotate an array to the right by `k` steps in O(1) extra space using the reversal trick: reverse all → reverse first k → reverse rest.

### Problem 14 — Next Permutation

> 🔗 **LeetCode:** [31. Next Permutation](https://leetcode.com/problems/next-permutation/)
> **`[Pattern: Array Scanning / Math]` `[Google] [Facebook] [Medium]`**
> Find the next lexicographically greater permutation. Trace backwards to find the first dip, swap, and reverse the tail. O(n) time.

### Problem 15 — Product of Array Except Self

> 🔗 **LeetCode:** [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
> **`[Pattern: Prefix / Suffix Products]` `[Amazon] [Apple] [Medium]`**
> Return an array where `answer[i]` is the product of all elements except `nums[i]`, without using the division operator. O(n) time.

### Problem 16 — Best Time to Buy and Sell Stock

> 🔗 **LeetCode:** [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
> **`[Pattern: Kadane’s Cousin]` `[Amazon] [Microsoft] [Medium]`**
> (Wait, this is often Easy, but we'll include it here for continuity). Track `minPrice` to find the maximum possible profit.

### Problem 17 — Maximum Circular Subarray Sum

> 🔗 **LeetCode:** [918. Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)
> **`[Pattern: Advanced Kadane's]` `[Amazon] [Medium]`**
> Max sub-sum is either `Kadane_Max(nums)` or `Total_Sum - Kadane_Min(nums)`. Be careful when all numbers are negative!

### Problem 18 — Group Anagrams

> 🔗 **LeetCode:** [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)
> **`[Pattern: Frequency Array as HashMap Key]` `[Amazon] [Microsoft] [Medium]`**
> Group strings by character frequencies. Tip: Use a delimited string from a freq array as the key instead of sorting (O(N*K) vs O(N*K log K)).

### Problem 19 — Rotate Image (2D Rotation)

> 🔗 **LeetCode:** [48. Rotate Image](https://leetcode.com/problems/rotate-image/)
> **`[Pattern: Matrix Transposition & Reversal]` `[Amazon] [Google] [Medium]`**
> Rotate an `n x n` matrix clockwise in-place. Formula: `transpose(matrix)` then `reverse(each row)`. O(n²) time.

### Problem 20 — Range Sum Query 2D (Immutable)

> 🔗 **LeetCode:** [304. Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/)
> **`[Pattern: 2D Prefix Sums]` `[Facebook] [Google] [Medium]`**
> Precompute a 2D prefix sum to answer any sub-rectangle query in O(1) using the `+ - - +` formula.

### Problem 21 — Insert Interval

> 🔗 **LeetCode:** [57. Insert Interval](https://leetcode.com/problems/insert-interval/)
> **`[Pattern: Array Iteration / Intersections]` `[Google] [Microsoft] [Medium]`**
> Insert an interval into a sorted array of non-overlapping intervals and merge if necessary. O(n) time.

### Problem 22 — Largest Number

> 🔗 **LeetCode:** [179. Largest Number](https://leetcode.com/problems/largest-number/)
> **`[Pattern: Custom String Sorting]` `[Amazon] [Google] [Medium]`**
> Sort numbers by comparing string concatenations `(a+b)` vs `(b+a)`. O(n log n) time.

### Problem 23 — Subarray Sums Divisible by K

> 🔗 **LeetCode:** [974. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
> **`[Pattern: Prefix Sum + Modulo Math]` `[Microsoft] [Medium]`**
> Count subarrays whose sum is divisible by `k`. Use `(sum % k + k) % k` to handle negative remainders in Java.

### Problem 24 — Majority Element II

> 🔗 **LeetCode:** [229. Majority Element II](https://leetcode.com/problems/majority-element-ii/)
> **`[Pattern: Boyer-Moore Voting Extension]` `[Amazon] [Medium]`**
> Find all elements that appear more than `⌊ n/3 ⌋` times using two counters. O(n) time, O(1) space.

### Problem 25 — Top K Frequent Elements

> 🔗 **LeetCode:** [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
> **`[Pattern: Frequency Map -> Bucket Sort]` `[Amazon] [Google] [Medium]`**
> Given an array and integer `k`, return the `k` most frequent elements in `O(n)` using Bucket Sort on frequency.

---

## 🔴 Challenge Zone — 10 Advanced Problems

---

- **P26: Trapping Rain Water** ([LC 42](https://leetcode.com/problems/trapping-rain-water/)) `[Pattern: Prefix / Suffix Max]` — Amazon Hard
- **P27: First Missing Positive** ([LC 41](https://leetcode.com/problems/first-missing-positive/)) `[Pattern: Cyclic Sort / In-place Hashing]` — Microsoft Hard
- **P28: Maximum Sum Submatrix** ([Practice GFG](https://www.geeksforgeeks.org/maximum-sum-rectangle-in-a-2d-matrix-dp-27/)) `[Pattern: Kadane’s on 2D]`
- **P29: Shortest Palindrome** ([LC 214](https://leetcode.com/problems/shortest-palindrome/)) `[Pattern: Rolling Hash / KMP]`
- **P30: String Transforms Into Another String** ([LC 1153](https://leetcode.com/problems/string-transforms-into-another-string/)) `[Pattern: Character Mapping]`
- **P31: 3Sum** ([LC 15](https://leetcode.com/problems/3sum/)) `[Pattern: Sort + Two Pointers]`
- **P32: Container With Most Water** ([LC 11](https://leetcode.com/problems/container-with-most-water/)) `[Pattern: Two Pointers (Converging)]`
- **P33: Game of Life** ([LC 289](https://leetcode.com/problems/game-of-life/)) `[Pattern: In-Place State Transformation]`
- **P34: Longest Substring Without Repeating Characters** ([LC 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/)) `[Pattern: Sliding Window]`
- **P35: Wiggle Sort II** ([LC 324](https://leetcode.com/problems/wiggle-sort-ii/)) `[Pattern: Virtual Indexing]`

---

## 📊 Complexity Analysis Exercises — 5 Snippets

Determine **Time** and **Space** complexity for each. Answers below.

```java
// Snippet A — Sorting colors
int[] counts = new int[3];
for(int x : nums) counts[x]++;
int i = 0;
for(int c = 0; c < 3; c++)
    while(counts[c]-- > 0) nums[i++] = c;

// Snippet B — Matrix operations
for (int i = 0; i < n; i++)
    for (int j = i + 1; j < n; j++)
        swap(matrix[i][j], matrix[j][i]);

// Snippet C — String build
String res = "";
for (int i = 0; i < n; i++)
    res += s.charAt(i);

// Snippet D — Sliding window
int l = 0, sum = 0;
for (int r = 0; r < n; r++) {
    sum += nums[r];
    while (sum > k) sum -= nums[l++];
}

// Snippet E — Prefix lookup
Map<Integer, Integer> map = new HashMap<>();
for (int x : nums) {
    curr += x;
    if (map.containsKey(curr - k)) res += map.get(curr - k);
    map.put(curr, map.getOrDefault(curr, 0) + 1);
}
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

## ✅ Self-Assessment — True / False

1. `arr[mid] - 'a'` is a valid way to map lowercase English characters to integers 0–25. → **True**
2. Kadane's algorithm is only applicable if the array contains at least one positive number. → **False** (It works for all-negative arrays by tracking max directly).
3. `StringBuilder` is faster than `String` concatenations because it avoids repeated object copies. → **True**
4. Rolling hash allows us to update the hash of a sliding window in O(1) time. → **True**
5. A 2D Prefix Sum array requires an additional O(N²) space. → **True**
6. Finding the majority element using Boyer-Moore requires sorting the array first. → **False** (One pass, O(1) space).

---

## 🧠 Conceptual Questions

1. Explain the "baggage reset" intuition in Kadane’s algorithm. When do we decide to start a new subarray?
2. Compare a mapping using `int[26]` and `HashMap<Character, Integer>`. When is the array strictly better?
3. Why does swapping a `2` with the `high` index in Sort Colors (DNF) NOT allow us to increment the `mid` pointer immediately?
4. How do prefix sums convert O(N) range queries into O(1) operations? What is the tradeoff?
5. Describe the "Reversal Trick" for rotating an array. Why does it work?

---

Next: Topic 9 — Binary Search. Master the log(n) searching variants and "BS on Answer" patterns.\_
