# ⚙️ Assignment 1 — Java & Programming Fundamentals

> **Lecture:** 4 of 45 — Java & Programming Fundamentals
> **Phase:** 1 — Foundations
> **Estimated Time:** 5 days · **Total Problems:** 40 (30 Easy · 10 Medium · 0 Hard)
> **Goal:** Cement control flow, array manipulation, type system mastery, and complexity analysis.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                | Pattern                 | Move                                              |
| ------------------------------------ | ----------------------- | ------------------------------------------------- |
| "digits of a number"                 | Digit Extraction        | `n % 10` reads a digit, `n / 10` drops it         |
| "sum / count / max over an array"    | Single Pass Accumulator | one loop, one or two running variables            |
| "is it sorted / rotated / monotonic" | Adjacent Comparison     | compare `a[i]` with `a[i+1]`, count breaks        |
| "how many pairs" with small values   | Counting Array          | count first, then combine counts — no nested loop |
| "grid", "row", "column"              | 2D Index Mapping        | `idx = r * cols + c` and back with `/` and `%`    |
| "might not fit in an int"            | Overflow Guard          | check before multiplying, or switch to `long`     |

---

## 🟢 Easy Tier (30 Problems)

_Build the Foundation._

### E1 · Fizz Buzz

**🔗 [LC 412 — Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)** · Easy
**Pattern:** Conditionals | **Companies:** Amazon, Google

**Hint:** For numbers 1 to n: print "FizzBuzz" if divisible by both 3 and 5, "Fizz" if by 3, "Buzz" if by 5, else the number itself. **Check the combined case first.**

---

### E2 · Count the Digits That Divide a Number

**🔗 [LC 2520 — Count the Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/)** · Easy
**Pattern:** Digit Extraction | **Companies:** Amazon, Adobe

**Hint:** Peel digits with `n % 10` and `n / 10`, but keep the original `n` in a separate variable — you need it to test `original % digit == 0`. Digits of the input are never 0 here, so no divide-by-zero guard is needed.

---

### E3 · Subtract the Product and Sum of Digits of an Integer

**🔗 [LC 1281 — Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)** · Easy
**Pattern:** Digit Extraction | **Companies:** Amazon, Google

**Hint:** One loop, two accumulators: `product *= n % 10` and `sum += n % 10`, then `n /= 10`. Start `product` at 1, not 0. Follow-up: the same loop checks an Armstrong number — sum each digit raised to the digit count and compare with the original.

---

### E4 · Palindrome Number

