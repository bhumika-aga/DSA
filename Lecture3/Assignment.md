# 📝 Assignment 03 — Bit Manipulation

> **Lecture:** Bit Manipulation  
> **Builds on:** Lecture 2 (Recursion & Backtracking)  
> **Complete before:** Lecture 4 (Arrays & Strings)  
> **Rule:** Always state the bitwise trick used and verify with a dry run on at least 2 examples.

---

## 🗺️ Problem Map by Pattern

| Pattern                      | Problems       |
| ---------------------------- | -------------- |
| Basic Bit Operations         | 01, 02, 03, 04 |
| XOR Tricks                   | 05, 06, 07, 08 |
| Brian Kernighan / Count Bits | 09, 10, 11     |
| Power of 2 / Masks           | 12, 13, 14     |
| Bit Manipulation + Math      | 15, 16, 17, 18 |
| Hard / FAANG-level           | 19, 20, 21, 22 |
| Complexity Analysis          | 23             |
| Bonus Practice               | B1–B7          |

---

## 🟢 Easy — Pattern Builders (Do ALL)

---

### Problem 01 — Check if Nth Bit is Set

> 🔗 **Practice:** [Check Nth Bit (GFG)](https://www.geeksforgeeks.org/problems/check-whether-k-th-bit-is-set-or-not-1587115620/1)

**`[Amazon] [TCS] [Easy]`**  
**Pattern: Basic Bit Check**

Given a number `n` and a position `k` (0-indexed from right), check if the kth bit is set (1) or not (0).

```txt
Input:  n = 13 (1101), k = 2  → Output: true  (bit 2 is 1)
Input:  n = 13 (1101), k = 1  → Output: false (bit 1 is 0)
```

**Two approaches:** `(n >> k) & 1` or `n & (1 << k)`. Both are O(1).  
**Expected:** Time O(1), Space O(1)

---

### Problem 02 — Set, Clear, and Toggle a Bit

> 🔗 **Practice:** [Set kth Bit (GFG)](https://www.geeksforgeeks.org/problems/set-kth-bit3724/1)

**`[Microsoft] [Easy]`**  
**Pattern: Bit Masking Fundamentals**

Given `n` and position `k`, implement three operations:

- **Set:** Turn bit k to 1 → `n | (1 << k)`
- **Clear:** Turn bit k to 0 → `n & ~(1 << k)`
- **Toggle:** Flip bit k → `n ^ (1 << k)`

```txt
Input:  n = 10 (1010), k = 2
Set → 14 (1110), Clear → 10 (1010), Toggle → 14 (1110)
```

**Expected:** Time O(1), Space O(1)

---

### Problem 03 — Swap Two Numbers Without Temp

> 🔗 **Practice:** [Swap without temp (GFG)](https://www.geeksforgeeks.org/problems/swap-two-numbers3844/1)

**`[Amazon] [Microsoft] [Easy]`**  
**Pattern: XOR Property — a ^ a = 0, a ^ 0 = a**

Swap two integers without using a temporary variable.

```txt
a = 5, b = 9
a = a ^ b  → a = 12
b = a ^ b  → b = 5   (original a)
a = a ^ b  → a = 9   (original b)
```

**Why it works:** XOR is self-inverse. `(a^b)^b = a` and `(a^b)^a = b`.  
**Expected:** Time O(1), Space O(1)

---

### Problem 04 — Count Number of Set Bits (Hamming Weight)

> 🔗 **LeetCode:** [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)

**`[Amazon] [Microsoft] [Apple] [Easy]`**  
**Pattern: Brian Kernighan's Algorithm**

Count the number of 1-bits in the binary representation of an unsigned integer.

```txt
Input:  n = 11 (1011)  → Output: 3
Input:  n = 128 (10000000) → Output: 1
```

**Brute:** Check each bit with `n & 1`, shift right → O(32)  
**Optimal (Brian Kernighan):** `n = n & (n-1)` removes lowest set bit each iteration → O(set bits)  
**Expected:** Time O(k) where k = number of set bits

---

### Problem 05 — Single Number (XOR)

> 🔗 **LeetCode:** [136. Single Number](https://leetcode.com/problems/single-number/)

**`[Amazon] [Google] [Microsoft] [Apple] [Easy]`**  
**Pattern: XOR Cancellation — a ^ a = 0**

Every element appears twice except one. Find the single one. Must use O(1) space.

```txt
Input:  [2, 2, 1]     → Output: 1
Input:  [4, 1, 2, 1, 2] → Output: 4
```

**Key insight:** XOR all elements. Pairs cancel out (a^a=0), leaving the unique number.  
**Expected:** Time O(n), Space O(1)

---

### Problem 06 — Power of Two

> 🔗 **LeetCode:** [231. Power of Two](https://leetcode.com/problems/power-of-two/)

**`[Amazon] [Google] [Easy]`**  
**Pattern: n & (n-1) == 0**

Check if a given integer is a power of two.

```txt
Input:  n = 16  → Output: true  (10000)
Input:  n = 6   → Output: false (110)
Input:  n = 1   → Output: true  (1)
```

**Why `n & (n-1)` works:** Powers of 2 have exactly ONE set bit. `n-1` flips all bits below it. AND gives 0.  
**Edge case:** n must be > 0!  
**Expected:** Time O(1), Space O(1)

---

## 🟡 Medium — Core Pattern Mastery

---

### Problem 07 — Missing Number

> 🔗 **LeetCode:** [268. Missing Number](https://leetcode.com/problems/missing-number/)

**`[Amazon] [Google] [Microsoft] [Medium]`**  
**Pattern: XOR with indices**

Given array of n distinct numbers in range [0, n], find the missing one.

```txt
Input:  [3, 0, 1]     → Output: 2
Input:  [9,6,4,2,3,5,7,0,1] → Output: 8
```

**XOR approach:** XOR all numbers with all indices 0..n. Everything cancels except the missing one.  
**Math approach:** sum(0..n) - sum(array). But XOR avoids overflow!  
**Expected:** Time O(n), Space O(1)

---

### Problem 08 — Reverse Bits

> 🔗 **LeetCode:** [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)

**`[Amazon] [Apple] [Medium]`**  
**Pattern: Bit-by-bit construction**

Reverse the bits of a 32-bit unsigned integer.

```txt
Input:  00000010100101000001111010011100
Output: 00111001011110000010100101000000 → 964176192
```

**Approach:** Extract each bit from right, place it from left using shift and OR.  
**Expected:** Time O(32) → O(1), Space O(1)

---

### Problem 09 — Counting Bits (DP + Bits)

> 🔗 **LeetCode:** [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

**`[Amazon] [Google] [Medium]`**  
**Pattern: DP using n & (n-1)**

Return an array where ans[i] is the number of 1's in binary representation of i, for 0 ≤ i ≤ n.

```txt
Input:  n = 5
Output: [0, 1, 1, 2, 1, 2]
```

**DP relation:** `bits[i] = bits[i & (i-1)] + 1` — removing lowest set bit gives a smaller number whose answer we already computed.  
**Expected:** Time O(n), Space O(n)

---

### Problem 10 — Bitwise AND of Numbers Range

> 🔗 **LeetCode:** [201. Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)

**`[Amazon] [Microsoft] [Medium]`**  
**Pattern: Common prefix**

Find the bitwise AND of all numbers in range [left, right].

```txt
Input:  left = 5, right = 7  → Output: 4
Input:  left = 1, right = 2147483647 → Output: 0
```

**Key insight:** AND of a range keeps only the common prefix bits. Right-shift both until they're equal, then left-shift back.  
**Expected:** Time O(log n), Space O(1)

---

### Problem 11 — Find the Two Non-Repeating Elements

> 🔗 **Practice:** [Two Non-Repeating (GFG)](https://www.geeksforgeeks.org/problems/finding-the-numbers0702/1)

**`[Google] [Amazon] [Medium]`**  
**Pattern: XOR + Rightmost Differing Bit**

Every element appears twice except TWO. Find both unique numbers in O(1) space.

```txt
Input:  [1, 2, 3, 2, 1, 4]  → Output: [3, 4]
```

**Steps:** 1) XOR all → get xor of two unique numbers. 2) Find any set bit (rightmost). 3) Split array into two groups by that bit. 4) XOR each group separately.  
**Expected:** Time O(n), Space O(1)

---

### Problem 12 — Total Hamming Distance

> 🔗 **LeetCode:** [477. Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/)

**`[Facebook] [Amazon] [Medium]`**  
**Pattern: Bit-by-bit counting**

Find the total Hamming distance between all pairs of integers in an array.

```txt
Input:  [4, 14, 2]  → Output: 6
```

**Naive:** Compare all pairs → O(n²×32). **Optimal:** For each bit position, count how many numbers have that bit set (c). Contribution = c × (n-c).  
**Expected:** Time O(32n) → O(n), Space O(1)

---

### Problem 13 — Subsets Using Bitmask

> 🔗 **LeetCode:** [78. Subsets](https://leetcode.com/problems/subsets/)

**`[Google] [Amazon] [Facebook] [Medium]`**  
**Pattern: Iterative subset generation via bitmask**

Generate all subsets of a set using bit manipulation (no recursion).

```txt
Input:  [1, 2, 3]
Output: [[], [1], [2], [1,2], [3], [1,3], [2,3], [1,2,3]]
```

**How:** For n elements, iterate mask from 0 to 2ⁿ-1. For each mask, include element j if bit j is set.  
**Expected:** Time O(2ⁿ × n), Space O(1) extra

---

### Problem 14 — UTF-8 Validation

> 🔗 **LeetCode:** [393. UTF-8 Validation](https://leetcode.com/problems/utf-8-validation/)

**`[Google] [Medium]`**  
**Pattern: Bit masking for protocol parsing**

Determine if a given array of integers represents valid UTF-8 encoding.

**Key:** Check leading bits to determine byte count (1-byte: 0xxxxxxx, 2-byte: 110xxxxx, etc.) then verify continuation bytes start with 10.  
**Expected:** Time O(n), Space O(1)

---

## 🔴 Hard — FAANG Level

---

### Problem 15 — Single Number II (every element appears 3 times)

> 🔗 **LeetCode:** [137. Single Number II](https://leetcode.com/problems/single-number-ii/)

**`[Google] [Amazon] [Microsoft] [Hard]`**  
**Pattern: Bit counting modulo 3**

Every element appears three times except one. Find the single one in O(1) space.

```txt
Input:  [2, 2, 3, 2]  → Output: 3
Input:  [0, 1, 0, 1, 0, 1, 99] → Output: 99
```

**Approach 1:** Count each bit across all numbers. If count % 3 ≠ 0, that bit belongs to the unique number.  
**Approach 2:** State machine using `ones` and `twos` variables.  
**Expected:** Time O(n), Space O(1)

---

### Problem 16 — Single Number III (two unique numbers)

> 🔗 **LeetCode:** [260. Single Number III](https://leetcode.com/problems/single-number-iii/)

**`[Google] [Amazon] [Medium-Hard]`**  
**Pattern: XOR + Partitioning**

Every element appears twice except two. Find both.

```txt
Input:  [1, 2, 1, 3, 2, 5]  → Output: [3, 5]
```

**This is Problem 11 on LeetCode.** Use the XOR + rightmost-set-bit partitioning technique.  
**Expected:** Time O(n), Space O(1)

---

### Problem 17 — Maximum XOR of Two Numbers in Array

> 🔗 **LeetCode:** [421. Maximum XOR of Two Numbers](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)

**`[Google] [Amazon] [Hard]`**  
**Pattern: Greedy bit-by-bit + HashSet**

Find the maximum XOR of any two numbers in the array.

```txt
Input:  [3, 10, 5, 25, 2, 8]  → Output: 28 (5 XOR 25)
```

**Greedy approach:** Build the answer bit by bit from MSB. For each bit, check if setting it to 1 is achievable using a HashSet of prefixes.  
**Expected:** Time O(32n), Space O(n)

---

### Problem 18 — Minimum Flips to Make a OR b Equal c

> 🔗 **LeetCode:** [1318. Minimum Flips](https://leetcode.com/problems/minimum-flips-to-make-a-or-b-equal-to-c/)

**`[Amazon] [Medium]`**  
**Pattern: Bit-by-bit comparison**

Given three integers, return the minimum number of bit flips to make `a OR b == c`.

```txt
Input:  a=2, b=6, c=5  → Output: 3
Input:  a=4, b=2, c=7  → Output: 1
```

**For each bit:** If c's bit is 1, at least one of a,b must be 1. If c's bit is 0, BOTH a,b bits must be 0 (may need 2 flips).  
**Expected:** Time O(32), Space O(1)

---

### Problem 19 — Divide Two Integers (No \* / %)

> 🔗 **LeetCode:** [29. Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)

**`[Amazon] [Facebook] [Microsoft] [Hard]`**  
**Pattern: Bit shifting for division**

Divide two integers without using multiplication, division, or mod operator.

```txt
Input:  dividend=10, divisor=3  → Output: 3
Input:  dividend=7, divisor=-2  → Output: -3
```

**Approach:** Use left shifts to find the largest `divisor << k` that fits. Subtract it, add 2^k to result, repeat.  
**Edge case:** Integer overflow when dividend = INT_MIN and divisor = -1.  
**Expected:** Time O(log²n), Space O(1)

---

### Problem 20 — Gray Code

> 🔗 **LeetCode:** [89. Gray Code](https://leetcode.com/problems/gray-code/)

**`[Amazon] [Microsoft] [Medium-Hard]`**  
**Pattern: XOR construction**

Generate gray code sequence of n bits (consecutive numbers differ by 1 bit).

```txt
Input:  n = 2  → Output: [0, 1, 3, 2]  (00,01,11,10)
```

**Formula:** `gray(i) = i ^ (i >> 1)`. Generate all values 0 to 2ⁿ-1 using this.  
**Expected:** Time O(2ⁿ), Space O(1) extra

---

### Problem 21 — Concatenation of Consecutive Binary Numbers

> 🔗 **LeetCode:** [1680. Concatenation of Consecutive Binary Numbers](https://leetcode.com/problems/concatenation-of-consecutive-binary-numbers/)

**`[Medium-Hard]`**  
**Pattern: Bit length tracking + shift**

Concatenate binary representations of 1 to n, return the decimal value mod 10⁹+7.

```txt
Input:  n = 3  → "1" + "10" + "11" = "11011" → Output: 27
```

**Key:** For each number i, shift result left by `bitLength(i)` and OR with i.  
**Expected:** Time O(n), Space O(1)

---

### Problem 22 — Sum of Two Integers (No + Operator)

> 🔗 **LeetCode:** [371. Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/)

**`[Amazon] [Facebook] [Medium]`**  
**Pattern: XOR for sum, AND+shift for carry**

Add two integers without using + or - operator.

```txt
Input:  a=1, b=2  → Output: 3
Input:  a=2, b=3  → Output: 5
```

**How:** `sum = a ^ b` (no-carry sum), `carry = (a & b) << 1`. Repeat until carry is 0.  
**Expected:** Time O(32), Space O(1)

---

## 📊 Complexity Analysis

### Problem 23 — Identify the Complexity

```java
// Code A: Brian Kernighan
int count = 0;
while (n > 0) { n = n & (n-1); count++; }
```

> **Time:** \_\_\_\_  
> **Hint:** How many times does the loop run?

```java
// Code B: Generate all subsets with bitmask
for (int mask = 0; mask < (1 << n); mask++) {
    for (int j = 0; j < n; j++) {
        if ((mask & (1 << j)) != 0) list.add(arr[j]);
    }
}
```

> **Time:** \_\_\_\_  
> **Hint:** How many masks? How many bits per mask?

```java
// Code C: Find two unique numbers
int xor = 0; for (int x : arr) xor ^= x;
int bit = xor & (-xor);
int a = 0, b = 0;
for (int x : arr) { if ((x & bit) != 0) a ^= x; else b ^= x; }
```

> **Time:** \_**\_ Space: \_\_**

---

## 🎁 Bonus — Extra Practice

---

### Problem B1 — Hamming Distance

> 🔗 **LeetCode:** [461. Hamming Distance](https://leetcode.com/problems/hamming-distance/)

**`[Facebook] [Easy]`** — XOR then count set bits. Combines two patterns in one.

---

### Problem B2 — Number Complement

> 🔗 **LeetCode:** [476. Number Complement](https://leetcode.com/problems/number-complement/)

**`[Easy]`** — Flip all bits. Trick: create a mask of all 1s the same length as n.

---

### Problem B3 — Binary Number with Alternating Bits

> 🔗 **LeetCode:** [693. Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/)

**`[Easy]`** — Check if bits alternate (101010...). Hint: `n ^ (n >> 1)` should be all 1s.

---

### Problem B4 — Prime Number of Set Bits

> 🔗 **LeetCode:** [762. Prime Number of Set Bits](https://leetcode.com/problems/prime-number-of-set-bits-in-binary-representation/)

**`[Easy]`** — Count numbers in range where popcount is prime. Use a bitmask of primes ≤ 32.

---

### Problem B5 — Power of Four

> 🔗 **LeetCode:** [342. Power of Four](https://leetcode.com/problems/power-of-four/)

**`[Easy]`** — Power of 2 check + bit must be at even position. Use mask `0x55555555`.

---

### Problem B6 — XOR Queries of a Subarray

> 🔗 **LeetCode:** [1310. XOR Queries of a Subarray](https://leetcode.com/problems/xor-queries-of-a-subarray/)

**`[Medium]`** — Prefix XOR (same idea as prefix sum but with XOR).

---

### Problem B7 — Find the Duplicate Number (Bit Approach)

> 🔗 **LeetCode:** [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

**`[Medium]`** — For each bit position, compare count of set bits in array vs count in [1..n].

---

## 📋 Answers — Complexity Problems

<details>
<summary>Click only after attempting</summary>

**Code A:** O(k) where k = number of set bits. Loop runs exactly k times.  
**Code B:** O(2ⁿ × n). Outer loop: 2ⁿ masks. Inner loop: n bits per mask.  
**Code C:** Time O(n) — two passes through the array. Space O(1) — only uses 3 variables.

</details>

---

## 🏁 Self-Assessment Checklist

- [ ] I can perform get/set/clear/toggle on any bit from memory
- [ ] I can explain Brian Kernighan's algorithm and why it's O(k)
- [ ] I know why `n & (n-1)` removes the lowest set bit (drew it on paper)
- [ ] I solved Single Number without looking at the solution
- [ ] I understand the XOR partitioning trick for two unique numbers
- [ ] I can generate subsets using bitmask (no recursion)
- [ ] I solved at least 3 Hard problems
- [ ] I can explain how to add two numbers using only XOR and AND

---

_Next: Lecture 4 — Arrays & Strings. The most heavily tested topic in interviews._
