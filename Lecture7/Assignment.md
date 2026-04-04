# 📝 Assignment 07 — Mathematics for DSA

> **Topic:** Mathematics & Number Theory
> **Topic Count:** 7 of 30 — Phase 1 Foundations
> **Duration:** 3 Days
> **Core Problems:** 30 (10 Easy · 15 Medium · 5 Hard) + 10 Challenge + 6 Complexity Exercises
> **Goal:** Master number theory and combinatorics to handle large numbers, overflow prevention, and prime-based algorithms.

---

## 🗺️ Problem Map by Pattern

| Pattern / Topic         | Problems           |
| ----------------------- | ------------------ |
| Primality Check (O(√N)) | 01, 02, 03, 04     |
| Sieve of Eratosthenes   | 05, 06, 07         |
| Prime Factorization     | 08, 09, 10         |
| GCD & LCM (Euclidean)   | 11, 12, 13, 14     |
| Modular Arithmetic      | 15, 16, 17, 18     |
| Binary Exponentiation   | 19, 20, 21         |
| Combinatorics (nCr)     | 22, 23, 24, 25     |
| Number Theory Puzzles   | 26, 27, 28, 29, 30 |
| Challenge Zone (FAANG)  | 31, 32, 33, 34, 35 |

---

## 🟢 Easy Tier — 10 Problems (Number Essentials)

### Problem 01 — Primality Check (O(√N))

> 🔗 **Practice:** Write `isPrime(n)` which iterates up to `Math.sqrt(n)`. Explain why `n % i == 0` for some `i > √n` implies there exists another factor `j < √n`.

### Problem 02 — List all Divisors

> 🔗 **Practice:** Print all divisors of `n` in sorted order in O(√N). Use `divisor = i` and `divisor = n/i`.

### Problem 03 — Power of Three

