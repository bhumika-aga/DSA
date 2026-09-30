# 🔣 Assignment 9 — Bit Manipulation

> **Lecture:** 9 of 45 — Bit Manipulation
> **Phase:** 1 — Foundations
> **Estimated Time:** 4 days · **Total Problems:** 30 (16 Easy · 14 Medium · 0 Hard)
> **Goal:** Develop binary intuition, master O(1) bitwise optimisations, and understand XOR properties for
> interview-standard puzzles.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                | Pattern             | Move                                       |
| ------------------------------------ | ------------------- | ------------------------------------------ | ------------- |
| "appears twice except one"           | XOR Cancellation    | XOR everything; pairs vanish               |
| "power of two", "lowest set bit"     | `n & (n - 1)`       | clears the lowest set bit                  |
| "count 1 bits"                       | Kernighan's Loop    | repeat `n &= n - 1`                        |
| "all subsets" with n ≤ 20            | Bitmask Enumeration | `for mask in 0 .. 2ⁿ - 1`                  |
| "check / set / clear / toggle bit i" | Bit Masks           | `1 << i` with `&`, `                       | `, `& ~`, `^` |
| "without + or -"                     | Bitwise Arithmetic  | XOR for the sum, AND + shift for the carry |

---

## 🟢 Easy Tier (16 Problems)

_The Binary Language._

### E1 · Binary to Decimal & Back

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Basic Bit Operations | **Companies:** Amazon, Google, Apple

**Task:** Write a function `binToDec(String s)` and `decToBin(int n)` manually without using `Integer.parseInt(s, 2)`. This cements the base-2 understanding.

---

### E2 · Check if Bit is Set

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Basic Bit Operations | **Companies:** Amazon, Google, Apple

**Task:** Write `isSet(int n, int i)` which returns true if the i-th bit from right (0-indexed) is 1. (Use: `(n & (1 << i)) != 0` or `(n >> i) & 1 == 1`).

---

### E3 · Set the i-th Bit

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Basic Bit Operations | **Companies:** Amazon, Google, Apple

**Task:** `setBit(int n, int i)` which ensures the i-th bit is 1. (Use: `n | (1 << i)`).

---

### E4 · Clear the i-th Bit

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Basic Bit Operations | **Companies:** Amazon, Google, Apple

**Task:** `clearBit(int n, int i)` which ensures the i-th bit is 0. (Use: `n & ~(1 << i)`).

---

### E5 · Toggle the i-th Bit

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Basic Bit Operations | **Companies:** Amazon, Google, Apple

**Task:** `toggleBit(int n, int i)` which flips 0 to 1 and vice-versa. (Use: `n ^ (1 << i)`).

---

### E6 · Power of Two

