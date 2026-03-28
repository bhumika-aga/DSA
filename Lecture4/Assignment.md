# 📝 Assignment 04 — Arrays & Strings Deep Dive

> **Lecture:** Arrays & Strings Deep Dive  
> **Builds on:** Lecture 1 (Array Basics), Lecture 3 (Bit Manipulation in Arrays)  
> **Complete before:** Lecture 5 (Sorting & Searching)  
> **Goal:** Master in-place modifications, Kadane's algorithm, prefix sums, and frequency mappings without resorting to O(n²) or heavy HashMaps.

---

## 🗺️ Problem Map by Pattern

| Pattern                      | Problems           |
| ---------------------------- | ------------------ |
| Prefix Sum Arrays (1D)       | 01, 02, 03, 04     |
| 2D Prefix Sums / Matrices    | 05, 06, 07         |
| Kadane's Algorithm           | 08, 09, 10, 11     |
| Dutch National Flag (Swaps)  | 12, 13, 14         |
| Frequency Arrays & Anagrams  | 15, 16, 17, 18, 19 |
| In-Place Reversals/Rotations | 20, 21, 22, 23     |
| Hard / FAANG-level           | 24, 25, 26, 27, 28 |
| Complexity Analysis          | 29, 30             |
| Bonus Practice               | B1–B5              |

---

## 🟢 Easy — Pattern Builders (Do ALL)

---

### Problem 01 — Running Sum of 1d Array

