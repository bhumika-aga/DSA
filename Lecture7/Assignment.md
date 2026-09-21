# 🔢 Assignment 7 — Mathematics for DSA

> **Lecture:** 7 of 38 — Mathematics for DSA
> **Phase:** 1 — Foundations
> **Estimated Time:** 4 days · **Total Problems:** 30 (10 Easy · 15 Medium · 5 Hard)
> **Goal:** Master number theory and combinatorics to handle large numbers, overflow prevention, and prime-based
> algorithms.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem               | Pattern               | Move                                    |
| ----------------------------------- | --------------------- | --------------------------------------- |
| "is n prime", "divisors"            | Trial Division        | loop while `i * i <= n`                 |
| "all primes up to n"                | Sieve of Eratosthenes | cross out multiples starting at `p * p` |
| "answer modulo 1e9+7"               | Modular Arithmetic    | reduce after every `+` and `*`          |
| "x to the power n", huge n          | Binary Exponentiation | square the base, halve the exponent     |
| "how many ways to choose / arrange" | Combinatorics         | factorials + modular inverse            |
| "gcd / lcm / common divisor"        | Euclid's Algorithm    | `gcd(b, a % b)`                         |

---

## 🟢 Easy Tier (10 Problems)

_Number Essentials._

### E1 · Prime In Diagonal

