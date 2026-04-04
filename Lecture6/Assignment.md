# 📝 Assignment 06 — Bit Manipulation Masterclass

> **Lecture:** Topic 6 — Bit Manipulation
> **Topic Count:** 6 of 30 — Phase 1 Foundations
> **Duration:** 3 Days
> **Core Problems:** 30 (10 Easy · 15 Medium · 5 Hard) + 8 Challenge + 8 Complexity Exercises
> **Goal:** Develop binary intuition, master O(1) bitwise optimizations, and understand XOR properties for interview-standard puzzles.

---

## 🗺️ Problem Map by Pattern

| Pattern / Topic              | Problems           |
| ---------------------------- | ------------------ |
| Basic Bitwise Operations     | 01, 02, 03, 04, 05 |
| Bit Hacks (Set/Clear/Toggle) | 06, 07, 08, 09, 10 |
| Counting Bits (Kernighan)    | 11, 12, 13         |
| Power of 2 & Multiples       | 14, 15             |
| XOR Cancellation Properties  | 16, 17, 18, 19, 20 |
| Bitmasking (Subsets)         | 21, 22, 23         |
| Hamming Distance             | 24, 25             |
| Binary Logic Puzzles         | 26, 27, 28, 29, 30 |
| Challenge Zone (FAANG)       | 31, 32, 33, 34, 35 |

---

## 🟢 Easy Tier — 10 Problems (The Binary Language)

### Problem 01 — Binary to Decimal & Back

Write a function `binToDec(String s)` and `decToBin(int n)` manually without using `Integer.parseInt(s, 2)`. This cements the base-2 understanding.

### Problem 02 — Check if Bit is Set

> 🔗 **Practice:** Write `isSet(int n, int i)` which returns true if the i-th bit from right (0-indexed) is 1. (Use: `(n & (1 << i)) != 0` or `(n >> i) & 1 == 1`).

### Problem 03 — Set the i-th Bit

> 🔗 **Practice:** `setBit(int n, int i)` which ensures the i-th bit is 1. (Use: `n | (1 << i)`).

### Problem 04 — Clear the i-th Bit

> 🔗 **Practice:** `clearBit(int n, int i)` which ensures the i-th bit is 0. (Use: `n & ~(1 << i)`).

### Problem 05 — Toggle the i-th Bit

> 🔗 **Practice:** `toggleBit(int n, int i)` which flips 0 to 1 and vice-versa. (Use: `n ^ (1 << i)`).

### Problem 06 — Check if Power of 2