**🔗 [LC 231 — Power of Two](https://leetcode.com/problems/power-of-two/)** · Easy
**Pattern:** n & (n-1) == 0 | **Companies:** Google, Amazon, Apple

**Hint:** A power of 2 has only one set bit. XORing or ANDing with `n-1` clears the only set bit. Result should be 0.

---

### E7 · Number of 1 Bits

**🔗 [LC 191 — Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)** · Easy
**Pattern:** Counting Set Bits | **Companies:** Amazon, Microsoft, Apple

**Hint:** Count bits by shifting and checking one by one. O(log N) where N is bits count.

---

### E8 · Sort Integers by The Number of 1 Bits

**🔗 [LC 1356 — Sort Integers by The Number of 1 Bits](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/)** · Easy
**Pattern:** Counting Set Bits (Kernighan's) | **Companies:** Amazon, Adobe

**Hint:** Write `popcount(x)` with Kernighan's loop `x &= x - 1`. Sort `Integer[]` by `(popcount, value)`. Compare the number of loop iterations with the naive bit-by-bit count.

---

### E9 · Single Number

**🔗 [LC 136 — Single Number](https://leetcode.com/problems/single-number/)** · Easy
**Pattern:** XOR Cancellation | **Companies:** Google, Amazon, Microsoft

**Hint:** Every number appears twice except one. XOR all numbers. Result is the single number. O(n) time, O(1) space.

---

### E10 · Hamming Distance

**🔗 [LC 461 — Hamming Distance](https://leetcode.com/problems/hamming-distance/)** · Easy
**Pattern:** XOR + Count Bits | **Companies:** Meta, Amazon, Adobe

**Hint:** Count different bits between two integers. XOR them and count the set bits in the result.

---

### E11 · Decode XORed Array

**🔗 [LC 1720 — Decode XORed Array](https://leetcode.com/problems/decode-xored-array/)** · Easy
**Pattern:** XOR Inverse | **Companies:** Amazon, Google

**Hint:** If `encoded[i] = result[i] ^ result[i+1]`, then `result[i+1] = encoded[i] ^ result[i]`.

---

### E12 · Binary Number with Alternating Bits

**🔗 [LC 693 — Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/)** · Easy
**Pattern:** n ^ (n >> 1) | **Companies:** Amazon, Microsoft

**Hint:** Check `x = n ^ (n >> 1)`: if the bits alternate, `x` is all ones, so `x & (x + 1) == 0`. No loop needed.

---

### E13 · Number of Steps to Reduce a Number to Zero

**🔗 [LC 1342 — Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)** · Easy
**Pattern:** Even/Odd Logic | **Companies:** Amazon, Adobe

**Hint:** If even, divide by 2 (Right shift); if odd, subtract 1 (Clear rightmost bit).

---

### E14 · Missing Number

**🔗 [LC 268 — Missing Number](https://leetcode.com/problems/missing-number/)** · Easy
**Pattern:** XOR Cancellation | **Companies:** Amazon, Google, Microsoft

**Hint:** XOR all indices `0..n` together with all values; everything present twice cancels and only the missing number survives. No overflow, unlike the sum formula in some languages.

---

### E15 · Reverse Bits

**🔗 [LC 190 — Reverse Bits](https://leetcode.com/problems/reverse-bits/)** · Easy
**Pattern:** Bit Reversal | **Companies:** Amazon, Apple, Adobe

**Hint:** Loop 32 times: `result = (result << 1) | (n & 1)`, then `n >>>= 1` (the unsigned shift matters in Java). Follow-up: cache byte reversals for repeated calls.

---

### E16 · Sum of All Subset XOR Totals

**🔗 [LC 1863 — Sum of All Subset XOR Totals](https://leetcode.com/problems/sum-of-all-subset-xor-totals/)** · Easy
**Pattern:** Bit Contribution / OR Trick | **Companies:** Amazon, Google, Apple

**Hint:** Brute force is 2ⁿ subsets; the bit-frequency insight gives `(OR of all) × 2ⁿ⁻¹` in O(n).

---

## 🟡 Medium Tier (14 Problems)

_XOR & Masking._

### M1 · Single Number II

**🔗 [LC 137 — Single Number II](https://leetcode.com/problems/single-number-ii/)** · Medium
**Pattern:** Bit Counting / Finite State | **Companies:** Google, Amazon, Meta

**Hint:** Every number appears thrice except one. Solution 1: Count bits in each position and take mod 3. Solution 2: Use two bitmasks `ones` and `twos`.

---

### M2 · Single Number III

**🔗 [LC 260 — Single Number III](https://leetcode.com/problems/single-number-iii/)** · Medium
**Pattern:** XOR + Partition | **Companies:** Google, Amazon, Meta

**Hint:** Two numbers appear once, all others twice. XOR all (result = A ^ B). Find the rightmost set bit in `A ^ B` and use it to partition numbers into two groups (one where bit is set, one where it isn't). XOR each group.

---

### M3 · Count Number of Maximum Bitwise-OR Subsets

**🔗 [LC 2044 — Count Number of Maximum Bitwise-OR Subsets](https://leetcode.com/problems/count-number-of-maximum-bitwise-or-subsets/)** · Medium
**Pattern:** Bitmask Enumeration | **Companies:** Google, Amazon

**Hint:** The maximum OR is the OR of the whole array. Enumerate every mask from 1 to `2ⁿ - 1`, OR the chosen elements, and count the masks that reach the maximum.

---

### M4 · Bitwise XOR of All Pairings

**🔗 [LC 2425 — Bitwise XOR of All Pairings](https://leetcode.com/problems/bitwise-xor-of-all-pairings/)** · Medium
**Pattern:** XOR Parity Counting | **Companies:** Amazon, Google

**Hint:** Each `nums1[i]` appears in `len(nums2)` pairs. If that count is odd it survives the XOR, otherwise it cancels. The same holds for `nums2` with `len(nums1)`. O(n + m).

---

### M5 · Maximum XOR of Two Numbers in an Array

**🔗 [LC 421 — Maximum XOR of Two Numbers in an Array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)** · Medium
**Pattern:** Greedy + Prefix Mask | **Companies:** Google, Amazon, Meta

**Hint:** Use a Trie (Lecture 36) or build max XOR bit-by-bit from left.

---

### M6 · Divide Two Integers

**🔗 [LC 29 — Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)** · Medium
**Pattern:** Exponential Bit Shift | **Companies:** Amazon, Microsoft, Meta

**Hint:** Divide without using `*`, `/`, or `%`. Use left shifts to subtract `divisor * 2ⁿ`.

---

### M7 · Gray Code

**🔗 [LC 89 — Gray Code](https://leetcode.com/problems/gray-code/)** · Medium
**Pattern:** n ^ (n >> 1) | **Companies:** Amazon, Google, Adobe

**Hint:** The i-th Gray code is `i ^ (i >> 1)`. Generate it for `i` from 0 to `2ⁿ - 1`. Neighbouring values then differ in exactly one bit.

---

### M8 · Bitwise AND of Numbers Range

**🔗 [LC 201 — Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)** · Medium
**Pattern:** Common Prefix | **Companies:** Google, Amazon

**Hint:** The AND of a range keeps only the common binary prefix of `left` and `right`. Shift both right until they're equal, counting the shifts, then shift back left by that count.

---

### M9 · Minimum Flips to Make a OR b Equal to c

**🔗 [LC 1318 — Minimum Flips to Make a OR b Equal to c](https://leetcode.com/problems/minimum-flips-to-make-a-or-b-equal-to-c/)** · Medium
**Pattern:** Bit-by-bit comparison | **Companies:** Amazon, Google

**Hint:** Go bit by bit. If bit `c` is 1 and both `a` and `b` are 0, you need 1 flip. If bit `c` is 0, you need one flip for each of `a` and `b` that is 1. Sum over 32 bits.

---

### M10 · Maximum Product of Word Lengths

**🔗 [LC 318 — Maximum Product of Word Lengths](https://leetcode.com/problems/maximum-product-of-word-lengths/)** · Medium
**Pattern:** String to Bitmask | **Companies:** Google, Amazon

**Hint:** Map each word to an `int` (bitmask of 26 chars). Two words have no common chars if `(mask1 & mask2) == 0`.

---

### M11 · Swap Two Numbers without Temporary Variable

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Bit Tricks & Puzzles | **Companies:** Amazon, Google, Apple

**Task:** `a = a ^ b; b = a ^ b; a = a ^ b;`. Explain why this works.

---

### M12 · Total Hamming Distance

**🔗 [LC 477 — Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/)** · Medium
**Pattern:** Bit Contribution | **Companies:** Meta, Amazon

**Hint:** Count set bits at each position. If `k` bits are set and `n-k` are not, that bit position contributes `k * (n-k)` to the total.

---

### M13 · UTF-8 Validation

**🔗 [LC 393 — UTF-8 Validation](https://leetcode.com/problems/utf-8-validation/)** · Medium
**Pattern:** Bit Masking | **Companies:** Google, Amazon, Meta

**Hint:** Read the lead byte's high bits to learn the character length (`0xxxxxxx` = 1, `110xxxxx` = 2, `1110xxxx` = 3, `11110xxx` = 4), then check that the next `len - 1` bytes each start with `10`. Mask with `>> 6 == 0b10`.

---

### M14 · Count Triplets That Can Form Two Arrays of Equal XOR

**🔗 [LC 1442 — Count Triplets That Can Form Two Arrays of Equal XOR](https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor/)** · Medium
**Pattern:** Prefix XOR | **Companies:** Google, Amazon

**Hint:** `a == b` means `XOR(i..k) == 0`, which means `prefix[i] == prefix[k + 1]`. Every such pair `(i, k)` gives `k - i` valid `j`s. Count with maps of prefix XOR → count and → sum of indices for O(n).

---

## 🔴 Hard Tier (0 Problems)

_No Hard problems at this stage of the course._

## 📊 Complexity Analysis Exercises

Analyse Time and Space for these Bitwise operations.

```pseudocode
// Snippet 1
count ← 0
while n > 0:
    n ← n AND (n - 1)
    count ← count + 1

// Snippet 2
for mask from 0 to 2ⁿ - 1:
    for j from 0 to n - 1:
        if mask AND (1 << j) ≠ 0:
            process(j)

// Snippet 3
x ← a XOR b          // Time?

// Snippet 4
while m ≠ n:
    m ← m >> 1
    n ← n >> 1
    count ← count + 1

// Snippet 5 — XOR of all numbers from 1 to N
function xorN(n):
    if n mod 4 = 0: return n
    if n mod 4 = 1: return 1
    if n mod 4 = 2: return n + 1
    return 0

// Snippet 6
function getBit(n, i):
    return (n >> i) AND 1

// Snippet 7
for i from 0 to 31:
    // constant work

// Snippet 8
list ← [0, 1, 2, …, 999]          // an array-backed list
remove every even number from list   // each removal shifts the elements after it
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

## 🔍 Self-Assessment — True / False

1. `n ^ n` always equals 0. → **True**.
2. `n & (n - 1)` always clears the leftmost set bit. → **False** (it clears the **rightmost** set bit).
3. Right shift `>>` is equivalent to dividing by 2. → **True** (for positive integers).
4. `~n` is always equal to `-n`. → **False** (`~n = -n - 1`).
5. Bitwise operations work faster than arithmetic operations like `*` or `/`. → **True**.
6. XORing all elements in an array cancels everything out. → **False** (only if they appear even times).
7. `1 << 31` will result in a negative number in Java. → **True** (sign bit set).
8. Every Even number has the 0-th bit as 0. → **True**.

---

## 🧠 Conceptual Check

1. **Why XOR?**: Why is XOR used so frequently in cryptography and checksums? (Hint: Reversibility and bit
   distribution).
2. **2's Complement**: Explain how Java stores negative numbers. Why use 2's complement over sign-magnitude?
3. **Signed vs Unsigned**: What is the difference between `>>` and `>>>` in Java?
4. **Masking**: When would you use a bitmask over a `Boolean[]` or `HashSet<Integer>`? (Hint: Memory vs Speed).
5. **Binary Addition**: How would you add two numbers using only bitwise operators? (Hint: XOR for sum, AND-Shift for
   carry).

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Count Triplets That Can Form Two Arrays of Equal XOR](https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor/), [Reverse Bits](https://leetcode.com/problems/reverse-bits/), [Sum of All Subset XOR Totals](https://leetcode.com/problems/sum-of-all-subset-xor-totals/), [Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/) |
| **Google**    | [Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/), [Bitwise XOR of All Pairings](https://leetcode.com/problems/bitwise-xor-of-all-pairings/), [Count Number of Maximum Bitwise-OR Subsets](https://leetcode.com/problems/count-number-of-maximum-bitwise-or-subsets/), [Decode XORed Array](https://leetcode.com/problems/decode-xored-array/)                         |
| **Meta**      | [Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/), [UTF-8 Validation](https://leetcode.com/problems/utf-8-validation/), [Divide Two Integers](https://leetcode.com/problems/divide-two-integers/), [Maximum XOR of Two Numbers in an Array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)                                                                 |
| **Adobe**     | [Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/), [Sort Integers by The Number of 1 Bits](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/), [Reverse Bits](https://leetcode.com/problems/reverse-bits/), [Gray Code](https://leetcode.com/problems/gray-code/)                                                       |
| **Microsoft** | [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/), [Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/), [Missing Number](https://leetcode.com/problems/missing-number/), [Single Number](https://leetcode.com/problems/single-number/)                                                                                                   |

---

## ✅ Completion Checklist

- [ ] All 16 Easy problems solved
- [ ] All 14 Medium problems solved
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can do set, clear, toggle and check bit i without looking anything up
- [ ] I can explain why `n & (n - 1)` removes the lowest set bit

---

**← [Lecture 8 · Recursion — The Mental Model](../Lecture8/Assignment.md)** &nbsp;·&nbsp; **[Lecture 10 · Mathematics for DSA](../Lecture10/Assignment.md) →**
