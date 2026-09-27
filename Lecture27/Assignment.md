# 🎒 Assignment 27 — Dynamic Programming III — Knapsack & Subsets

> **Lecture:** 27 of 38 — Dynamic Programming III — Knapsack & Subsets
> **Phase:** 4 — Dynamic Programming
> **Estimated Time:** 6 days · **Total Problems:** 25 (8 Easy · 13 Medium · 4 Hard)
> **Goal:** See the bag hiding in the wording, then let the loop order decide which knapsack you are solving.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                  | Pattern            | Move                                 |
| -------------------------------------- | ------------------ | ------------------------------------ |
| "each item at most once", exact target | 0/1 Knapsack       | capacity loop **backwards**          |
| "coins / items may repeat"             | Unbounded Knapsack | capacity loop **forwards**           |
| "there are k copies of each item"      | Bounded Knapsack   | binary-split the copies, then 0/1    |
| "split into two equal halves"          | Subset Sum         | target is `total / 2`, boolean table |
| "how many ways" and order matters      | Permutation Count  | target outside, items inside         |
| n ≤ 30 but the sums are enormous       | Meet in the Middle | enumerate halves, then search        |

---

## 🟢 Easy Tier (8 Problems)

_Selection and partition warm-ups: totals, bounds and picking a subset by rule._

### E1 · Partition Array Into Three Parts With Equal Sum