> 🔗 **LeetCode:** [1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

**`[Amazon] [Microsoft] [Easy]`**  
**Pattern: Prefix Sum Basics**

Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`. Return the running sum of `nums`.

```txt
Input: nums = [1,2,3,4]
Output: [1,3,6,10]
```

**Expected:** Modify the array in-place. Time O(n), Space O(1).

---

### Problem 02 — Find Pivot Index

> 🔗 **LeetCode:** [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)

**`[Amazon] [Apple] [Easy]`**  
**Pattern: Prefix Sum · Left/Right Balance**

Find the index where the sum of all numbers strictly to the left is equal to the sum of all numbers strictly to the right. If none exists, return -1.

**Key insight:** Compute `totalSum` first. Then, as you iterate, maintain a `leftSum`. The right sum is exactly `totalSum - leftSum - nums[i]`.  
**Expected:** Time O(n), Space O(1).

---

### Problem 03 — Valid Anagram

> 🔗 **LeetCode:** [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)

**`[Google] [Amazon] [Microsoft] [Easy]`**  
**Pattern: Frequency Array**

Given two strings `s` and `t`, return true if `t` is an anagram of `s`.

**Rule:** Do NOT use `HashMap`. Use an `int[26]` frequency array. Increment counts for `s`, decrement for `t`. If all spots back to 0 at the end, true.  
**Expected:** Time O(n), Space O(1).

---

### Problem 04 — Move Zeroes

> 🔗 **LeetCode:** [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

**`[Facebook] [Apple] [Easy]`**  
**Pattern: In-Place Swaps (Two Pointers prefix)**

Given an integer array `nums`, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

```txt
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Expected:** Time O(n), Space O(1). Maintain an `insertPos` tracking where the next non-zero should be placed.

---

### Problem 05 — First Unique Character in a String

> 🔗 **LeetCode:** [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)

**`[Amazon] [Microsoft] [Easy]`**  
**Pattern: Frequency Array**

Return the index of the first non-repeating character in a string.  
**Expected:** Time O(n), Space O(1) (since the alphabet size is constant at 26).

---

### Problem 06 — Maximum Subarray

> 🔗 **LeetCode:** [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

**`[Amazon] [Microsoft] [Google] [Medium-Easy]`**  
**Pattern: Kadane's Algorithm**

Find the contiguous subarray which has the largest sum and return its sum. (A classic!)

```txt
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

**Expected:** Don't do O(N²). Use Kadane's `maxEndingHere` vs `maxSoFar`. Time O(N).

---

## 🟡 Medium — Core Pattern Mastery

---

### Problem 07 — Subarray Sum Equals K

> 🔗 **LeetCode:** [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)

**`[Facebook] [Amazon] [Google] [Medium]`**  
**Pattern: Prefix Sum + HashMap Cache**

Given an array of integers `nums` and an integer `k`, return the total number of continuous subarrays whose sum equals to `k`.

**Why prefix sum + map?** If at index `i`, current prefix sum is `C`, we are looking for a previous index `j` where the prefix sum was exactly `C - k`. We store past prefix sums and their frequencies in a map.  
**Expected:** Time O(n), Space O(n).

---

### Problem 08 — Sort Colors (Dutch National Flag)

> 🔗 **LeetCode:** [75. Sort Colors](https://leetcode.com/problems/sort-colors/)

**`[Microsoft] [Amazon] [Medium]`**  
**Pattern: Three Pointers (Dutch National Flag)**

Given an array with n objects colored red(0), white(1), or blue(2), sort them **in-place** so that objects of the same color are adjacent.

**Rule:** You cannot use the library sort function. You cannot use counting sort (two passes). Do it in ONE pass.  
**Hint:** Use `low`, `mid`, and `high` pointers. Process element at `mid`.

---

### Problem 09 — Rotate Array

> 🔗 **LeetCode:** [189. Rotate Array](https://leetcode.com/problems/rotate-array/)

**`[Amazon] [Microsoft] [Microsoft] [Medium]`**  
**Pattern: In-Place Reversals**

Rotate an array to the right by `k` steps.

```txt
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
```

**Notice:** Do it in O(1) extra space.  
**The magic trick:** 1. Reverse entire array. 2. Reverse first `k` elements. 3. Reverse remaining `n-k` elements.

---

### Problem 10 — Next Permutation

> 🔗 **LeetCode:** [31. Next Permutation](https://leetcode.com/problems/next-permutation/)

**`[Google] [Facebook] [Amazon] [Medium]`**  
**Pattern: Array scanning / Math**

Find the next lexicographically greater permutation of numbers. If none exists, rearrange it to the lowest possible order (sorted ascending).

**Expected:** Time O(N), Space O(1). Trace backwards to find the first dip, find the smallest element to its right that is larger, swap them, and reverse the rest.

---

### Problem 11 — Product of Array Except Self

> 🔗 **LeetCode:** [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

**`[Amazon] [Apple] [Microsoft] [Medium]`**  
**Pattern: Prefix/Suffix Arrays**

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of nums except `nums[i]`.

**Rule:** You cannot use the division operator `/`.  
**Expected:** Compute prefix products going left-to-right, then compute suffix products going right-to-left. O(N) time, O(1) extra space (excluding the output array).

---

### Problem 12 — Best Time to Buy and Sell Stock

> 🔗 **LeetCode:** [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

**`[Amazon] [Microsoft] [Medium]`**  
**Pattern: Kadane’s Cousin (Min/Max Tracking)**

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

**Insight:** Track the `minPrice` seen so far. At each day `i`, absolute max profit is `max(maxProfit, prices[i] - minPrice)`. O(N) Time.

---

### Problem 13 — Maximum Circular Subarray Sum

> 🔗 **LeetCode:** [918. Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)

**`[Amazon] [Medium]`**  
**Pattern: Advanced Kadane's**

Given a _circular_ integer array, find the maximum possible sum of a non-empty subarray.  
**Hint:** The max circular subarray sum is either simply `Kadane_Max(nums)` OR it wraps around: `Total_Sum - Kadane_Min(nums)`. Be careful of the edge case where all numbers are negative!

---

### Problem 14 — Group Anagrams

> 🔗 **LeetCode:** [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)

**`[Amazon] [Facebook] [Microsoft] [Medium]`**  
**Pattern: Frequency Array as HashMap Key**

Given an array of strings, group the anagrams together.  
**Slow way:** Sort every string to use as the key. O(N _K log K).  
**Fast way:** Build a 26-char frequency array for each string, convert it to a delimited string `"1#0#2#..."` and use that as the HashMap key! O(N_ K).

---

### Problem 15 — Rotate Image (2D Matrix Rotation)

> 🔗 **LeetCode:** [48. Rotate Image](https://leetcode.com/problems/rotate-image/)

**`[Amazon] [Google] [Microsoft] [Medium]`**  
**Pattern: Matrix Transposition & Reversal**

You are given an `n x n` 2D matrix representing an image, rotate the image by 90 degrees (clockwise) in-place.

**The magic trick:** Transpose the matrix (swap `[i][j]` with `[j][i]`), and then reverse each row. O(N²) time, O(1) extra space.

---

### Problem 16 — Range Sum Query 2D - Immutable

> 🔗 **LeetCode:** [304. Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/)

**`[Facebook] [Google] [Medium]`**  
**Pattern: 2D Prefix Sums**

Compute the sum of the elements of a 2D matrix inside a rectangle defined by its upper left corner `(row1, col1)` and lower right corner `(row2, col2)`.

**Goal:** Answer range sum queries in **O(1)** time after an **O(N²)** precomputation.  
`sumRegion = Prefix[r2][c2] - Prefix[r1-1][c2] - Prefix[r2][c1-1] + Prefix[r1-1][c1-1]`

---

### Problem 17 — Insert Interval

> 🔗 **LeetCode:** [57. Insert Interval](https://leetcode.com/problems/insert-interval/)

**`[Google] [Microsoft] [Medium]`**  
**Pattern: Array Iteration / Intersections**

You are given an array of non-overlapping intervals sorted in ascending order. Insert a new interval into the intervals, merging if necessary.

**Expected:** O(N) time. Add all intervals ending before the new one starts. Merge overlapping intervals into a single `newInterval`. Add the rest.

---

### Problem 18 — Largest Number

> 🔗 **LeetCode:** [179. Largest Number](https://leetcode.com/problems/largest-number/)

**`[Amazon] [Google] [Medium]`**  
**Pattern: Custom String Sorting**

Given a list of non-negative integers `nums`, arrange them such that they form the largest number and return it.

**Hint:** Sort strings `a` and `b` by comparing `(a+b)` vs `(b+a)`. Don't forget to handle the edge case of all 0s!

---

### Problem 19 — Subarray Sums Divisible by K

> 🔗 **LeetCode:** [974. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)

**`[Microsoft] [Medium]`**  
**Pattern: Prefix Sum + Modulo Math**

Given an integer array and an integer `k`, return the number of non-empty subarrays that have a sum divisible by `k`.

**Hint:** Maintain a running prefix sum modulo `k`. If you see the same mod twice, the prefix sum difference is perfectly divisible by `k`. Beware of negative moduli in Java! Use `(sum % k + k) % k`.

---

### Problem 20 — Majority Element II

> 🔗 **LeetCode:** [229. Majority Element II](https://leetcode.com/problems/majority-element-ii/)

**`[Amazon] [Medium]`**  
**Pattern: Boyer-Moore Voting Algorithm Extension**

Given an array of size n, find all elements that appear more than `⌊ n/3 ⌋` times.

**Expected:** O(N) time, O(1) space! Since there can be at most 2 elements that appear > n/3 times, maintain two candidate counters.

---

### Problem 21 — Wiggle Sort II

> 🔗 **LeetCode:** [324. Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/)

**`[Google] [Medium]`**  
**Pattern: Index Manipulation / Virtual Array**

Sort an array so that `nums[0] < nums[1] > nums[2] < nums[3]...`

**Expected:** It can be done in O(N log N) using sorting. The true O(N) time, O(1) space solution requires QuickSelect (Kth Largest) combined with a "virtual indexing" Dutch National Flag partition pattern!

---

### Problem 22 — Minimum Size Subarray Sum

> 🔗 **LeetCode:** [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

**`[Facebook] [Medium]`**  
**Pattern: Prefix Sums + Binary Search (O(N log N) variant)**

Given an array of positive integers and a target, find the minimal length of a contiguous subarray whose sum is `>= target`. If none exists, return 0.

_(Note: The O(N) Sliding Window solution is best, but solving it via Prefix Sums + `lower_bound` Binary Search is an EXCELLENT exercise that interviewers ask to test your Prefix Sum mastery!)._

---

### Problem 23 — Top K Frequent Elements

> 🔗 **LeetCode:** [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

**`[Amazon] [Google] [Medium]`**  
**Pattern: Frequency Map -> Bucket Sort**

Given an array and integer `k`, return the `k` most frequent elements in `O(n)` time!

**Hint:** Count frequencies in a HashMap. Then use Bucket Sort — create an array of Lists where the index is the frequency. Iterate backwards from `n`. O(N) time!

---

## 🔴 Hard — FAANG Level

---

### Problem 24 — Trapping Rain Water

> 🔗 **LeetCode:** [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

**`[Amazon] [Google] [Facebook] [Apple] [Hard]`**  
**Pattern: Prefix / Suffix Max Arrays**

Given `n` non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

**Solution 1:** Compute `leftMax[i]` array and `rightMax[i]` array. Water at `i = min(leftMax, rightMax) - height[i]`. O(N) Space.  
_(Two Pointer O(1) space will be taught in Lecture 6, but master the prefix arrays first!)_

---

### Problem 25 — First Missing Positive

> 🔗 **LeetCode:** [41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

**`[Amazon] [Microsoft] [Hard]`**  
**Pattern: Cyclic Sort / In-place Hashing**

Given an unsorted integer array `nums`, return the smallest missing positive integer. You must implement an algorithm that runs in `O(n)` time and uses constant extra space.

**Hint:** Place each number `x` where `1 <= x <= n` at its correct index `x-1` by continuously swapping `nums[i]` with `nums[nums[i]-1]`.

---

### Problem 26 — Submatrix Sum Queries (Maximum Sum Rectangle)

> 🔗 **Practice:** [Maximum Sum Rectangle in a 2D Matrix (GFG)](https://www.geeksforgeeks.org/maximum-sum-rectangle-in-a-2d-matrix-dp-27/)

**`[Amazon] [Google] [Hard]`**  
**Pattern: 1D Prefix Sums + Kadane's on 2D**

Given a 2D matrix, find the maximum sum submatrix.

**Hint:** Fix the left and right columns `(O(C²))`. For the rows between these columns, maintain a 1D running sum array of row sums. Run 1D Kadane's algorithm on that array `(O(R))`.  
**Overall Complexity:** O(C² × R).

---

### Problem 27 — Shortest Palindrome

> 🔗 **LeetCode:** [214. Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/)

**`[Google] [Hard]`**  
**Pattern: String Reversal + KMP (or Prefix check)**

You are given a string `s`. You can convert `s` to a palindrome by adding characters strictly in front of it. Find and return the shortest palindrome you can find.

**Hint:** You essentially need to find the longest palindromic prefix of `s`. `s.substring(0, i)` that equals its reverse.

---

### Problem 28 — String Transforms Into Another String

> 🔗 **LeetCode:** [1153. String Transforms Into Another String](https://leetcode.com/problems/string-transforms-into-another-string/) _(Premium)_

**`[Google] [Hard]`**  
**Pattern: Character Mapping / Graphs**

Determine if you can transform `str1` into `str2` by simultaneously replacing one character with another everywhere it appears.

**Hint:** You need a 1-to-1 or Many-to-1 mapping. Keep a `HashMap<Character, Character>`. If the mapping tries to map `a -> b` and `a -> c`, it's impossible. Also, check edge case: if all 26 characters are present in `str2`, you need at least one unused char to use as a temporary variable!

---

## 📊 Complexity Analysis — Spot the Tradeoffs

### Problem 29 — Analyze Kadane's modifications

```java
int maxProd = nums[0], minProd = nums[0], res = nums[0];
for (int i = 1; i < nums.length; i++) {
    int temp = Math.max(nums[i], Math.max(maxProd * nums[i], minProd * nums[i]));
    minProd = Math.min(nums[i], Math.min(maxProd * nums[i], minProd * nums[i]));
    maxProd = temp;
    res = Math.max(res, maxProd);
}
```

> **What does this snippet compute?** \_\_\_\_  
> **What is the Time & Space Complexity?** \_\_\_\_

---

### Problem 30 — Memory Tracing Frequency Maps

```java
boolean check(String s) {
    int[] count = new int[128];
    for (char c : s.toCharArray()) {
        count[c]++;
        if (count[c] > 1) return false;
    }
    return true;
}
```

> **Time Complexity:** O(N) or O(128)?? Why? \_\_\_\_  
> **Space Complexity:** O(1). Why not O(N)? \_\_\_\_

---

## 🎁 Bonus — Extended Prefix Matrices and More

**B1:** [523. Continuous Subarray Sum (LeetCode)](https://leetcode.com/problems/continuous-subarray-sum/) — (Modulus Prefix sum)  
**B2:** [152. Maximum Product Subarray (LeetCode)](https://leetcode.com/problems/maximum-product-subarray/) — (Kadane's for products)  
**B3:** [169. Majority Element (LeetCode)](https://leetcode.com/problems/majority-element/) — (Boyer-Moore Voting baseline)  
**B4:** [73. Set Matrix Zeroes (LeetCode)](https://leetcode.com/problems/set-matrix-zeroes/) — (In-place state storage)  
**B5:** [54. Spiral Matrix (LeetCode)](https://leetcode.com/problems/spiral-matrix/) — (2D traversal boundaries)

---

## 🏁 Self-Assessment Checklist

Before moving to Lecture 5 (Sorting & Binary Search):

- [ ] I implemented Kadane’s Algorithm completely from memory.
- [ ] I understand why Range Sum Query 2D works with the `+ - - +` matrix formula.
- [ ] I can write the Dutch National Flag (Sort Colors) `low`, `mid`, `high` swap loop.
- [ ] I completed the "Top K Frequent Elements" using Bucket Sort in O(n) instead of PriorityQueue.
- [ ] I solved First Missing Positive or Trapping Rain Water.
- [ ] I did not use `.sort()` for any problem unless it specifically allowed O(n log n).

---

_Next: Lecture 5 — Sorting & Binary Search. Dive into log(n) searching variants, rotated arrays, and advanced QuickSelect._
