# 📝 Assignment 01 — Java Fundamentals & Big-O Analysis

> **Lecture:** Java & Programming Fundamentals  
> **Complete before:** Lecture 2 (Recursion & Backtracking)  
> **Goal:** Cement control flow, array manipulation, and complexity analysis.  
> **How to use:** Solve each problem from scratch. Write the brute force first, then optimize. Always state Time + Space complexity before submitting.

---

## 🟢 Easy — Do ALL of these (Foundation building)

---

### Problem 01 — Count Digits

> 🔗 **Practice:** [Count Digits (GFG)](https://www.geeksforgeeks.org/problems/count-digits5716/1)

**`[Amazon] [TCS] [Infosys] [Easy]`**

Given a positive integer `n`, return the number of digits in it.

```txt
Input:  n = 12345
Output: 5

Input:  n = 1000000
Output: 7
```

**Constraints:** 1 ≤ n ≤ 10⁹  
**Hint:** Think about what happens when you repeatedly divide by 10.  
**Expected Complexity:** Time O(log n), Space O(1)  
**Follow-up:** Can you solve it without a loop using Math?

---

### Problem 02 — Reverse a Number

> 🔗 **LeetCode:** [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)

**`[Amazon] [Microsoft] [Adobe] [Easy]`**

Given an integer `n`, return its digits reversed. If the reversed number overflows a 32-bit integer, return 0.

```txt
Input:  n = 1534236469
Output: 0   (overflow)

Input:  n = 123
Output: 321

Input:  n = -120
Output: -21
```

**Constraints:** -2³¹ ≤ n ≤ 2³¹ - 1  
**Hint:** Extract digits using `% 10` and build the result. Check overflow before multiplying.  
**Expected Complexity:** Time O(log n), Space O(1)

---

### Problem 03 — Armstrong Number

> 🔗 **Practice:** [Armstrong Number (GFG)](https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1)

**`[TCS] [Infosys] [Wipro] [Easy]`**

A number is an Armstrong number if the sum of its digits each raised to the power of the number of digits equals the number itself.

```txt
Input:  n = 153
Output: true    (1³ + 5³ + 3³ = 153)

Input:  n = 370
Output: true    (3³ + 7³ + 0³ = 370)

Input:  n = 100
Output: false
```

**Hint:** First count the digits (call this `k`), then compute sum of digit^k.  
**Expected Complexity:** Time O(log n), Space O(1)

---

### Problem 04 — GCD and LCM

> 🔗 **Practice:** [GCD of Two Numbers (GFG)](https://www.geeksforgeeks.org/problems/gcd-of-two-numbers3459/1)

**`[Amazon] [Google] [Microsoft] [Easy]`**

Given two integers `a` and `b`, find their GCD and LCM.

```txt
Input:  a = 12, b = 18
Output: GCD = 6, LCM = 36
```

**Hint:** Use Euclidean algorithm: `gcd(a, b) = gcd(b, a % b)`. LCM = (a × b) / GCD.  
**Expected Complexity:** Time O(log(min(a,b))), Space O(1)  
**Why this matters:** GCD appears in fraction simplification, music rhythm problems, and number theory questions at FAANG.

---

### Problem 05 — Sum of All Divisors from 1 to N

> 🔗 **Practice:** [Sum of All Divisors (GFG)](https://www.geeksforgeeks.org/problems/sum-of-all-divisors-from-1-to-n4738/1)

**`[Amazon] [Microsoft] [Easy]`**

For each number from 1 to N, print the count of its divisors.

```txt
Input:  N = 5
Output:
1 → 1 divisor
2 → 2 divisors
3 → 2 divisors
4 → 3 divisors
5 → 2 divisors
```

**Approach 1 (Brute):** For each number, check all factors up to √n → O(N√N)  
**Approach 2 (Smart):** For each divisor d from 1 to N, add 1 to all multiples of d → O(N log N) — like a sieve!  
**Expected Complexity:** Aim for O(N log N), Space O(N)

---

### Problem 06 — Print All Prime Numbers up to N (Sieve of Eratosthenes)

> 🔗 **LeetCode:** [204. Count Primes](https://leetcode.com/problems/count-primes/)

**`[Google] [Amazon] [Microsoft] [Adobe] [Easy-Medium]`**

Print all prime numbers from 2 to N.

```txt
Input:  N = 20
Output: 2 3 5 7 11 13 17 19
```

**Brute force:** Check each number with isPrime() → O(N√N)  
**Optimal:** Sieve of Eratosthenes → O(N log log N)  
**Hint for Sieve:** Start with boolean array `isPrime[0..N] = true`. For each prime p starting from 2, mark all multiples of p (p², p²+p, ...) as false.  
**Expected Complexity:** Time O(N log log N), Space O(N)

---

### Problem 07 — Check Palindrome (Number)

> 🔗 **LeetCode:** [9. Palindrome Number](https://leetcode.com/problems/palindrome-number/)

**`[Amazon] [Microsoft] [Facebook] [Easy]`**

Given an integer `x`, return `true` if it is a palindrome.

```txt
Input:  x = 121    → Output: true
Input:  x = -121   → Output: false  (reads -121 backwards = 121-)
Input:  x = 10     → Output: false
```

**Constraint:** Solve without converting to string (use digit reversal!).  
**Hint:** Negative numbers are never palindromes. Reverse only the second half of the number.  
**Expected Complexity:** Time O(log n), Space O(1)

---

### Problem 08 — Move Zeroes to End

> 🔗 **LeetCode:** [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

**`[Facebook] [Amazon] [Microsoft] [Bloomberg] [Easy]`**

Given an array, move all zeroes to the end while maintaining the relative order of non-zero elements. Do it in-place with O(1) extra space.

```txt
Input:  [0, 1, 0, 3, 12]
Output: [1, 3, 12, 0, 0]

Input:  [0, 0, 1]
Output: [1, 0, 0]
```

**Two-pointer approach:** Use a slow pointer (`insertPos`) that tracks where the next non-zero should go. Fast pointer scans ahead.  
**Expected Complexity:** Time O(n), Space O(1)

---

## 🟡 Medium — Attempt at least 5 of these

---

### Problem 09 — Second Largest Element in Array

> 🔗 **Practice:** [Second Largest (GFG)](https://www.geeksforgeeks.org/problems/second-largest3735/1)

**`[Amazon] [Microsoft] [Flipkart] [Medium]`**

Find the second largest distinct element in an array without sorting.

```txt
Input:  [12, 35, 1, 10, 34, 1]
Output: 34

Input:  [10, 10, 10]
Output: -1  (no second largest distinct element)
```

**Hint:** Use two variables: `first` and `second`. Update both in a single pass.  
**Expected Complexity:** Time O(n), Space O(1)  
**Follow-up:** What if you need the Kth largest? (That uses a heap → O(n log K))

---

### Problem 10 — Missing Number in Array

> 🔗 **LeetCode:** [268. Missing Number](https://leetcode.com/problems/missing-number/)

**`[Amazon] [Google] [Microsoft] [Apple] [Medium]`**

Given an array containing n distinct numbers in the range [0, n], return the only missing number.

```txt
Input:  [3, 0, 1]    → Output: 2
Input:  [9,6,4,2,3,5,7,0,1] → Output: 8
```

**Approach 1:** Sum formula: Expected sum = n\*(n+1)/2. Missing = expected - actual.  
**Approach 2:** XOR trick: XOR all indices and all values → missing number remains.  
**Expected Complexity:** Time O(n), Space O(1)  
**Why XOR works:** `a XOR a = 0` and `a XOR 0 = a`. All paired values cancel out!

---

### Problem 11 — Maximum Subarray Sum (Kadane's Algorithm)

> 🔗 **LeetCode:** [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

**`[Google] [Amazon] [Facebook] [Microsoft] [Apple] [Medium]`**

Given an array of integers, find the contiguous subarray with the largest sum.

```txt
Input:  [-2, 1, -3, 4, -1, 2, 1, -5, 4]
Output: 6   (subarray: [4, -1, 2, 1])

Input:  [-1]
Output: -1
```

**Brute force:** Check all O(n²) subarrays → O(n²) time.  
**Kadane's key insight:** At each position, the maximum subarray ending here is either:

- Just the current element alone (start fresh), OR
- The current element + maximum subarray ending at previous position  
  → `maxEndingHere = max(arr[i], maxEndingHere + arr[i])`  
  **Expected Complexity:** Time O(n), Space O(1)  
  **Follow-up:** Return the actual subarray (track start/end indices).

---

### Problem 12 — Two Sum

> 🔗 **LeetCode:** [1. Two Sum](https://leetcode.com/problems/two-sum/)

**`[Amazon] [Google] [Facebook] [Microsoft] [Apple] [Uber] [Medium]`**

Given an array and a target, return indices of the two numbers that add up to target. Each input has exactly one solution.

```txt
Input:  nums = [2,7,11,15], target = 9
Output: [0, 1]   (nums[0] + nums[1] = 2 + 7 = 9)

Input:  nums = [3,2,4], target = 6
Output: [1, 2]
```

**Brute force:** Check all pairs → O(n²)  
**Optimal:** HashMap stores `complement → index`. For each element x, check if `target - x` is in the map.  
**Expected Complexity:** Time O(n), Space O(n)  
**This is the most frequently asked interview question in the world. Know it cold.**

---

### Problem 13 — Best Time to Buy and Sell Stock

> 🔗 **LeetCode:** [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

**`[Amazon] [Facebook] [Google] [Goldman Sachs] [Medium]`**

You have an array `prices[i]` = price on day i. You may buy one stock and sell it later. Find max profit.

```txt
Input:  [7, 1, 5, 3, 6, 4]
Output: 5   (buy at 1, sell at 6)

Input:  [7, 6, 4, 3, 1]
Output: 0   (prices only fall — don't trade)
```

**Key insight:** Track `minPrice` seen so far. At each day, profit = `prices[i] - minPrice`. Track max profit.  
**Expected Complexity:** Time O(n), Space O(1)

---

### Problem 14 — Rotate Array by K Positions

> 🔗 **LeetCode:** [189. Rotate Array](https://leetcode.com/problems/rotate-array/)

**`[Microsoft] [Amazon] [Facebook] [Medium]`**

Rotate an array to the right by k steps, in-place with O(1) extra space.

```txt
Input:  nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
```

**Naive approach:** Rotate one step k times → O(n×k)  
**Extra array approach:** Place each element at correct position → O(n) time, O(n) space  
**Optimal trick (Reversal Algorithm):**

1. Reverse entire array
2. Reverse first k elements
3. Reverse remaining n-k elements  
   → O(n) time, O(1) space  
   **Trace through the example to verify this works!**

---

### Problem 15 — Find Duplicate in Array

> 🔗 **LeetCode:** [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

**`[Amazon] [Google] [Microsoft] [Medium]`**

Given an array of n+1 integers where each integer is between 1 and n (inclusive), find the one duplicate. Space must be O(1) and you cannot modify the array.

```txt
Input:  [1, 3, 4, 2, 2]   → Output: 2
Input:  [3, 1, 3, 4, 2]   → Output: 3
```

**Approaches (from naive to brilliant):**

1. Sort + check adjacent → O(n log n), O(1) space, but modifies array
2. HashMap to track seen → O(n) time, O(n) space
3. Floyd's Cycle Detection (Tortoise & Hare) — treats array as a linked list!  
   → O(n) time, O(1) space — the elegant solution  
   **Hint for Floyd's:** Index i "points to" value arr[i]. A duplicate creates a cycle.

---

## 🔴 Hard — Challenge yourself (attempt at least 2)

---

### Problem 16 — Trapping Rain Water

> 🔗 **LeetCode:** [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

**`[Google] [Amazon] [Facebook] [Microsoft] [Hard]`**

Given an elevation map, compute how much water it can trap after raining.

```txt
Input:  height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```

**Brute force:** For each position, find max height to its left and right → O(n²)  
**Prefix arrays:** Precompute leftMax[] and rightMax[] → O(n) time, O(n) space  
**Two pointers (optimal):** O(n) time, O(1) space.  
**Key insight:** Water at position i = min(maxLeft, maxRight) - height[i].  
Move the pointer on the side with the smaller max (it's the limiting factor).

---

### Problem 17 — Maximum Product Subarray

> 🔗 **LeetCode:** [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)

**`[Amazon] [Google] [Facebook] [Microsoft] [Hard]`**

Find the contiguous subarray with the largest product.

```txt
Input:  [2, 3, -2, 4]   → Output: 6  (subarray [2,3])
Input:  [-2, 0, -1]     → Output: 0
```

**Why it's harder than max sum:** Negatives! A large negative × large negative = large positive.  
**Key insight:** Track BOTH `maxSoFar` and `minSoFar` at each position. When you see a negative number, swap max and min.  
**Expected Complexity:** Time O(n), Space O(1)

---

### Problem 18 — Merge Intervals

> 🔗 **LeetCode:** [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)

**`[Google] [Facebook] [Amazon] [Microsoft] [Uber] [Hard]`**

Given a collection of intervals, merge all overlapping intervals.

```txt
Input:  [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]

Input:  [[1,4],[4,5]]
Output: [[1,5]]
```

**Key steps:**

1. Sort intervals by start time → O(n log n)
2. Iterate: if current interval overlaps with last merged, extend it. Else add new.  
   → Two intervals overlap if `current.start <= last.end`  
   **Expected Complexity:** Time O(n log n), Space O(n)

---

### Problem 19 — Majority Element (Boyer-Moore Voting)

> 🔗 **LeetCode:** [169. Majority Element](https://leetcode.com/problems/majority-element/)

**`[Amazon] [Google] [Microsoft] [Apple] [Hard]`**

Find the element appearing more than n/2 times in an array. Guaranteed to exist.

```txt
Input:  [3, 2, 3]     → Output: 3
Input:  [2,2,1,1,1,2,2] → Output: 2
```

**O(n) space:** Use HashMap to count frequencies.  
**O(1) space — Boyer-Moore Voting Algorithm:**  
Maintain a `candidate` and `count`. If count = 0, set new candidate. If element equals candidate, increment count; else decrement.  
**Why it works:** The majority element's votes can never be fully cancelled out.  
**Expected Complexity:** Time O(n), Space O(1)

---

### Problem 20 — Longest Consecutive Sequence

> 🔗 **LeetCode:** [128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

**`[Google] [Amazon] [Facebook] [Uber] [Hard]`**

Given an unsorted array, find the length of the longest consecutive sequence. Must run in O(n).

```txt
Input:  [100, 4, 200, 1, 3, 2]
Output: 4   (sequence: [1, 2, 3, 4])

Input:  [0,3,7,2,5,8,4,6,0,1]
Output: 9
```

**Brute force:** Sort then scan → O(n log n)  
**Optimal (HashSet):**

1. Put all numbers in a HashSet
2. For each number n, only start counting if (n-1) is NOT in the set (it's a sequence start)
3. Count consecutive from n upward  
   → Each element is visited at most twice → O(n)  
   **Expected Complexity:** Time O(n), Space O(n)

---

## 🎁 Bonus — Extra Practice (Build Speed & Confidence)

---

### Problem 21 — Contains Duplicate

> 🔗 **LeetCode:** [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

**`[Amazon] [Google] [Microsoft] [Easy]`**

Given an integer array, return true if any value appears at least twice.

```txt
Input:  [1, 2, 3, 1]    → Output: true
Input:  [1, 2, 3, 4]    → Output: false
```

**Approach 1 (Brute):** Check all pairs → O(n²)  
**Approach 2 (Sort):** Sort, then check adjacent → O(n log n)  
**Approach 3 (HashSet):** Add to set, return true if already present → O(n) time, O(n) space  
**This teaches you the HashSet pattern — use it everywhere.**

---

### Problem 22 — Valid Anagram

> 🔗 **LeetCode:** [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)

**`[Amazon] [Google] [Facebook] [Uber] [Easy]`**

Given two strings s and t, return true if t is an anagram of s.

```txt
Input:  s = "anagram", t = "nagaram"  → Output: true
Input:  s = "rat", t = "car"         → Output: false
```

**Approach 1:** Sort both strings, compare → O(n log n)  
**Approach 2:** Frequency count array of size 26 → O(n) time, O(1) space  
**Key insight:** Two strings are anagrams if and only if their character frequencies are identical.

---

### Problem 23 — Running Sum of 1D Array

> 🔗 **LeetCode:** [1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

**`[Amazon] [Easy]`**

Given an array, return the running sum (prefix sum).

```txt
Input:  [1, 2, 3, 4]    → Output: [1, 3, 6, 10]
Input:  [3, 1, 2, 10, 1] → Output: [3, 4, 6, 16, 17]
```

**Approach:** Iterate and accumulate: `nums[i] += nums[i-1]` for i ≥ 1.  
**Expected Complexity:** Time O(n), Space O(1) (in-place)  
**Why this matters:** Prefix sums are foundational — they appear in range queries, subarray sums, and DP.

---

### Problem 24 — Plus One

> 🔗 **LeetCode:** [66. Plus One](https://leetcode.com/problems/plus-one/)

**`[Google] [Facebook] [Amazon] [Easy]`**

Given an array of digits representing a number, add one to the number.

```txt
Input:  [1, 2, 3]   → Output: [1, 2, 4]
Input:  [9, 9, 9]   → Output: [1, 0, 0, 0]
```

**Key insight:** Walk backwards. If digit < 9, increment and return. If 9, set to 0 and carry.  
**Edge case:** All 9s → create new array of size n+1 with 1 at front.  
**Expected Complexity:** Time O(n), Space O(1) or O(n) for carry

---

### Problem 25 — Single Number

> 🔗 **LeetCode:** [136. Single Number](https://leetcode.com/problems/single-number/)

**`[Amazon] [Google] [Apple] [Easy]`**

Every element appears twice except one. Find the single one. Use O(1) space.

```txt
Input:  [2, 2, 1]       → Output: 1
Input:  [4, 1, 2, 1, 2] → Output: 4
```

**XOR trick:** `a ^ a = 0` and `a ^ 0 = a`. XOR all elements — duplicates cancel, single remains.  
**Expected Complexity:** Time O(n), Space O(1)  
**This is a must-know bit manipulation pattern!**

---

### Problem 26 — Richest Customer Wealth

> 🔗 **LeetCode:** [1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)

**`[Easy]`**

Given an m×n grid where `accounts[i][j]` is money customer i has in bank j, return the wealth of the richest customer.

```txt
Input:  [[1,2,3],[3,2,1]] → Output: 6
Input:  [[1,5],[7,3],[3,5]] → Output: 10
```

**Approach:** For each row, sum all values. Track max sum.  
**Expected Complexity:** Time O(m×n), Space O(1)  
**Good warm-up for 2D array traversal.**

---

### Problem 27 — Shuffle the Array

> 🔗 **LeetCode:** [1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)

**`[Easy]`**

Given array [x1, x2, ..., xn, y1, y2, ..., yn], return [x1, y1, x2, y2, ..., xn, yn].

```txt
Input:  nums = [2,5,1,3,4,7], n = 3
Output: [2,3,5,4,1,7]
```

**Approach:** Create result array, use two pointers (one for x-half, one for y-half).  
**Expected Complexity:** Time O(n), Space O(n)

## 📊 Complexity Analysis Exercises

For each code snippet below, determine the **Time** and **Space** complexity:

```java
// Snippet A
for (int i = 1; i < n; i *= 2)
    for (int j = 0; j < n; j++)
        System.out.println(i + j);
```

> **Your answer:** Time = \_\_\_\_, Space = \_\_\_\_

```java
// Snippet B
int fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n-1) + fibonacci(n-2);
}
```

> **Your answer:** Time = \_\_\_\_, Space = \_\_\_\_ (think about the call stack!)

```java
// Snippet C
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++)
        for (int k = j; k < n; k++)
            count++;
```

> **Your answer:** Time = \_\_\_\_, Space = \_\_\_\_

```java
// Snippet D
int[] result = new int[n];
for (int i = 0; i < n; i++)
    result[i] = binarySearch(arr, i);  // binarySearch is O(log n)
```

> **Your answer:** Time = \_\_\_\_, Space = \_\_\_\_

---

## ✅ Self-Assessment Checklist

Before moving to Lecture 2, confirm you can:

- [ ] Explain the difference between primitive and reference types in Java
- [ ] State what happens when you pass an int[] vs an int to a method
- [ ] Write a for-loop, while-loop, and do-while loop from memory
- [ ] Explain Big-O in one sentence without looking at notes
- [ ] Apply all 4 Big-O simplification rules to any code snippet
- [ ] Recognize O(log n) complexity just by seeing "divide by 2" in a loop
- [ ] Solve Two Sum using a HashMap in under 5 minutes
- [ ] Explain Kadane's Algorithm logic (not just the code) out loud
- [ ] State Time AND Space complexity for Problems 1–10

---

## 🎯 Complexity Answer Key (Snippets)

<details>
<summary>Click to reveal after attempting</summary>

**Snippet A:** Time = O(n log n) — outer loop runs log n times (i doubles), inner runs n times.  
**Snippet B:** Time = O(2ⁿ) — each call spawns 2 more. Space = O(n) — max recursion depth is n.  
**Snippet C:** Time = O(n³) — three nested loops, each dependent on n.  
**Snippet D:** Time = O(n log n) — n iterations × O(log n) each. Space = O(n) — the result array.

</details>

---

_Next lecture: Recursion & Backtracking — where the real DSA magic begins._