> 🔗 **LeetCode:** [231. Power of Two](https://leetcode.com/problems/power-of-two/)
> **`[Pattern: n & (n-1) == 0]` `[Easy]`**
> A power of 2 has only one set bit. XORing or ANDing with `n-1` clears the only set bit. Result should be 0.

### Problem 07 — Count Set Bits (Naïve)

> 🔗 **Practice:** Count bits by shifting and checking one by one. O(log N) where N is bits count.

### Problem 08 — Count Set Bits (Kernighan's)

> 🔗 **LeetCode:** [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
> **`[Pattern: n &= (n-1)]` `[Easy]`**
> Loop runs exactly as many times as there are set bits. High-performance interview favorite!

### Problem 09 — Single Number I

> 🔗 **LeetCode:** [136. Single Number](https://leetcode.com/problems/single-number/)
> **`[Pattern: XOR Cancellation]` `[Easy]`**
> Every number appears twice except one. XOR all numbers. Result is the single number. O(n) time, O(1) space.

### Problem 10 — Hamming Distance

> 🔗 **LeetCode:** [461. Hamming Distance](https://leetcode.com/problems/hamming-distance/)
> **`[Pattern: XOR + Count Bits]` `[Easy]`**
> Count different bits between two integers. XOR them and count the set bits in the result.

---

## 🟡 Medium Tier — 15 Problems (XOR & Masking)

### Problem 11 — Single Number II

> 🔗 **LeetCode:** [137. Single Number II](https://leetcode.com/problems/single-number-ii/)
> **`[Pattern: Bit Counting / Finite State]` `[Medium]`**
> Every number appears thrice except one. Solution 1: Count bits in each position and take mod 3. Solution 2: Use two bitmasks `ones` and `twos`.

### Problem 12 — Single Number III

> 🔗 **LeetCode:** [260. Single Number III](https://leetcode.com/problems/single-number-iii/)
> **`[Pattern: XOR + Partition]` `[Medium]`**
> Two numbers appear once, all others twice. XOR all (result = A ^ B). Find the rightmost set bit in `A ^ B` and use it to partition numbers into two groups (one where bit is set, one where it isn't). XOR each group.

### Problem 13 — Subsets (Power Set via Bits)

> 🔗 **LeetCode:** [78. Subsets](https://leetcode.com/problems/subsets/)
> **`[Pattern: Integer to Bitmask]` `[Medium]`**
> Iterate from `0` to `2ⁿ - 1`. For each number, if its `i-th` bit is set, include `nums[i]` in current subset. This is an O(2ⁿ \* n) iterative alternative to recursion.

### Problem 14 — Decode XORed Array

> 🔗 **LeetCode:** [1720. Decode XORed Array](https://leetcode.com/problems/decode-xored-array/)
> **`[Pattern: XOR Inverse]` `[Easy/Medium]`**
> If `encoded[i] = result[i] ^ result[i+1]`, then `result[i+1] = encoded[i] ^ result[i]`.

### Problem 15 — All Pairs Sum XOR

> 🔗 **Practice:** Find XOR of all possible pairs `(arr[i] + arr[j])`. (Hint: Look at individual bits contribution).

### Problem 16 — Binary Number with Alternating Bits

> 🔗 **LeetCode:** [693. Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/)
> **`[Pattern: n ^ (n >> 1)]` `[Medium]`**

### Problem 17 — Maximum XOR of Two Numbers in Array

> 🔗 **LeetCode:** [421. Maximum XOR of Two Numbers](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)
> **`[Pattern: Greedy + Prefix Mask]` `[Medium/Hard]`**
> Use a Trie (Topic 15) or build max XOR bit-by-bit from left.

### Problem 18 — Number of Steps to Reduce to Zero

> 🔗 **LeetCode:** [1342. Number of Steps](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)
> **`[Pattern: Even/Odd Logic]` `[Easy/Medium]`**
> If even, divide by 2 (Right shift); if odd, subtract 1 (Clear rightmost bit).

### Problem 19 — Divide Two Integers

> 🔗 **LeetCode:** [29. Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)
> **`[Pattern: Exponential Bit Shift]` `[Medium]`**
> Divide without using `*`, `/`, or `%`. Use left shifts to subtract `divisor * 2ⁿ`.

### Problem 20 — Gray Code

> 🔗 **LeetCode:** [89. Gray Code](https://leetcode.com/problems/gray-code/)
> **`[Pattern: n ^ (n >> 1)]` `[Medium]`**
> Sequence where adjacent numbers differ by only one bit.

### Problem 21 — Bitwise AND of Range [m, n]

> 🔗 **LeetCode:** [201. Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)
> **`[Pattern: Common Prefix]` `[Medium]`**
> Shift both right until they are equal, then shift back.

### Problem 22 — Minimum Flips to Make a OR b == c

> 🔗 **LeetCode:** [1318. Minimum Flips](https://leetcode.com/problems/minimum-flips-to-make-a-or-b-equal-to-c/)
> **`[Pattern: Bit-by-bit comparison]` `[Medium]`**

### Problem 23 — Maximum Product of Word Lengths

> 🔗 **LeetCode:** [318. Max Product of Word Lengths](https://leetcode.com/problems/maximum-product-of-word-lengths/)
> **`[Pattern: String to Bitmask]` `[Medium]`**
> Map each word to an `int` (bitmask of 26 chars). Two words have no common chars if `(mask1 & mask2) == 0`.

### Problem 24 — Swap Two Numbers without Temporary Variable

> 🔗 **Practice:** `a = a ^ b; b = a ^ b; a = a ^ b;`. Explain why this works.

### Problem 25 — Total Hamming Distance

> 🔗 **LeetCode:** [477. Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/)
> **`[Pattern: Bit Contribution]` `[Medium]`**
> Count set bits at each position. If `k` bits are set and `n-k` are not, that bit position contributes `k * (n-k)` to the total.

---

## 🔴 Challenge Zone — 5 Advanced Problems

### P31-35: The FAANG Tier

- **P31: Missing Number** ([LC 268](https://leetcode.com/problems/missing-number/)) - Solve using XOR.
- **P32: Reverse Bits** ([LC 190](https://leetcode.com/problems/reverse-bits/)) - O(1) time processing via bitwise.
- **P33: UTF-8 Validation** ([LC 393](https://leetcode.com/problems/utf-8-validation/)) - Masking complex bits.
- **P34: Count Triplets XOR** ([LC 1442](https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor/)) - Prefix XOR.
- **P35: Bitwise XOR of all Subsets Sum**: Challenging mathematical logic using bit frequencies.

---

## 📊 Complexity Analysis Exercises — 8 Snippets

Analyze Time and Space for these Bitwise operations.

```java
// Snippet 1
int count = 0;
while (n > 0) {
    n = n & (n - 1);
    count++;
}

// Snippet 2
for (int i = 0; i < (1 << n); i++) {
    for (int j = 0; j < n; j++) {
        if ((i & (1 << j)) != 0) process(j);
    }
}

// Snippet 3
int x = a ^ b; // Time?

// Snippet 4
while (m != n) {
    m >>= 1;
    n >>= 1;
    count++;
}

// Snippet 5 — XOR all numbers from 1 to N
int xorN(int n) {
    if (n % 4 == 0) return n;
    if (n % 4 == 1) return 1;
    if (n % 4 == 2) return n + 1;
    return 0;
}

// Snippet 6
int getBit(int n, int i) { return (n >> i) & 1; }

// Snippet 7
for (int i = 0; i < 32; i++) { /* work */ }

// Snippet 8
List<Integer> list = IntStream.range(0, 1000).boxed().collect(Collectors.toList());
list.removeIf(n -> (n & 1) == 0);
```

**Complexity Answers:**

1. **O(Set Bits)** Time. This is Kernighan's algorithm. Total bits is 32/64, but loop only runs for set bits.
2. **O(2ⁿ \* n)** Time. Power set generation logic.
3. **O(1)**. Bitwise operations are hardware-level constant time.
4. **O(log N)** Time (number of bits).
5. **O(1)** Time. This is a mathematical constant-time trick!
6. **O(1)**.
7. **O(1)** (Technically O(bits) but bits is a constant like 32/64).
8. **O(n)** Time. List traversal and bitwise check for parity.

---

## ✅ Self-Assessment — True / False

1. `n ^ n` always equals 0. → **True**.
2. `n & (n - 1)` always clears the leftmost set bit. → **False** (it clears the **rightmost** set bit).
3. Right shift `>>` is equivalent to dividing by 2. → **True** (for positive integers).
4. `~n` is always equal to `-n`. → **False** (`~n = -n - 1`).
5. Bitwise operations work faster than arithmetic operations like `*` or `/`. → **True**.
6. XORing all elements in an array cancels everything out. → **False** (only if they appear even times).
7. `1 << 31` will result in a negative number in Java. → **True** (sign bit set).
8. Every Even number has the 0-th bit as 0. → **True**.

---

## 🧠 Conceptual Mastery Questions

1. **Why XOR?**: Why is XOR used so frequently in cryptography and checksums? (Hint: Reversibility and bit distribution).
2. **2's Complement**: Explain how Java stores negative numbers. Why use 2's complement over sign-magnitude?
3. **Signed vs Unsigned**: What is the difference between `>>` and `>>>` in Java?
4. **Masking**: When would you use a bitmask over a `Boolean[]` or `HashSet<Integer>`? (Hint: Memory vs Speed).
5. **Binary Addition**: How would you add two numbers using only bitwise operators? (Hint: XOR for sum, AND-Shift for carry).

---

Next: [Topic 7 — Math & Number Theory](../Lecture7/Assignment.md)