> 🔗 **LeetCode:** [326. Power of Three](https://leetcode.com/problems/power-of-three/)
> **`[Pattern: Math / Loop]` `[Easy]`**
> Solve without using a loop or recursion (Hint: use `log` or the largest power of 3 that fits in an int).

### Problem 04 — Count Primes (Naïve)

> 🔗 **Practice:** Count primes in range [1, n] calling `isPrime()` for each. What is the total complexity? O(N√N).

### Problem 05 — Sieve of Eratosthenes (Foundation)

> 🔗 **LeetCode:** [204. Count Primes](https://leetcode.com/problems/count-primes/)
> **`[Pattern: Sieve]` `[Easy/Medium]`**
> Pre-mark numbers in a boolean array up to `n`. O(N log log N). The fastest way to count prime numbers.

### Problem 06 — GCD of two Numbers

> 🔗 **Practice:** Implement `gcd(a, b)` using Euclid’s algorithm `gcd(b, a % b)`. Base case: `b == 0`.

### Problem 07 — LCM of two Numbers

> 🔗 **Practice:** Find LCM using the formula `(a * b) / gcd(a, b)`. **Beware:** `a * b` may overflow. Use `(a / gcd(a, b)) * b`.

### Problem 08 — Trailing Zeroes in Factorial

> 🔗 **LeetCode:** [172. Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/)
> **`[Pattern: Counting Factors of 5]` `[Easy/Medium]`**
> Why do we only count 5s? `n/5 + n/25 + n/125...`

### Problem 09 — Excel Sheet Column Title

> 🔗 **LeetCode:** [168. Excel Column Title](https://leetcode.com/problems/excel-sheet-column-title/)
> **`[Pattern: Base-26 Logic]` `[Easy/Medium]`**
> Convert 1 → A, 28 → AB. (Hint: Subtract 1 before modulo to handle 1-indexing).

### Problem 10 — Happy Number

> 🔗 **LeetCode:** [202. Happy Number](https://leetcode.com/problems/happy-number/)
> **`[Pattern: Digit Sum Cycle]` `[Easy]`**
> Use a HashSet (Topic 2) or Floy's cycle detection (Topic 9) to detect if a sum-of-squares reaches 1 or loops.

---

## 🟡 Medium Tier — 15 Problems (Interview Math)

### Problem 11 — GCD of Array

> 🔗 **Practice:** Find the GCD of an entire array by applying `gcd(currentGCD, nextVal)`.

### Problem 12 — Sieve of Eratosthenes (Range Primes)

> 🔗 **Practice:** Print all primes in range [L, R] where `R <= 10⁶`. (Hint: Standard sieve is fine).

### Problem 13 — Segmented Sieve (Preview)

> 🔗 **Practice:** Find primes in range [L, R] where `L, R` can be up to 10¹² but `R - L` is small (10⁵). (Hint: Sieve up to √R, then mark range).

### Problem 14 — Modular Arithmetic Laws

Write a function `multiply(long a, long b, long m)` that safely returns `(a * b) % m` when `a * b` might exceed `Long.MAX_VALUE`.

### Problem 15 — Fast Exponentiation (Binary Exponentiation)

> 🔗 **LeetCode:** [50. Pow(x, n)](https://leetcode.com/problems/powx-n/)
> **`[Pattern: Divide & Conquer / Binary Exponentiation]` `[Google] [Amazon]` `[Medium]`**
> Implement in O(log n). Handle negative `n`. The core of modular exponentiation.

### Problem 16 — Modular Exponentiation

> 🔗 **Practice:** Compute `(a^b) % m` using Binary Exponentiation. This is used in RSA and competition math.

### Problem 17 — Perfect Number

> 🔗 **LeetCode:** [507. Perfect Number](https://leetcode.com/problems/perfect-number/)
> **`[Pattern: Sum of Divisors]` `[Easy/Medium]`**

### Problem 18 — Unique Binary Search Trees (Catalan Numbers)

> 🔗 **LeetCode:** [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)
> **`[Pattern: Combinatorics / DP]` `[Medium]`**
> Find number of unique BSTs with `n` nodes. Catalan(n) = (2n)! / ((n+1)! \* n!).

### Problem 19 — Pascal’s Triangle I

> 🔗 **LeetCode:** [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)
> **`[Pattern: Combinatorics / 2D DP]` `[Easy/Medium]`**
> Generate the first `n` rows. `current[j] = prev[j-1] + prev[j]`.

### Problem 20 — Pascal’s Triangle II (Space Optimized)

> 🔗 **LeetCode:** [119. Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)
> **`[Pattern: 1D DP / Row Formula]` `[Medium]`**
> Return the k-th row in O(k) space. (Hint: Use `nCr = nCr-1 * (n-r+1)/r`).

### Problem 21 — Permutation Sequence

> 🔗 **LeetCode:** [60. Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)
> **`[Pattern: Factorial Number System]` `[Hard]`**
> Return the k-th permutation of [1..n] in O(n²) without generating all.

### Problem 22 — Multiply Strings

> 🔗 **LeetCode:** [43. Multiply Strings](https://leetcode.com/problems/multiply-strings/)
> **`[Pattern: Long Multiplication]` `[Medium]`**
> Multiply two large numbers given as strings. (O(N\*M) - school method).

### Problem 23 — Check if Straight Line

> 🔗 **LeetCode:** [1232. Check Straight Line](https://leetcode.com/problems/check-if-it-is-a-straight-line/)
> **`[Pattern: Slope / Cross Product]` `[Easy/Medium]`**
> `(y2-y1)/(x2-x1) == (y3-y2)/(x3-x2)`. Use cross product to avoid division by zero: `(y2-y1)*(x3-x2) == (y3-y2)*(x2-x1)`.

### Problem 24 — Integer to Roman

> 🔗 **LeetCode:** [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)
> **`[Pattern: Greedy / Subtraction]` `[Medium]`**

### Problem 25 — Roman to Integer

> 🔗 **LeetCode:** [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/)
> **`[Pattern: Subtraction Rule]` `[Easy]`**

---

## 🔴 Challenge Zone — 5 Advanced Problems

### P31-35: The Competition Tier

- **P31: Modular Multiplicative Inverse**: Solve `(a * x) % m = 1`. Use Fermat's Little Theorem (requires `m` prime) or Extended Euclidean.
- **P32: Chinese Remainder Theorem (Simplified)**: Solve for `x` where `x % m1 = a1` and `x % m2 = a2`.
- **P33: Count Primes with Memory Optimization**: Implement Sieve using `BitSet` or `int[]` with bit manipulation to save 8x space.
- **P34: Fibonacci mod M for large N**: Use **Matrix Exponentiation** to find `Fib(n) % m` in O(log n).
- **P35: Count Anagrams with Factorials**: "How many unique permutations of MISSISSIPPI?" (Hint: `N! / (n1! * n2! * ...)`).

---

## 📊 Complexity Analysis Exercises — 6 Snippets

Determine the Time Complexity.

```java
// Snippet 1
for (int i = 2; i * i <= n; i++) {
    if (n % i == 0) return false;
}

// Snippet 2 — Sieve
for (int p = 2; p * p <= n; p++) {
    if (prime[p] == true) {
        for (int i = p * p; i <= n; i += p)
            prime[i] = false;
    }
}

// Snippet 3 — Binary Exponentiation
long pow(long a, long b) {
    long res = 1;
    while (b > 0) {
        if (b % 2 == 1) res *= a;
        a *= a;
        b /= 2;
    }
    return res;
}

// Snippet 4 — Excel Column Title (n characters)
// while (n > 0) { char c = (char)('A' + (n - 1) % 26); n = (n - 1) / 26; }

// Snippet 5 — Euclidean GCD
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}

// Snippet 6 — Pascal's Triangle Row N
for (int i = 0; i < n; i++) {
    // calculate nCi iteratively
}
```

**Complexity Answers:**

1. **O(√N)**. Standard primality check complexity.
2. **O(N log log N)**. Sieve mathematical proof.
3. **O(log b)**. Each step halves the exponent.
4. **O(log₂₆ N)**. Base conversion complexity.
5. **O(log(min(a,b)))**. Fibonacci numbers represent the worst case for GCD.
6. **O(N)** Time, O(N) Space. Using the `nCr = nCr-1 * (n-r+1)/r` formula.

---

## ✅ Self-Assessment — True / False

1. Prime Factorization of N can be found in O(√N). → **True**.
2. Modular arithmetic: `(a / b) % m == (a % m / b % m) % m`. → **False** (Requires Modular Inverse).
3. The number of primes less than N is approximately `N / log N`. → **True** (Prime Number Theorem).
4. `gcd(a, b) * lcm(a, b) = a * b`. → **True**.
5. Pascal's Triangle row 5 has 6 elements. → **True** (Row N has N+1 elements).
6. Binary exponentiation is only used for integers. → **False** (Can be used for matrices, polynomials, etc.).
7. `a % m` is always positive in Java for negative `a`. → **False** (Can be negative; use `(a % m + m) % m`).
8. Sieve of Eratosthenes uses O(N) space. → **True**.

---

## 🧠 Conceptual Mastery Questions

1. **Why √N?**: Intuitively, why do factors always occur in pairs around the √N mark?
2. **Overflow Prevention**: Why is it critical to use `(a % m * b % m) % m` when dealing with large products? What is the `long` range in Java?
3. **Euclidean Efficiency**: Why is the Euclidean algorithm so much faster than subtracting `b` from `a` repeatedly?
4. **Sieve Memory**: If N = 10⁹, can you use Sieve? Why or why not? (Hint: 1GB memory limit).
5. **Modular Inverse Requirement**: Why does the Modular Inverse `x` only exist if `gcd(a, m) = 1`?

---

Next: **Phase 2 — Data Structures & Arrays** (Topic 8)
