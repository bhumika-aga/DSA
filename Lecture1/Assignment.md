# 📝 Assignment 01 — Java Fundamentals & Big-O Analysis

> **Lecture:** Topic 1 — Java & Programming Fundamentals
> **Topic Count:** 1 of 30 — Phase 1 Foundations
> **Duration:** 5 Days
> **Core Problems:** 30 (20 Easy · 10 Medium) + 10 Challenge + 8 Complexity Exercises
> **Goal:** Cement control flow, array manipulation, type system mastery, and complexity analysis.

---

## 🟢 Easy Tier — 20 Problems (Build the Foundation)

---

### Problem 01 — FizzBuzz (The Universal Warm-Up)

> 🔗 **LeetCode:** [412. FizzBuzz](https://leetcode.com/problems/fizz-buzz/)
> **`[Pattern: Conditionals]` `[Every Company]` `[Easy]`**
> For numbers 1 to n: print "FizzBuzz" if divisible by both 3 and 5, "Fizz" if by 3, "Buzz" if by 5, else the number itself. **Check the combined case first.**

### Problem 02 — Count Digits

> 🔗 **Practice:** [Count Digits (GFG)](https://www.geeksforgeeks.org/problems/count-digits5716/1)
> **`[Pattern: Digit Extraction]` `[Amazon] [TCS]` `[Easy]`**
> Given a positive integer `n`, return the number of digits in it. Solve using loop (while n > 0, n /= 10) and verify with `String.valueOf(n).length()`.

### Problem 03 — Reverse a Number

> 🔗 **LeetCode:** [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)
> **`[Pattern: Digit Extraction]` `[Amazon] [Microsoft]` `[Easy]`**
> Given an integer `n`, return its digits reversed. If the reversed number overflows a 32-bit integer, return 0. **Use `long` to detect overflow.**

### Problem 04 — Armstrong Number

> 🔗 **Practice:** [Armstrong Number (GFG)](https://www.geeksforgeeks.org/problems/armstrong-numbers2727/1)
> **`[Pattern: Digit Extraction]` `[TCS] [Infosys]` `[Easy]`**
> A number is Armstrong if the sum of its digits each raised to the power of the digit count equals the number. E.g., 153 = 1³ + 5³ + 3³.

### Problem 05 — Palindrome Number

> 🔗 **LeetCode:** [9. Palindrome Number](https://leetcode.com/problems/palindrome-number/)
> **`[Pattern: Digit Extraction]` `[Amazon] [Google]` `[Easy]`**
> Check if a number reads the same backward without string conversion. Negative numbers are never palindromes.

### Problem 06 — Fibonacci Sequence (Iterative)

> 🔗 **Practice:** [Fibonacci (GFG)](https://www.geeksforgeeks.org/programs/fibonacci-series-in-java/)
> **`[Pattern: Iteration / DP Preview]` `[Amazon] [Microsoft] [Apple]` `[Easy]`**
> Return the n-th Fibonacci number iteratively — O(n) time, **O(1) space** using just two variables. Also implement the naïve recursive O(2ⁿ) version and compare.

### Problem 07 — GCD and LCM

> 🔗 **Practice:** [GCD of Two Numbers (GFG)](https://www.geeksforgeeks.org/problems/gcd-of-two-numbers3459/1)
> **`[Pattern: Euclidean Algorithm]` `[Amazon] [Google]` `[Easy]`**
> Find GCD using `gcd(a,b) = gcd(b, a%b)` recursively. Derive LCM via `lcm = a / gcd(a,b) * b` (divide first to avoid overflow).

### Problem 08 — Check Palindrome String

> 🔗 **Practice:** [Palindrome String (GFG)](https://www.geeksforgeeks.org/problems/palindrome-string0817/1)
> **`[Pattern: Two Pointers]` `[Amazon] [Google]` `[Easy]`**
> Given a string, check if it reads the same forwards and backwards using two pointers (left, right). O(n) time, O(1) space. Do NOT use `StringBuilder.reverse()`.

### Problem 09 — Count Vowels in a String

> 🔗 **Practice:** Write from scratch — no online link
> **`[Pattern: Frequency Array / char arithmetic]` `[TCS] [Wipro]` `[Easy]`**
> Count the number of vowels (a, e, i, o, u — both cases) in a string. Use a `HashSet` of vowels for O(1) lookup per character. O(n) overall.

### Problem 10 — Power Without `Math.pow()`

> 🔗 **LeetCode:** [50. Pow(x, n)](https://leetcode.com/problems/powx-n/) _(Medium on LC — today do the O(n) version)_
> **`[Pattern: Iteration → Binary Exponentiation preview]` `[Google] [Amazon]` `[Easy]`**
> Implement `power(base, exp)` iteratively in O(exp). Then think: how can you halve the number of multiplications when exp is even?

### Problem 11 — Sum of Digits

> 🔗 **Practice:** [Sum of Digits (GFG)](https://www.geeksforgeeks.org/programs/digital-root/)
> **`[Pattern: Digit Extraction]` `[TCS] [Infosys]` `[Easy]`**
> Return the sum of all digits of a number. Also find the **digital root**: keep summing until a single digit remains.

### Problem 12 — Move Zeroes to End

> 🔗 **LeetCode:** [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)
> **`[Pattern: Two Pointers — slow/fast]` `[Facebook/Meta] [Microsoft]` `[Easy]`**
> Move all zeroes to the end while maintaining the relative order of non-zero elements. O(n) time, O(1) space using a write-pointer.

### Problem 13 — Contains Duplicate

> 🔗 **LeetCode:** [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
> **`[Pattern: Hashing Fundamentals]` `[Amazon] [Google]` `[Easy]`**
> Return true if any value appears at least twice in an array. Use `HashSet` — add while checking, return true on duplicate found.

### Problem 14 — Valid Anagram

> 🔗 **LeetCode:** [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)
> **`[Pattern: Frequency Array]` `[Facebook] [Uber]` `[Easy]`**
> Check if two strings contain the same characters with the same frequencies. Use `int[26]` freq array — increment for s, decrement for t, check all zeros.

### Problem 15 — Running Sum of 1D Array

> 🔗 **LeetCode:** [1480. Running Sum](https://leetcode.com/problems/running-sum-of-1d-array/)
> **`[Pattern: Prefix Sum Basics]` `[Amazon]` `[Easy]`**
> Return the running (prefix) sum. `result[i] = result[i-1] + nums[i]`. The foundation of all range-query problems.

### Problem 16 — Plus One

> 🔗 **LeetCode:** [66. Plus One](https://leetcode.com/problems/plus-one/)
> **`[Pattern: Carry Propagation]` `[Google] [Amazon]` `[Easy]`**
> Add one to a number represented as a digit array. Traverse backwards, handle carry. Don't forget the all-9s edge case (e.g., [9,9,9] → [1,0,0,0]).

### Problem 17 — Single Number

> 🔗 **LeetCode:** [136. Single Number](https://leetcode.com/problems/single-number/)
> **`[Pattern: XOR Cancellation — Preview of L6]` `[Apple] [Amazon]` `[Easy]`**
> Find the unique element where every other appears twice. XOR all elements — pairs cancel to 0. O(n) time, O(1) space.

### Problem 18 — Richest Customer Wealth

> 🔗 **LeetCode:** [1672. Richest Customer](https://leetcode.com/problems/richest-customer-wealth/)
> **`[Pattern: 2D Array Traversal]` `[Easy]`**
> Return the maximum row-sum in an m×n matrix. Nested loops are fine — O(m×n).

### Problem 19 — Shuffle the Array

> 🔗 **LeetCode:** [1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)
> **`[Pattern: Index Arithmetic]` `[Easy]`**
> Interleave [x1, x2, ..., xn, y1, y2, ..., yn] → [x1, y1, x2, y2, ...]. Access using `nums[i]` and `nums[i+n]`.

### Problem 20 — Sum of Natural Numbers (Gauss Formula)

> 🔗 **Practice:** Write from scratch
> **`[Pattern: Math]` `[TCS] [Wipro]` `[Easy]`**
> Return sum 1+2+...+n using `n*(n+1)/2`. Then verify with a loop. Key insight: always use `(long) n * (n+1) / 2` to avoid overflow when n can be up to 10⁵.

---

## 🟡 Medium Tier — 10 Problems (Interview Staples)

---

### Problem 21 — Second Largest Element

> 🔗 **Practice:** [Second Largest (GFG)](https://www.geeksforgeeks.org/problems/second-largest3735/1)
> **`[Pattern: Single Pass State Machine]` `[Adobe] [Samsung]` `[Medium]`**
> Find the second largest without sorting in O(n). Maintain `first` and `second` variables. Handle the case where all elements are equal.

### Problem 22 — Missing Number

> 🔗 **LeetCode:** [268. Missing Number](https://leetcode.com/problems/missing-number/)
> **`[Pattern: Math / XOR]` `[Amazon] [Google]` `[Medium]`**
> Find the missing number in range [0, n]. Two approaches: (1) `expected_sum - actual_sum`; (2) XOR all indices with all values. Both O(n), O(1) space.

### Problem 23 — Maximum Subarray Sum (Kadane's)

> 🔗 **LeetCode:** [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
> **`[Pattern: Dynamic Programming / Greedy]` `[All FAANG]` `[Medium]`**
> Find the contiguous subarray with the largest sum. Kadane's key insight: `currentMax = max(num, currentMax + num)`. O(n) time, O(1) space. Also find the actual subarray indices.

### Problem 24 — Two Sum

> 🔗 **LeetCode:** [1. Two Sum](https://leetcode.com/problems/two-sum/)
> **`[Pattern: Complement Lookup]` `[Literally Everyone]` `[Medium]`**
> Return indices of two numbers summing to target in O(n). HashMap: store `value → index`, check `target - nums[i]` on each step. Store AFTER checking (prevents self-pair bug).

### Problem 25 — Best Time to Buy and Sell Stock

> 🔗 **LeetCode:** [121. Best Time to Buy/Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
> **`[Pattern: Min-So-Far]` `[Amazon] [Goldman Sachs]` `[Medium]`**
> One transaction — maximum profit. Track `minPrice` as you scan; at each step `profit = price - minPrice`. O(n) time. Follow-up: what changes for unlimited transactions? (LC 122)

### Problem 26 — Max Sum Subarray of Size K (Sliding Window Preview)

> 🔗 **Practice:** [Max Sum K-size (GFG)](https://www.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1)
> **`[Pattern: Fixed Sliding Window]` `[Amazon] [Microsoft]` `[Medium]`**
> Find the maximum sum among all subarrays of exactly size k. Build the first window in O(k), then slide: add right element, remove leftmost. O(n) total.

### Problem 27 — Sort Array of 0s, 1s, and 2s

> 🔗 **LeetCode:** [75. Sort Colors](https://leetcode.com/problems/sort-colors/)
> **`[Pattern: Dutch National Flag — 3-way partition]` `[Google] [Microsoft]` `[Medium]`**
> Sort in-place in O(n), O(1) space using three pointers: `lo`, `mid`, `hi`. This is the Dutch National Flag algorithm — a pattern that unlocks partition-based problems.

### Problem 28 — Find Majority Element

> 🔗 **LeetCode:** [169. Majority Element](https://leetcode.com/problems/majority-element/)
> **`[Pattern: Boyer-Moore Voting]` `[Amazon] [Microsoft]` `[Medium]`**
> Find the element appearing > n/2 times. Boyer-Moore: maintain `candidate` and `count`. When count hits 0, switch candidate. Proves itself final in one pass — fascinating algorithm!

### Problem 29 — Product of Array Except Self

> 🔗 **LeetCode:** [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
> **`[Pattern: Prefix × Suffix Product]` `[Amazon] [Facebook/Meta] [Apple]` `[Medium]`**
> Return result[i] = product of all elements except nums[i] — without division, in O(n). Two passes: left products forward, right products backward, multiply in-place.

### Problem 30 — Rotate Array by K

> 🔗 **LeetCode:** [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
> **`[Pattern: Three Reversals]` `[Amazon] [Microsoft]` `[Medium]`**
> Rotate right by k positions, O(1) space. Reversal trick: reverse all → reverse first k → reverse rest. Works because reversing reverses the shift direction.

---

## 🔴 Challenge Zone — 10 Advanced Problems

---

- **P31: Find Duplicate in Array** ([LC 287](https://leetcode.com/problems/find-the-duplicate-number/)) `[Pattern: Floyd's Cycle Detection]` — Only O(1) extra space allowed
- **P32: Trapping Rain Water** ([LC 42](https://leetcode.com/problems/trapping-rain-water/)) `[Pattern: Two Pointers / Precomputation]` — Google/Amazon favourite
- **P33: Max Product Subarray** ([LC 152](https://leetcode.com/problems/maximum-product-subarray/)) `[Pattern: Track min AND max]` — Sign-flip trick
- **P34: Merge Intervals** ([LC 56](https://leetcode.com/problems/merge-intervals/)) `[Pattern: Sort + Greedy Merge]` — Sort by start, merge overlapping
- **P35: Longest Consecutive Sequence** ([LC 128](https://leetcode.com/problems/longest-consecutive-sequence/)) `[Pattern: HashSet Lookup O(n)]`
- **P36: 3Sum** ([LC 15](https://leetcode.com/problems/3sum/)) `[Pattern: Sort + Two Pointers]` — Handle duplicates carefully
- **P37: Spiral Matrix** ([LC 54](https://leetcode.com/problems/spiral-matrix/)) `[Pattern: Layer-by-layer traversal]`
- **P38: Set Matrix Zeroes** ([LC 73](https://leetcode.com/problems/set-matrix-zeroes/)) `[Pattern: In-place marking]` — O(1) space version
- **P39: Jump Game** ([LC 55](https://leetcode.com/problems/jump-game/)) `[Pattern: Greedy reach tracking]` — Amazon/Google
- **P40: Pascal's Triangle** ([LC 118](https://leetcode.com/problems/pascals-triangle/)) `[Pattern: 2D DP]`

---

## 📊 Complexity Analysis Exercises — 8 Snippets

Determine **Time** and **Space** complexity for each. Answers below.

```java
// Snippet A
for (int i = 1; i < n; i *= 2)
    for (int j = 0; j < n; j++)
        sum++;

// Snippet B
int fib(int n) {
    if (n <= 1) return n;
    return fib(n-1) + fib(n-2);
}

// Snippet C
void merge(int[] arr, int l, int mid, int r) { /* O(n) work */ }
void mergeSort(int[] arr, int l, int r) {
    if (l >= r) return;
    int mid = (l + r) / 2;
    mergeSort(arr, l, mid);
    mergeSort(arr, mid+1, r);
    merge(arr, l, mid, r);
}

// Snippet D
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++)
        for (int k = j; k < n; k++)
            count++;

// Snippet E
Map<Integer, Integer> memo = new HashMap<>();
int fib(int n) {
    if (n <= 1) return n;
    if (memo.containsKey(n)) return memo.get(n);
    int res = fib(n-1) + fib(n-2);
    memo.put(n, res);
    return res;
}

// Snippet F — What is the total number of operations?
for (int i = n; i > 0; i /= 2)
    for (int j = 0; j < i; j++)
        process();

// Snippet G
boolean hasDuplicate(int[] arr) {
    Set<Integer> seen = new HashSet<>();
    for (int x : arr) {
        if (seen.contains(x)) return true;
        seen.add(x);
    }
    return false;
}

// Snippet H
int binarySearch(int[] arr, int target) { /* standard impl */ }
for (int i = 0; i < n; i++)
    binarySearch(arr, arr[i]);  // arr is sorted
```

**Answers:**

| Snippet       | Time       | Space | Key Insight                                    |
| ------------- | ---------- | ----- | ---------------------------------------------- |
| A             | O(n log n) | O(1)  | Outer: log₂n iters; inner: n iters             |
| B             | O(2ⁿ)      | O(n)  | Two recursive calls: binary tree of height n   |
| C (mergeSort) | O(n log n) | O(n)  | log n levels × O(n) merge; O(n) aux for merge  |
| D             | O(n³)      | O(1)  | Triple nested — n(n+1)(n+2)/6 ≈ O(n³)          |
| E (memo fib)  | O(n)       | O(n)  | Each subproblem computed once; O(n) call stack |
| F             | O(n)       | O(1)  | Geometric series: n + n/2 + n/4 + ... = 2n     |
| G             | O(n) avg   | O(n)  | HashMap O(1) per op × n ops; O(n) HashSet      |
| H             | O(n log n) | O(1)  | n iterations × O(log n) binary search each     |

---

## ✅ Self-Assessment — True / False

Answer without running the code:

1. `5 / 2 == 2.5` in Java → **False** (integer division → 2; cast needed)
2. `"hello" == "hello"` is always true → **False** (string literals CAN be cached, but `new String()` creates new object)
3. `Arrays.sort(int[])` is O(n log n) → **True** (dual-pivot quicksort)
4. `ArrayList.get(i)` is O(n) → **False** (O(1) — backed by array)
5. A recursive factorial(n) uses O(n) stack space → **True** (n frames on call stack)
6. `HashMap.get()` is always O(1) → **False** (O(1) average, O(n) worst case with collisions)
7. `(int)(3.99)` evaluates to 4 → **False** (truncates to 3)
8. Swapping two `int` primitives via a method changes the originals → **False** (pass-by-value)

---

## 🧠 Conceptual Questions

1. Why does `swap(int a, int b)` fail in Java but `swap(int[] arr, int i, int j)` works?
2. What is the difference between `==` and `.equals()` for `String`? Give an example where they differ.
3. Derive why digit extraction (`while n > 0, n /= 10`) is O(log n).
4. Kadane's algorithm vs brute force — what is the core performance win?
5. Why should you use `lo + (hi - lo) / 2` instead of `(lo + hi) / 2` in binary search?
6. What is the output of `Integer.MIN_VALUE * -1`? Why?

---

Next: Topic 2 — Java Memory Management & Collections Framework Deep Dive\_