**🔗 [LC 9 — Palindrome Number](https://leetcode.com/problems/palindrome-number/)** · Easy
**Pattern:** Digit Extraction | **Companies:** Amazon, Adobe, Apple

**Hint:** Check if a number reads the same backward without string conversion. Negative numbers are never palindromes.

---

### E5 · N-th Tribonacci Number

**🔗 [LC 1137 — N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)** · Easy
**Pattern:** Iteration — Rolling Variables | **Companies:** Amazon, Google

**Hint:** Don't recurse — keep only the last three values `a, b, c` and slide them forward `n - 2` times (`next = a + b + c`). Handle `n = 0, 1, 2` first. O(n) time, O(1) space.

---

### E6 · Smallest Even Multiple

**🔗 [LC 2413 — Smallest Even Multiple](https://leetcode.com/problems/smallest-even-multiple/)** · Easy
**Pattern:** GCD & LCM | **Companies:** Amazon, Adobe

**Hint:** The answer is `lcm(n, 2)`. Write `gcd(a, b)` with Euclid's rule `gcd(b, a % b)`, then `lcm = a / gcd(a, b) * b` — divide first so the product can't overflow.

---

### E7 · Find First Palindromic String in the Array

**🔗 [LC 2108 — Find First Palindromic String in the Array](https://leetcode.com/problems/find-first-palindromic-string-in-the-array/)** · Easy
**Pattern:** String Traversal | **Companies:** Amazon, Adobe

**Hint:** Write `isPalindrome(word)` with two indices walking inward, then return the first word for which it is true (or `""`). Practise using `charAt(i)` and comparing `char`s with `==`.

---

### E8 · Determine if String Halves Are Alike

**🔗 [LC 1704 — Determine if String Halves Are Alike](https://leetcode.com/problems/determine-if-string-halves-are-alike/)** · Easy
**Pattern:** Character Counting | **Companies:** Amazon, Microsoft

**Hint:** Count vowels in the first half and the second half separately. `"aeiouAEIOU".indexOf(c) >= 0` is a quick vowel test. Both halves have length `s.length() / 2`.

---

### E9 · Power of Four

**🔗 [LC 342 — Power of Four](https://leetcode.com/problems/power-of-four/)** · Easy
**Pattern:** Loops & Powers | **Companies:** Amazon, Google

**Hint:** Loop version first: while `n % 4 == 0`, divide by 4; the answer is `n == 1`. Guard `n <= 0` up front. (Lecture 9 shows the O(1) bit-trick version.)

---

### E10 · Add Digits

**🔗 [LC 258 — Add Digits](https://leetcode.com/problems/add-digits/)** · Easy
**Pattern:** Digit Extraction | **Companies:** Amazon, Adobe

**Hint:** Simulate: while `num >= 10`, replace it with the sum of its digits. Then find the O(1) formula — the digital root is `1 + (num - 1) % 9` for `num > 0`.

---

### E11 · Duplicate Zeros

**🔗 [LC 1089 — Duplicate Zeros](https://leetcode.com/problems/duplicate-zeros/)** · Easy
**Pattern:** Array Shifting | **Companies:** Google, Amazon

**Hint:** First count how many zeros will be duplicated and still fit. Then fill from the back with a write pointer so you never overwrite a value you still need. Watch the edge case where the last zero only half-fits.

---

### E12 · Concatenation of Array

**🔗 [LC 1929 — Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/)** · Easy
**Pattern:** Array Basics | **Companies:** Amazon, Adobe

**Hint:** Allocate `ans = new int[2 * n]` and set `ans[i] = ans[i + n] = nums[i]`. A warm-up for index arithmetic and array allocation.

---

### E13 · Number of Good Pairs

**🔗 [LC 1512 — Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)** · Easy
**Pattern:** Counting | **Companies:** Amazon, Microsoft

**Hint:** Brute force is two nested loops. Better: a count array — when you see a value that has already appeared `c` times, it forms `c` new good pairs, so add `c` before incrementing.

---

### E14 · Running Sum of 1d Array

**🔗 [LC 1480 — Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)** · Easy
**Pattern:** Prefix Sum Basics | **Companies:** Amazon, Microsoft

**Hint:** Return the running (prefix) sum. `result[i] = result[i-1] + nums[i]`. The foundation of all range-query problems.

---

### E15 · Plus One

**🔗 [LC 66 — Plus One](https://leetcode.com/problems/plus-one/)** · Easy
**Pattern:** Carry Propagation | **Companies:** Google, Amazon, Meta

**Hint:** Add one to a number represented as a digit array. Traverse backwards, handle carry. Don't forget the all-9s edge case (e.g., [9,9,9] → [1,0,0,0]).

---

### E16 · Find the Highest Altitude

**🔗 [LC 1732 — Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/)** · Easy
**Pattern:** Running Sum | **Companies:** Amazon, Microsoft

**Hint:** Start at altitude 0 and add each `gain[i]`, tracking the maximum seen (including the starting 0).

---

### E17 · Richest Customer Wealth

**🔗 [LC 1672 — Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)** · Easy
**Pattern:** 2D Array Traversal | **Companies:** Amazon, Adobe

**Hint:** Return the maximum row-sum in an m×n matrix. Nested loops are fine — O(m×n).

---

### E18 · Shuffle the Array

**🔗 [LC 1470 — Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)** · Easy
**Pattern:** Index Arithmetic | **Companies:** Amazon, Adobe

**Hint:** Interleave [x1, x2, ..., xn, y1, y2, ..., yn] → [x1, y1, x2, y2, ...]. Access using `nums[i]` and `nums[i+n]`.

---

### E19 · Find the Pivot Integer

**🔗 [LC 2485 — Find the Pivot Integer](https://leetcode.com/problems/find-the-pivot-integer/)** · Easy
**Pattern:** Gauss Sum Formula | **Companies:** Amazon, Google

**Hint:** Total sum is `n(n+1)/2`. The pivot `x` satisfies `x(x+1)/2 = total - x(x-1)/2`, which simplifies to `x² = total`. Check whether `total` is a perfect square.

---

### E20 · Third Maximum Number

**🔗 [LC 414 — Third Maximum Number](https://leetcode.com/problems/third-maximum-number/)** · Easy
**Pattern:** Track Top Values | **Companies:** Amazon, Microsoft

**Hint:** Keep three variables `first > second > third` (use `long` or `Integer` so `Integer.MIN_VALUE` in the input isn't confused with "empty"). Skip duplicates. If `third` was never set, return `first`.

---

### E21 · Find Closest Number to Zero

**🔗 [LC 2239 — Find Closest Number to Zero](https://leetcode.com/problems/find-closest-number-to-zero/)** · Easy
**Pattern:** Linear Scan | **Companies:** Amazon, Google

**Hint:** Track the value with the smallest `Math.abs(x)`; on a tie, prefer the larger value. One pass, O(1) space.

---

### E22 · Max Consecutive Ones

**🔗 [LC 485 — Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)** · Easy
**Pattern:** Running Count | **Companies:** Amazon, Google

**Hint:** Keep `current` (length of the run of 1s ending here) and `best`. On a 1 increment `current`; on a 0 reset it to 0. This reset-or-extend idea is the seed of Kadane's algorithm in Lecture 11.

---

### E23 · How Many Numbers Are Smaller Than the Current Number

**🔗 [LC 1365 — How Many Numbers Are Smaller Than the Current Number](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)** · Easy
**Pattern:** Counting Array | **Companies:** Amazon, Microsoft

**Hint:** Brute force O(n²) is fine for n ≤ 500. Then do it in O(n + 100): count each value in `int[101]`, build prefix counts, and the answer for `x` is `prefix[x - 1]`.

---

### E24 · Maximum Ascending Subarray Sum

**🔗 [LC 1800 — Maximum Ascending Subarray Sum](https://leetcode.com/problems/maximum-ascending-subarray-sum/)** · Easy
**Pattern:** Running Sum with Reset | **Companies:** Amazon, Google

**Hint:** Walk the array keeping `sum` of the current ascending run. If `nums[i] > nums[i-1]` extend it, otherwise restart at `nums[i]`. Track the best sum.

---

### E25 · Sort Array By Parity II

**🔗 [LC 922 — Sort Array By Parity II](https://leetcode.com/problems/sort-array-by-parity-ii/)** · Easy
**Pattern:** Two Index Pointers | **Companies:** Amazon, Google

**Hint:** Keep `even = 0` and `odd = 1`. Walk `even` in steps of 2; when `nums[even]` is odd, advance `odd` (steps of 2) to an even value and swap. O(n), in place.

---

### E26 · Element Appearing More Than 25% In Sorted Array

**🔗 [LC 1287 — Element Appearing More Than 25% In Sorted Array](https://leetcode.com/problems/element-appearing-more-than-25-in-sorted-array/)** · Easy
**Pattern:** Sorted Array Scan | **Companies:** Amazon, Google

**Hint:** Because the array is sorted, the answer appears more than n/4 times, so `arr[i] == arr[i + n/4]` for some `i`. One pass, O(1) space.

---

### E27 · Maximum Product of Two Elements in an Array

**🔗 [LC 1464 — Maximum Product of Two Elements in an Array](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/)** · Easy
**Pattern:** Track Top Two | **Companies:** Amazon, Microsoft

**Hint:** You need the two largest values — no sort required. Track `max1` and `max2` in one pass and return `(max1 - 1) * (max2 - 1)`.

---

### E28 · Check if Array Is Sorted and Rotated

**🔗 [LC 1752 — Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)** · Easy
**Pattern:** Count Breaks | **Companies:** Amazon, Google

**Hint:** Count positions where `nums[i] > nums[(i + 1) % n]` (note the wrap-around). A sorted-then-rotated array has at most one such drop.

---

### E29 · Reshape the Matrix

**🔗 [LC 566 — Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)** · Easy
**Pattern:** 2D Index Mapping | **Companies:** Amazon, Microsoft

**Hint:** If `m * n != r * c` return the original. Otherwise walk every cell with a single counter `idx` and place it at `[idx / c][idx % c]`.

---

### E30 · Special Positions in a Binary Matrix

**🔗 [LC 1582 — Special Positions in a Binary Matrix](https://leetcode.com/problems/special-positions-in-a-binary-matrix/)** · Easy
**Pattern:** 2D Counting | **Companies:** Amazon, Google

**Hint:** Pre-count ones per row and per column. A cell `(i, j)` is special when `mat[i][j] == 1` and `rowCount[i] == 1` and `colCount[j] == 1`. O(m·n).

---

## 🟡 Medium Tier (10 Problems)

_Interview Staples._

### M1 · Reverse Integer

**🔗 [LC 7 — Reverse Integer](https://leetcode.com/problems/reverse-integer/)** · Medium
**Pattern:** Digit Extraction | **Companies:** Amazon, Apple, Bloomberg

**Hint:** Given an integer `n`, return its digits reversed. If the reversed number overflows a 32-bit integer, return 0. **Use `long` to detect overflow.**

---

### M2 · Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold

**🔗 [LC 1343 — Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/)** · Medium
**Pattern:** Fixed-Size Window (Preview) | **Companies:** Amazon, Microsoft

**Hint:** Compare sums, not averages: count windows with `sum >= k * threshold`. Build the first window's sum, then slide — add `arr[i]`, subtract `arr[i - k]`. O(n). Lecture 25 generalises this.

---

### M3 · String to Integer (atoi)

**🔗 [LC 8 — String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)** · Medium
**Pattern:** Parsing & Overflow | **Companies:** Amazon, Microsoft, Meta

**Hint:** Four stages in order: skip spaces, read an optional sign, read digits, stop at the first non-digit. Before `result = result * 10 + d`, check `result > (Integer.MAX_VALUE - d) / 10` and clamp.

---

### M4 · Count and Say

**🔗 [LC 38 — Count and Say](https://leetcode.com/problems/count-and-say/)** · Medium
**Pattern:** String Building | **Companies:** Amazon, Google, Meta

**Hint:** Build each term from the previous one: scan runs of equal digits and append `count` then `digit` to a `StringBuilder`. Never use `+=` on a `String` inside the loop.

---

### M5 · Maximum Product Subarray

**🔗 [LC 152 — Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)** · Medium
**Pattern:** Track min AND max | **Companies:** Amazon, Google, LinkedIn

**Hint:** Track both the maximum and the minimum product ending at `i` — a negative number turns the smallest product into the largest. At each step `newMax = max(x, x * max, x * min)` (and symmetrically for min), computed before overwriting.

---

### M6 · Zigzag Conversion

**🔗 [LC 6 — Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion/)** · Medium
**Pattern:** Index Simulation | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Keep `numRows` `StringBuilder`s and a row pointer that bounces 0 → numRows-1 → 0. Append each character to the current row, then join. Handle `numRows == 1` separately.

---

### M7 · Sequential Digits

**🔗 [LC 1291 — Sequential Digits](https://leetcode.com/problems/sequential-digits/)** · Medium
**Pattern:** Number Generation | **Companies:** Amazon, Google

**Hint:** Don't test every number in `[low, high]`. Generate candidates from the string `"123456789"`: for each length from 2 to 9, take every substring of that length, convert it, and keep those in range.

---

### M8 · Smallest Integer Divisible by K

**🔗 [LC 1015 — Smallest Integer Divisible by K](https://leetcode.com/problems/smallest-integer-divisible-by-k/)** · Medium
**Pattern:** Modular Arithmetic | **Companies:** Amazon, Google

**Hint:** The number 111…1 overflows fast, so track only `remainder = (remainder * 10 + 1) % k`. If `k` is divisible by 2 or 5 the answer is -1; otherwise a remainder of 0 appears within `k` steps.

---

### M9 · Jump Game

**🔗 [LC 55 — Jump Game](https://leetcode.com/problems/jump-game/)** · Medium
**Pattern:** Greedy reach tracking | **Companies:** Amazon, Google, Meta, Microsoft

**Hint:** Greedy: keep `farthest`, the furthest index reachable so far. Walk `i` from 0; if `i > farthest` you're stuck, otherwise update `farthest = max(farthest, i + nums[i])`. Return true once `farthest >= n - 1`.

---

### M10 · Check if Number is a Sum of Powers of Three

**🔗 [LC 1780 — Check if Number is a Sum of Powers of Three](https://leetcode.com/problems/check-if-number-is-a-sum-of-powers-of-three/)** · Medium
**Pattern:** Base Conversion | **Companies:** Amazon, Google

**Hint:** Write `n` in base 3 by repeatedly taking `n % 3`. It is a sum of distinct powers of three exactly when no base-3 digit equals 2.

---

## 🔴 Hard Tier (0 Problems)

_No Hard problems at this stage of the course._

## 📊 Complexity Analysis Exercises

Determine **Time** and **Space** complexity for each. Answers below.

```java
// Snippet A
for (int i = 1; i < n; i *= 2)
    for (int j = 0; j < n; j++)
        sum++;

// Snippet B
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}

// Snippet C
void merge(int[] arr, int l, int mid, int r) { /* O(n) work */ }

void mergeSort(int[] arr, int l, int r) {
    if (l >= r) return;
    int mid = (l + r) / 2;
    mergeSort(arr, l, mid);
    mergeSort(arr, mid + 1, r);
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
    int res = fib(n - 1) + fib(n - 2);
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

## 🔍 Self-Assessment — True / False

Answer without running the code:

1. `5 / 2 == 2.5` in Java → **False** (integer division → 2; cast needed)
2. `"hello" == "hello"` is always true → **False** (string literals CAN be cached, but `new String()` creates new
   object)
3. `Arrays.sort(int[])` is O(n log n) → **True** (dual-pivot quicksort)
4. `ArrayList.get(i)` is O(n) → **False** (O(1) — backed by array)
5. A recursive factorial (n) uses O(n) stack space → **True** (n frames on call stack)
6. `HashMap.get()` is always O(1) → **False** (O(1) average, O(n) worst case with collisions)
7. `(int)(3.99)` evaluates to 4 → **False** (truncates to 3)
8. Swapping two `int` primitives via a method changes the originals → **False** (pass-by-value)

---

## 🧠 Conceptual Check

1. Why does `swap(int a, int b)` fail in Java but `swap(int[] arr, int i, int j)` works?
2. What is the difference between `==` and `.equals()` for `String`? Give an example where they differ.
3. Derive why digit extraction (`while n > 0, n /= 10`) is O(log n).
4. Kadane's algorithm vs brute force — what is the core performance win?
5. Why should you use `lo + (hi - lo) / 2` instead of `(lo + hi) / 2` in binary search?
6. What is the output of `Integer.MIN_VALUE * -1`? Why?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Reverse Integer](https://leetcode.com/problems/reverse-integer/), [Check if Number is a Sum of Powers of Three](https://leetcode.com/problems/check-if-number-is-a-sum-of-powers-of-three/), [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/), [Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)                                                                                                                                                                                         |
| **Google**    | [Sequential Digits](https://leetcode.com/problems/sequential-digits/), [Smallest Integer Divisible by K](https://leetcode.com/problems/smallest-integer-divisible-by-k/), [Special Positions in a Binary Matrix](https://leetcode.com/problems/special-positions-in-a-binary-matrix/), [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)                                                                                                                                                 |
| **Microsoft** | [How Many Numbers Are Smaller Than the Current Number](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/), [Maximum Product of Two Elements in an Array](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/), [Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/), [Third Maximum Number](https://leetcode.com/problems/third-maximum-number/) |
| **Adobe**     | [Add Digits](https://leetcode.com/problems/add-digits/), [Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/), [Count the Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/), [Find First Palindromic String in the Array](https://leetcode.com/problems/find-first-palindromic-string-in-the-array/)                                                                                                                                                                   |
| **Meta**      | [Count and Say](https://leetcode.com/problems/count-and-say/), [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/), [Plus One](https://leetcode.com/problems/plus-one/), [Jump Game](https://leetcode.com/problems/jump-game/)                                                                                                                                                                                                                                                                                       |

---

## ✅ Completion Checklist

- [ ] All 20 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 10 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can trace a nested loop and state its Big-O without running it
- [ ] I can explain why `a / gcd * b` is safer than `a * b / gcd`

---

**← [Lecture 3 · Testing & Debugging Your Own Code](../Lecture3/Assignment.md)** &nbsp;·&nbsp; **[Lecture 5 · Java Memory Management](../Lecture5/Assignment.md) →**