**🔗 [LC 1013 — Partition Array Into Three Parts With Equal Sum](https://leetcode.com/problems/partition-array-into-three-parts-with-equal-sum/)** · Easy
**Pattern:** Prefix Sums + Partition | **Companies:** Amazon

**Hint:** The total must divide by three. Sweep once, cutting whenever the running sum reaches a third — and make sure two cuts happen before the array ends.

---

### E2 · Find Subsequence of Length K With the Largest Sum

**🔗 [LC 2099 — Find Subsequence of Length K With the Largest Sum](https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/)** · Easy
**Pattern:** Select by Value, Restore Order | **Companies:** Amazon, Google

**Hint:** Pick the k largest by value, then output them in their original order. Selection with a constraint — the simplest form of "choose a subset".

---

### E3 · Maximum Product Difference Between Two Pairs

**🔗 [LC 1913 — Maximum Product Difference Between Two Pairs](https://leetcode.com/problems/maximum-product-difference-between-two-pairs/)** · Easy
**Pattern:** Sort and Take the Ends | **Companies:** Amazon

**Hint:** The best pair is the two largest, the worst the two smallest. Sorting makes it obvious; a single pass tracking four values is O(n).

---

### E4 · Kids With the Greatest Number of Candies

**🔗 [LC 1431 — Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)** · Easy
**Pattern:** Compare Against the Maximum | **Companies:** Amazon

**Hint:** Find the maximum once, then test each child with `candies[i] + extra >= max`. Precomputing the bound is the habit every knapsack needs.

---

### E5 · Number of Common Factors

**🔗 [LC 2427 — Number of Common Factors](https://leetcode.com/problems/number-of-common-factors/)** · Easy
**Pattern:** Bounded Counting | **Companies:** Amazon

**Hint:** Count divisors of the smaller number that also divide the larger, or go up to `gcd(a, b)`. A fixed, small search space.

---

### E6 · Three Divisors

**🔗 [LC 1952 — Three Divisors](https://leetcode.com/problems/three-divisors/)** · Easy
**Pattern:** Divisor Counting | **Companies:** Amazon

**Hint:** A number has exactly three divisors only when it is the square of a prime. Test with a loop to `sqrt(n)` — Lecture 7 arithmetic in a Phase 4 wrapper.

---

### E7 · Count Elements With Maximum Frequency

**🔗 [LC 3005 — Count Elements With Maximum Frequency](https://leetcode.com/problems/count-elements-with-maximum-frequency/)** · Easy
**Pattern:** Frequency of Frequencies | **Companies:** Amazon

**Hint:** Count values, find the highest count, then total the values that reach it. Counting first, deciding second.

---

### E8 · Minimum Common Value

**🔗 [LC 2540 — Minimum Common Value](https://leetcode.com/problems/minimum-common-value/)** · Easy
**Pattern:** Two Pointers on Sorted Arrays | **Companies:** Amazon

**Hint:** Both arrays are sorted, so walk them together and advance the smaller side. The merge step you already know from Lecture 9.

---

## 🟡 Medium Tier (13 Problems)

_The three variants, and the word problems that hide them._

### M1 · Partition Equal Subset Sum

**🔗 [LC 416 — Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)** · Medium
**Pattern:** 0/1 Knapsack (Feasibility) | **Companies:** Amazon, Google, Meta

**Hint:** Odd total means false. Otherwise ask whether any subset reaches `total / 2`, with a boolean table and a backwards capacity loop.

---

### M2 · Coin Change II

**🔗 [LC 518 — Coin Change II](https://leetcode.com/problems/coin-change-ii/)** · Medium
**Pattern:** Unbounded Knapsack (Count) | **Companies:** Amazon, Google, Meta

**Hint:** `dp[0] = 1`, coins in the outer loop and amounts inner and forward. That nesting is what counts combinations rather than orderings.

---

### M3 · Combination Sum IV

**🔗 [LC 377 — Combination Sum IV](https://leetcode.com/problems/combination-sum-iv/)** · Medium
**Pattern:** Unbounded (Permutations) | **Companies:** Google, Amazon, Meta

**Hint:** Same arithmetic as Coin Change II with the loops swapped: target outside, numbers inside, because order matters here.

---

### M4 · Last Stone Weight II

**🔗 [LC 1049 — Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/)** · Medium
**Pattern:** 0/1 Knapsack (Minimise Gap) | **Companies:** Amazon, Google

**Hint:** Every smash assigns a sign, so the answer is `total − 2 × bestPile` where the pile is the largest reachable sum at most `total / 2`.

---

### M5 · Ones and Zeroes

**🔗 [LC 474 — Ones and Zeroes](https://leetcode.com/problems/ones-and-zeroes/)** · Medium
**Pattern:** 0/1 Knapsack, 2D Capacity | **Companies:** Google, Amazon

**Hint:** Each string costs zeros and ones. Keep `dp[zeros][ones]` and run both capacity loops backwards.

---

### M6 · Number of Dice Rolls With Target Sum

**🔗 [LC 1155 — Number of Dice Rolls With Target Sum](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/)** · Medium
**Pattern:** Counting Knapsack | **Companies:** Amazon, Google

**Hint:** `dp[d][t]` counts ways to reach total `t` with `d` dice. Each die contributes faces 1..k; take the modulus as you go.

---

### M7 · Integer Break

**🔗 [LC 343 — Integer Break](https://leetcode.com/problems/integer-break/)** · Medium
**Pattern:** Unbounded Cutting | **Companies:** Amazon, Google

**Hint:** `dp[i] = max(j × (i − j), j × dp[i − j])` over all cuts `j`. The maths shortcut — cut into 3s — is worth deriving afterwards.

---

### M8 · Partition to K Equal Sum Subsets

**🔗 [LC 698 — Partition to K Equal Sum Subsets](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/)** · Medium
**Pattern:** Bitmask Search, Not Knapsack | **Companies:** Google, Amazon, Meta

**Hint:** Each subset must reach `total / k`. Sort descending and backtrack with pruning, or use a bitmask over used elements — a knapsack table cannot express "k equal groups".

---

### M9 · Closest Dessert Cost

**🔗 [LC 1774 — Closest Dessert Cost](https://leetcode.com/problems/closest-dessert-cost/)** · Medium
**Pattern:** Bounded Knapsack | **Companies:** Amazon

**Hint:** Base flavours are a fixed choice; each topping may be taken 0, 1 or 2 times. Enumerate reachable costs and keep the one closest to target, preferring the smaller on ties.

---

### M10 · Count Ways To Build Good Strings

**🔗 [LC 2466 — Count Ways To Build Good Strings](https://leetcode.com/problems/count-ways-to-build-good-strings/)** · Medium
**Pattern:** Unbounded Counting | **Companies:** Amazon, Google

**Hint:** `dp[i] = dp[i − zero] + dp[i − one]`, summed over the allowed lengths. A counting knapsack where the items are two step sizes.

---

### M11 · Check if There is a Valid Partition For The Array

**🔗 [LC 2369 — Check if There is a Valid Partition For The Array](https://leetcode.com/problems/check-if-there-is-a-valid-partition-for-the-array/)** · Medium
**Pattern:** Partition DP | **Companies:** Amazon, Google

**Hint:** `dp[i]` is true when the first `i` elements can be split validly. Check the last two or three elements against the three allowed shapes.

---

### M12 · Partition Array for Maximum Sum

**🔗 [LC 1043 — Partition Array for Maximum Sum](https://leetcode.com/problems/partition-array-for-maximum-sum/)** · Medium
**Pattern:** Partition into Windows | **Companies:** Amazon, Google

**Hint:** `dp[i] = max over the last k elements of dp[i − k] + k × (max of that window)`. The inner loop both sizes the window and tracks its maximum.

---

### M13 · Filling Bookcase Shelves

**🔗 [LC 1105 — Filling Bookcase Shelves](https://leetcode.com/problems/filling-bookcase-shelves/)** · Medium
**Pattern:** Sequential Partition | **Companies:** Amazon, Google

**Hint:** Books must stay in order, so `dp[i]` is the cheapest shelving of the first `i` books; extend the last shelf backwards while the width allows, tracking its height.

---

## 🔴 Hard Tier (4 Problems)

_When the table is too big, or the state is not a capacity at all._

### H1 · Partition Array Into Two Arrays to Minimize Sum Difference

**🔗 [LC 2035 — Partition Array Into Two Arrays to Minimize Sum Difference](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/)** · Hard
**Pattern:** Meet in the Middle | **Companies:** Google, Amazon

**Hint:** n is up to 30, so a full knapsack is too big. Enumerate subset sums of each half, sort one side, and binary search for the closest complement.

---

### H2 · Tallest Billboard

**🔗 [LC 956 — Tallest Billboard](https://leetcode.com/problems/tallest-billboard/)** · Hard
**Pattern:** Knapsack Keyed on Difference | **Companies:** Google, Amazon

**Hint:** State is the gap between the piles; the value stored is the shorter pile. Each rod goes on the taller side, the shorter side, or neither.

---

### H3 · Profitable Schemes

**🔗 [LC 879 — Profitable Schemes](https://leetcode.com/problems/profitable-schemes/)** · Hard
**Pattern:** Two-Capacity Counting | **Companies:** Google, Amazon

**Hint:** `dp[members][profit]` counts schemes, with profit capped at the minimum required. Both loops backwards, modulo 1e9+7.

---

### H4 · Form Largest Integer With Digits That Add up to Target

**🔗 [LC 1449 — Form Largest Integer With Digits That Add up to Target](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/)** · Hard
**Pattern:** Unbounded Knapsack + Reconstruction | **Companies:** Google, Amazon

**Hint:** First fill `dp[target]` with the most digits affordable, then build the number greedily from digit 9 down, spending cost while the remaining budget still allows the rest.

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Loop direction:** Why must the 0/1 capacity loop run backwards? Give a two-element input where the forward version is wrong.
2. **Nesting:** State which nesting counts combinations and which counts permutations, and explain why with {1,2} summing to 3.
3. **Reduction:** Derive the Target Sum reduction from `P − N = target` and `P + N = total`. When are there no solutions?
4. **Base cases:** For feasibility, counting, maximising and minimising, what is `dp[0]` in each case?
5. **Pseudo-polynomial:** O(n · capacity) sounds polynomial. Explain why it is not, in terms of the input size.
6. **When knapsack fails:** Partition to K Equal Sum Subsets is not a knapsack. What about the question breaks the table?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon** | [Partition Array Into Two Arrays to Minimize Sum Difference](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/), [Tallest Billboard](https://leetcode.com/problems/tallest-billboard/), [Profitable Schemes](https://leetcode.com/problems/profitable-schemes/), [Form Largest Integer With Digits That Add up to Target](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/) |
| **Google** | [Partition Array Into Two Arrays to Minimize Sum Difference](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/), [Tallest Billboard](https://leetcode.com/problems/tallest-billboard/), [Profitable Schemes](https://leetcode.com/problems/profitable-schemes/), [Form Largest Integer With Digits That Add up to Target](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/) |
| **Meta**   | [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/), [Coin Change II](https://leetcode.com/problems/coin-change-ii/), [Combination Sum IV](https://leetcode.com/problems/combination-sum-iv/), [Partition to K Equal Sum Subsets](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/)                                                                                                                   |

---

## ✅ Completion Checklist

- [ ] All 8 Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] All 6 conceptual questions answered out loud
- [ ] I can name the items, capacity and objective of a disguised problem in under a minute
- [ ] I can write all three knapsack variants with the correct loop order from memory

---

**← [Lecture 26 · Dynamic Programming II — Grids & Strings](../Lecture26/Assignment.md)** &nbsp;·&nbsp; **[Lecture 28 · Dynamic Programming IV — Interval, Tree, Bitmask & Digit](../Lecture28/Assignment.md) →**