**🔗 [LC 2614 — Prime In Diagonal](https://leetcode.com/problems/prime-in-diagonal/)** · Easy
**Pattern:** Primality Check O(√n) | **Companies:** Amazon, Google

**Hint:** Only the two diagonals matter. Write `isPrime(x)` that tests divisors while `i * i <= x` (and returns false for `x < 2`), then track the largest prime on either diagonal.

---

### E2 · The kth Factor of n

**🔗 [LC 1492 — The kth Factor of n](https://leetcode.com/problems/the-kth-factor-of-n/)** · Medium
**Pattern:** Divisors in Pairs | **Companies:** Amazon, Google, Expedia

**Hint:** Walk `i` from 1 while `i * i <= n`. Each divisor `i` gives a partner `n / i`. Count small divisors on the way up; if `k` is beyond them, find the answer among the partners on the way back down.

---

### E3 · Power of Three

**🔗 [LC 326 — Power of Three](https://leetcode.com/problems/power-of-three/)** · Easy
**Pattern:** Math / Loop | **Companies:** Google, Amazon, Adobe

**Hint:** Solve without using a loop or recursion (Hint: use `log` or the largest power of 3 that fits in an int).

---

### E4 · Prime Number of Set Bits in Binary Representation

**🔗 [LC 762 — Prime Number of Set Bits in Binary Representation](https://leetcode.com/problems/prime-number-of-set-bits-in-binary-representation/)** · Easy
**Pattern:** Primality on Small Numbers | **Companies:** Amazon, Google

**Hint:** The set-bit count of a number up to 10⁶ is at most 20, so the primes you care about are {2, 3, 5, 7, 11, 13, 17, 19}. Count bits with `Integer.bitCount` and look them up in that set.

---

### E5 · Count Primes

**🔗 [LC 204 — Count Primes](https://leetcode.com/problems/count-primes/)** · Medium
**Pattern:** Sieve | **Companies:** Google, Amazon, Microsoft

**Hint:** Pre-mark numbers in a boolean array up to `n`. O(N log log N). The fastest way to count prime numbers.

---

### E6 · Greatest Common Divisor of Strings

**🔗 [LC 1071 — Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/)** · Easy
**Pattern:** Euclidean GCD | **Companies:** Amazon, Google, Microsoft

**Hint:** If `str1 + str2 != str2 + str1`, there is no common divisor string. Otherwise the answer is the prefix of length `gcd(len1, len2)` — Euclid's algorithm applied to lengths.

---

### E7 · Number of Subarrays With LCM Equal to K

**🔗 [LC 2470 — Number of Subarrays With LCM Equal to K](https://leetcode.com/problems/number-of-subarrays-with-lcm-equal-to-k/)** · Medium
**Pattern:** LCM Accumulation | **Companies:** Amazon, Google

**Hint:** Fix a start index and extend right, updating `l = lcm(l, nums[j])`. Once `l > k` (or `k % l != 0`), stop extending — the LCM can only grow. Count the positions where `l == k`.

---

### E8 · Factorial Trailing Zeroes

**🔗 [LC 172 — Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/)** · Medium
**Pattern:** Counting Factors of 5 | **Companies:** Amazon, Bloomberg, Google

**Hint:** Why do we only count 5s? `n/5 + n/25 + n/125...`

---

### E9 · Excel Sheet Column Title

**🔗 [LC 168 — Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)** · Easy
**Pattern:** Base-26 Logic | **Companies:** Microsoft, Amazon, Google

**Hint:** Convert 1 → A, 28 → AB. (Hint: Subtract 1 before modulo to handle 1-indexing).

---

### E10 · Happy Number

**🔗 [LC 202 — Happy Number](https://leetcode.com/problems/happy-number/)** · Easy
**Pattern:** Digit Sum Cycle | **Companies:** Amazon, Google, Uber

**Hint:** Use a HashSet (Lecture 13) or Floyd's cycle detection (Lecture 11) to detect if a sum-of-squares reaches 1 or loops.

---

## 🟡 Medium Tier (15 Problems)

_Interview Math._

### M1 · Find Greatest Common Divisor of Array

**🔗 [LC 1979 — Find Greatest Common Divisor of Array](https://leetcode.com/problems/find-greatest-common-divisor-of-array/)** · Easy
**Pattern:** GCD of Array | **Companies:** Amazon, Google

**Hint:** The GCD of the whole array equals the GCD of its minimum and maximum. Use `gcd(b, a % b)`, then generalise: fold `g = gcd(g, x)` over any array.

---

### M2 · Closest Prime Numbers in Range

**🔗 [LC 2523 — Closest Prime Numbers in Range](https://leetcode.com/problems/closest-prime-numbers-in-range/)** · Medium
**Pattern:** Sieve on a Range | **Companies:** Amazon, Google

**Hint:** Sieve all primes up to `right` once, collect the primes in `[left, right]`, and scan adjacent pairs for the smallest gap. Early exit: a gap of 2 (twin primes) can't be beaten.

---

### M3 · Segmented Sieve (Preview)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Primes & Divisors | **Companies:** Google, Amazon, Goldman Sachs

**Task:** Find primes in range [L, R] where `L, R` can be up to 10¹² but `R - L` is small (10⁵). (Hint: Sieve up to √R, then mark range).

---

### M4 · Modular Arithmetic Laws

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Modular Arithmetic & Fast Power | **Companies:** Google, Amazon, Goldman Sachs

**Task:** Write a function `multiply(long a, long b, long m)` that safely returns `(a * b) % m` when `a * b` might exceed `Long.MAX_VALUE`.

---

### M5 · Pow(x, n)

**🔗 [LC 50 — Pow(x, n)](https://leetcode.com/problems/powx-n/)** · Medium
**Pattern:** Divide & Conquer / Binary Exponentiation | **Companies:** Google, Amazon, Meta

**Hint:** Implement in O(log n). Handle negative `n`. The core of modular exponentiation.

---

### M6 · Super Pow

**🔗 [LC 372 — Super Pow](https://leetcode.com/problems/super-pow/)** · Medium
**Pattern:** Modular Arithmetic & Fast Power | **Companies:** Google, Amazon

**Hint:** Compute `(a^b) % m` using Binary Exponentiation. LC 372 is the interview form: `a^b mod 1337` where `b` is too large to fit in any integer type. This is used in RSA and competition math.

---

### M7 · Perfect Number

**🔗 [LC 507 — Perfect Number](https://leetcode.com/problems/perfect-number/)** · Easy
**Pattern:** Sum of Divisors | **Companies:** Amazon, Microsoft

**Hint:** Sum divisors in pairs while `i * i <= n`: add `i` and `n / i` (count a square root only once). Exclude `n` itself, and remember that 1 is not a perfect number.

---

### M8 · Unique Binary Search Trees

**🔗 [LC 96 — Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)** · Medium
**Pattern:** Combinatorics / DP | **Companies:** Google, Amazon, Meta

**Hint:** Find number of unique BSTs with `n` nodes. Catalan (n) = (2n)! / ((n+1)! \* n!).

---

### M9 · Pascal's Triangle

**🔗 [LC 118 — Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)** · Easy
**Pattern:** Combinatorics / 2D DP | **Companies:** Amazon, Google, Adobe

**Hint:** Generate the first `n` rows. `current[j] = prev[j-1] + prev[j]`.

---

### M10 · Pascal's Triangle II

**🔗 [LC 119 — Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)** · Easy
**Pattern:** 1D DP / Row Formula | **Companies:** Apple, Amazon, Microsoft

**Hint:** Return the k-th row in O(k) space. (Hint: Use `nCr = nCr-1 * (n-r+1)/r`).

---

### M11 · Permutation Sequence

**🔗 [LC 60 — Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)** · Hard
**Pattern:** Factorial Number System | **Companies:** Google, Amazon, Meta

**Hint:** Return the k-th permutation of [1..n] in O(n²) without generating all.

---

### M12 · Multiply Strings

**🔗 [LC 43 — Multiply Strings](https://leetcode.com/problems/multiply-strings/)** · Medium
**Pattern:** Long Multiplication | **Companies:** Meta, Amazon, Microsoft

**Hint:** Multiply two large numbers given as strings. (O(N\*M) - school method).

---

### M13 · Check If It Is a Straight Line

**🔗 [LC 1232 — Check If It Is a Straight Line](https://leetcode.com/problems/check-if-it-is-a-straight-line/)** · Easy
**Pattern:** Slope / Cross Product | **Companies:** Amazon, Google

**Hint:** `(y2-y1)/(x2-x1) == (y3-y2)/(x3-x2)`. Use cross product to avoid division by zero: `(y2-y1)*(x3-x2) == (y3-y2)*(x2-x1)`.

---

### M14 · Integer to Roman

**🔗 [LC 12 — Integer to Roman](https://leetcode.com/problems/integer-to-roman/)** · Medium
**Pattern:** Greedy / Subtraction | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Greedy over the 13 values `1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1` with their symbols: while `num >= value`, append the symbol and subtract. Putting 900, 400, 90… in the table removes every special case.

---

### M15 · Excel Sheet Column Number

**🔗 [LC 171 — Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)** · Easy
**Pattern:** Base-26 Conversion | **Companies:** Microsoft, Amazon, Google

**Hint:** It's base 26 with digits 1 to 26: `result = result * 26 + (c - 'A' + 1)`. Then do the reverse (LC 168) and notice the `n - 1` adjustment there.

---

## 🔴 Hard Tier (5 Problems)

_5 Advanced Problems._

### H1 · Count Ways to Make Array With Product

**🔗 [LC 1735 — Count Ways to Make Array With Product](https://leetcode.com/problems/count-ways-to-make-array-with-product/)** · Hard
**Pattern:** Prime Factorisation + nCr with Modular Inverse | **Companies:** Google, Amazon

**Hint:** Factor `k` into primes. A prime with exponent `e` spread over `n` slots gives `C(n + e - 1, e)` ways (stars and bars). Precompute factorials and inverse factorials mod 1e9+7 using Fermat's little theorem.

---

### H2 · Chinese Remainder Theorem (Simplified)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Chinese Remainder Theorem | **Companies:** Google, Amazon, Goldman Sachs

**Task:** Solve for `x` where `x % m1 = a1` and `x % m2 = a2`.

---

### H3 · Count Primes with Memory Optimization

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Bit-Packed Sieve | **Companies:** Google, Amazon, Goldman Sachs

**Task:** Implement Sieve using `BitSet` or `int[]` with bit manipulation to save 8x space.

---

### H4 · Fibonacci mod M for large N

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Matrix Exponentiation | **Companies:** Google, Amazon, Goldman Sachs

**Task:** Use **Matrix Exponentiation** to find `Fib(n) % m` in O(log n).

---

### H5 · Count Anagrams

**🔗 [LC 2514 — Count Anagrams](https://leetcode.com/problems/count-anagrams/)** · Hard
**Pattern:** Multinomial Counting mod p | **Companies:** Google, Amazon

**Hint:** Each word contributes `len! / (c₁! · c₂! · …)`; multiply the words together. Division mod p means multiplying by modular inverses: precompute factorials and inverse factorials.

---

## 📊 Complexity Analysis Exercises

Determine the Time Complexity.

```psuedocode
// Snippet 1
for i from 2 while i × i ≤ n:
    if n mod i = 0: return false

// Snippet 2 — Sieve
for p from 2 while p × p ≤ n:
    if prime[p]:
        for i from p × p to n step p:
            prime[i] ← false

// Snippet 3 — Binary Exponentiation
function pow(a, b):
    res ← 1
    while b > 0:
        if b mod 2 = 1: res ← res × a
        a ← a × a
        b ← b ÷ 2
    return res

// Snippet 4 — Excel Column Title (n characters)
while n > 0:
    c ← letter('A' + (n - 1) mod 26)
    n ← (n - 1) ÷ 26

// Snippet 5 — Euclidean GCD
function gcd(a, b):
    if b = 0: return a
    return gcd(b, a mod b)

// Snippet 6 — Pascal's Triangle Row N
for i from 0 to n - 1:
    // calculate C(n, i) iteratively from C(n, i - 1)
```

**Complexity Answers:**

1. **O(√N)**. Standard primality check complexity.
2. **O(N log log N)**. Sieve mathematical proof.
3. **O(log b)**. Each step halves the exponent.
4. **O(log₂₆ N)**. Base conversion complexity.
5. **O(log (min (a,b)))**. Fibonacci numbers represent the worst case for GCD.
6. **O(N)** Time, O(N) Space. Using the `nCr = nCr-1 * (n-r+1)/r` formula.

---

## 🔍 Self-Assessment — True / False

1. Prime Factorization of N can be found in O(√N). → **True**.
2. Modular arithmetic: `(a / b) % m == (a % m / b % m) % m`. → **False** (Requires Modular Inverse).
3. The number of primes less than N is approximately `N / log N`. → **True** (Prime Number Theorem).
4. `gcd(a, b) * lcm(a, b) = a * b`. → **True**.
5. Pascal's Triangle row 5 has 6 elements. → **True** (Row N has N+1 elements).
6. Binary exponentiation is only used for integers. → **False** (Can be used for matrices, polynomials, etc.).
7. `a % m` is always positive in Java for negative `a`. → **False** (Can be negative; use `(a % m + m) % m`).
8. Sieve of Eratosthenes uses O(N) space. → **True**.

---

## 🧠 Conceptual Check

1. **Why √N?**: Intuitively, why do factors always occur in pairs around the √N mark?
2. **Overflow Prevention**: Why is it critical to use `(a % m * b % m) % m` when dealing with large products? What is
   the `long` range in Java?
3. **Euclidean Efficiency**: Why is the Euclidean algorithm so much faster than subtracting `b` from `a` repeatedly?
4. **Sieve Memory**: If N = 10⁹, can you use Sieve? Why or why not? (Hint: 1GB memory limit).
5. **Modular Inverse Requirement**: Why does the Modular Inverse `x` only exist if `gcd(a, m) = 1`?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Count Ways to Make Array With Product](https://leetcode.com/problems/count-ways-to-make-array-with-product/), [Count Anagrams](https://leetcode.com/problems/count-anagrams/), [Find Greatest Common Divisor of Array](https://leetcode.com/problems/find-greatest-common-divisor-of-array/), [Closest Prime Numbers in Range](https://leetcode.com/problems/closest-prime-numbers-in-range/) |
| **Google**    | [Count Ways to Make Array With Product](https://leetcode.com/problems/count-ways-to-make-array-with-product/), [Count Anagrams](https://leetcode.com/problems/count-anagrams/), [Find Greatest Common Divisor of Array](https://leetcode.com/problems/find-greatest-common-divisor-of-array/), [Closest Prime Numbers in Range](https://leetcode.com/problems/closest-prime-numbers-in-range/) |
| **Microsoft** | [Perfect Number](https://leetcode.com/problems/perfect-number/), [Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/), [Multiply Strings](https://leetcode.com/problems/multiply-strings/), [Integer to Roman](https://leetcode.com/problems/integer-to-roman/)                                                                                                          |
| **Meta**      | [Pow(x, n)](https://leetcode.com/problems/powx-n/), [Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/), [Permutation Sequence](https://leetcode.com/problems/permutation-sequence/), [Multiply Strings](https://leetcode.com/problems/multiply-strings/)                                                                                                  |
| **Adobe**     | [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/), [Integer to Roman](https://leetcode.com/problems/integer-to-roman/), [Power of Three](https://leetcode.com/problems/power-of-three/)                                                                                                                                                                                     |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can explain why the sieve starts crossing out at `p * p`
- [ ] I can compute `a^b mod m` in O(log b) from memory

---

**← [Lecture 6 · Bit Manipulation](../Lecture6/Assignment.md)** &nbsp;·&nbsp; **[Lecture 8 · Arrays & Strings](../Lecture8/Assignment.md) →**
