# 🧩 Assignment 32 — Dynamic Programming I — Foundations & 1D

> **Lecture:** 32 of 45 — Dynamic Programming I — Foundations & 1D
> **Phase:** 4 — Dynamic Programming
> **Estimated Time:** 6 days · **Total Problems:** 25 (10 Easy · 12 Medium · 3 Hard)
> **Goal:** Write the recursion, spot the repeats, add the memo — then turn it into a table and squeeze the space.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                     | Pattern             | Move                                          |
| ----------------------------------------- | ------------------- | --------------------------------------------- |
| "maximum / minimum / number of ways"      | Dynamic Programming | write the recursion, then memoise it          |
| "choose each item: take it or skip it"    | Take or Skip        | `dp[i] = max(dp[i-1], dp[i-2] + value)`       |
| "make exactly this amount, reuse allowed" | Unbounded Choice    | loop amounts forward over the items           |
| "longest increasing / chain / divisible"  | LIS                 | best ending at i, or patience + binary search |
| "buy, sell, cooldown, fee, k times"       | DP over States      | one variable per situation per day            |
| a choice that blocks a range after it     | Suffix DP           | fill the table from the end backwards         |

---

## 🟢 Easy Tier (10 Problems)

_Small recurrences, where the state is obvious and the table is short._

### E1 · Divisor Game

**🔗 [LC 1025 — Divisor Game](https://leetcode.com/problems/divisor-game/)** · Easy
**Pattern:** Recurrence + Base Case | **Companies:** Amazon, Google

**Hint:** Write `dp[n] = true if some divisor makes dp[n - x] false`. Compute the first few by hand — the pattern that emerges is the one-line answer worth proving.

---

### E2 · Is Subsequence

**🔗 [LC 392 — Is Subsequence](https://leetcode.com/problems/is-subsequence/)** · Easy
**Pattern:** Two Pointers or DP | **Companies:** Amazon, Google, Meta

**Hint:** Greedy two pointers is O(n). Also write the DP version, `dp[i][j]`, because the follow-up (many queries against one long text) is what the table is for.

---

### E3 · Get Maximum in Generated Array

**🔗 [LC 1646 — Get Maximum in Generated Array](https://leetcode.com/problems/get-maximum-in-generated-array/)** · Easy
**Pattern:** Direct Recurrence | **Companies:** Amazon

**Hint:** The definition is the recurrence: even indices copy, odd indices add. Build the array to `n` and take the maximum.

---

### E4 · Maximum Difference Between Increasing Elements

**🔗 [LC 2016 — Maximum Difference Between Increasing Elements](https://leetcode.com/problems/maximum-difference-between-increasing-elements/)** · Easy
**Pattern:** Prefix Minimum | **Companies:** Amazon, Google

**Hint:** Keep the smallest value seen so far and, for every later element, try `nums[i] − minSoFar`. It is the Best Time to Buy and Sell Stock skeleton.

---

### E5 · Maximum Score After Splitting a String

**🔗 [LC 1422 — Maximum Score After Splitting a String](https://leetcode.com/problems/maximum-score-after-splitting-a-string/)** · Easy
**Pattern:** Prefix Counts | **Companies:** Amazon

**Hint:** Count zeros on the left and ones on the right in one pass each; then every split is O(1). Remember both sides must be non-empty.

---

### E6 · Maximum Value of an Ordered Triplet I

**🔗 [LC 2873 — Maximum Value of an Ordered Triplet I](https://leetcode.com/problems/maximum-value-of-an-ordered-triplet-i/)** · Easy
**Pattern:** Prefix Max + Running Best | **Companies:** Amazon, Google

**Hint:** For each middle index, you need the best `i` before it and the best `k` after it. Keep a running maximum from the left and a running maximum from the right.

---

### E7 · Minimum Changes To Make Alternating Binary String

**🔗 [LC 1758 — Minimum Changes To Make Alternating Binary String](https://leetcode.com/problems/minimum-changes-to-make-alternating-binary-string/)** · Easy
**Pattern:** Count Both Targets | **Companies:** Amazon

**Hint:** Only two possible final strings exist. Count mismatches against one of them; the other costs `n − that`. Take the smaller.

---

### E8 · Minimum Cost to Move Chips to The Same Position

**🔗 [LC 1217 — Minimum Cost to Move Chips to The Same Position](https://leetcode.com/problems/minimum-cost-to-move-chips-to-the-same-position/)** · Easy
**Pattern:** Parity Counting | **Companies:** Amazon, Google

**Hint:** Moves of two are free, so only parity matters: count chips on even and odd positions, and move the smaller group.

---

### E9 · Longest Unequal Adjacent Groups Subsequence I

**🔗 [LC 2900 — Longest Unequal Adjacent Groups Subsequence I](https://leetcode.com/problems/longest-unequal-adjacent-groups-subsequence-i/)** · Easy
**Pattern:** Take or Skip | **Companies:** Amazon

**Hint:** Walk the array keeping the last group taken; take a word whenever its group differs from that one. A greedy pass that is also the simplest DP.

---

### E10 · Maximum Repeating Substring

**🔗 [LC 1668 — Maximum Repeating Substring](https://leetcode.com/problems/maximum-repeating-substring/)** · Easy
**Pattern:** Try Every Count | **Companies:** Amazon

**Hint:** `k` is small: test repetitions 1, 2, 3 … while the repeated word is still a substring. The DP framing is `dp[k] = dp[k−1] + 1` when the longer copy still fits.

---

## 🟡 Medium Tier (12 Problems)

_The five 1D families: take-or-skip, unbounded choice, ending-here, state machines and suffixes._

### M1 · Coin Change

**🔗 [LC 322 — Coin Change](https://leetcode.com/problems/coin-change/)** · Medium
**Pattern:** Unbounded Choice | **Companies:** Amazon, Google, Meta

**Hint:** `dp[a] = 1 + min(dp[a − coin])`. Seed `dp[0] = 0`, treat unreachable as infinity, and loop amounts forward so coins can repeat.

---

### M2 · House Robber II

**🔗 [LC 213 — House Robber II](https://leetcode.com/problems/house-robber-ii/)** · Medium
**Pattern:** Linear DP, Twice | **Companies:** Amazon, Google, Microsoft

**Hint:** The circle only forbids robbing both ends. Run the straight-line House Robber on `[0, n−2]` and on `[1, n−1]`, and take the better.

---

### M3 · Word Break

**🔗 [LC 139 — Word Break](https://leetcode.com/problems/word-break/)** · Medium
**Pattern:** Reachability DP | **Companies:** Amazon, Google, Meta

**Hint:** `dp[i]` is true when some `j < i` has `dp[j]` true and `s[j..i)` is in the dictionary. Put the dictionary in a set first.

---

### M4 · Longest Increasing Subsequence

**🔗 [LC 300 — Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)** · Medium
**Pattern:** LIS / Patience | **Companies:** Amazon, Google, Meta

**Hint:** `dp[i]` is the best subsequence ending at `i` — O(n²). For O(n log n), binary search each value into a `tails` array.

---

### M5 · Perfect Squares

**🔗 [LC 279 — Perfect Squares](https://leetcode.com/problems/perfect-squares/)** · Medium
**Pattern:** Unbounded Choice | **Companies:** Amazon, Google

**Hint:** Same shape as Coin Change with coins `1, 4, 9, 16, …`. `dp[i] = 1 + min(dp[i − square])` for every square at most `i`.

---

### M6 · Arithmetic Slices

**🔗 [LC 413 — Arithmetic Slices](https://leetcode.com/problems/arithmetic-slices/)** · Medium
**Pattern:** Ending Exactly Here | **Companies:** Amazon, Google

**Hint:** `dp[i]` counts arithmetic slices ending at `i`: if the difference continues, `dp[i] = dp[i−1] + 1`, else 0. Sum the table.

---

### M7 · Largest Divisible Subset

**🔗 [LC 368 — Largest Divisible Subset](https://leetcode.com/problems/largest-divisible-subset/)** · Medium
**Pattern:** Sort + LIS Shape | **Companies:** Amazon, Google

**Hint:** Sort first, so divisibility only needs checking against earlier elements. Then it is LIS with `nums[i] % nums[j] == 0`, plus parent pointers to rebuild the subset.

---

### M8 · Number of Longest Increasing Subsequence

**🔗 [LC 673 — Number of Longest Increasing Subsequence](https://leetcode.com/problems/number-of-longest-increasing-subsequence/)** · Medium
**Pattern:** LIS + Counting | **Companies:** Google, Amazon, Meta

**Hint:** Keep two tables: the length ending at `i` and how many ways achieve it. On a strictly longer candidate, copy the count; on a tie, add it.

---

### M9 · Best Time to Buy and Sell Stock with Cooldown

**🔗 [LC 309 — Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)** · Medium
**Pattern:** DP over States | **Companies:** Google, Amazon, Meta

**Hint:** Three running values — holding, just sold, free. Compute today's `sold` from yesterday's `hold`, and today's `rest` from yesterday's `sold`.

---

### M10 · Best Time to Buy and Sell Stock with Transaction Fee

**🔗 [LC 714 — Best Time to Buy and Sell Stock with Transaction Fee](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/)** · Medium
**Pattern:** DP over States | **Companies:** Amazon, Google

**Hint:** Two states, `hold` and `free`. Pay the fee on the sale: `free = max(free, hold + price − fee)`.

---

### M11 · Minimum Cost For Tickets

**🔗 [LC 983 — Minimum Cost For Tickets](https://leetcode.com/problems/minimum-cost-for-tickets/)** · Medium
**Pattern:** Choose the Pass Length | **Companies:** Google, Amazon

**Hint:** `dp[day]` is the cheapest cover through that day. For a travel day, take the minimum of buying a 1-, 7- or 30-day pass; for other days, copy the previous value.

---

### M12 · Solving Questions With Brainpower

**🔗 [LC 2140 — Solving Questions With Brainpower](https://leetcode.com/problems/solving-questions-with-brainpower/)** · Medium
**Pattern:** Suffix DP | **Companies:** Google, Amazon

**Hint:** Fill from the end: `dp[i] = max(points + dp[i + brainpower + 1], dp[i + 1])`. Clamp the jump to `n`, and use 64-bit totals.

---

## 🔴 Hard Tier (3 Problems)

_A second dimension: transactions, sorted pairs, and jump sizes._

### H1 · Best Time to Buy and Sell Stock IV

**🔗 [LC 188 — Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)** · Hard
**Pattern:** DP over Transactions | **Companies:** Google, Amazon, Meta

**Hint:** Keep `buy[t]` and `sell[t]` for each transaction count and update them for every price. When `k ≥ n / 2` the limit is meaningless — sum every rise instead.

---

### H2 · Russian Doll Envelopes

**🔗 [LC 354 — Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)** · Hard
**Pattern:** Sort + LIS | **Companies:** Google, Amazon, Meta

**Hint:** Sort by width ascending and height descending, so equal widths cannot chain. Then the answer is the LIS of the heights, in O(n log n).

---

### H3 · Frog Jump

**🔗 [LC 403 — Frog Jump](https://leetcode.com/problems/frog-jump/)** · Hard
**Pattern:** DP over (Stone, Jump) | **Companies:** Google, Amazon, Meta

**Hint:** The state is the stone plus the jump that reached it. Store, for each stone, the set of jump sizes that can arrive; from each, try `k−1`, `k` and `k+1`.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — Fibonacci, plain recursion

// Snippet 2 — Fibonacci with memoisation

// Snippet 3 — Fibonacci bottom-up with two variables

// Snippet 4 — climbing stairs with steps of 1 to k

// Snippet 5 — house robber, bottom-up

// Snippet 6 — longest increasing subsequence, O(n²) DP
```

**Complexity Answers:**

1. **O(2ⁿ)** time, O(n) space.
2. **O(n)** time, **O(n)** space.
3. **O(n)** time, **O(1)** space.
4. **O(n · k)**.
5. **O(n)** time, O(1) space.
6. **O(n²)** time, O(n) space.

---

## 🔍 Self-Assessment — True / False

1. Dynamic programming needs overlapping subproblems. → **True** — otherwise there is nothing to reuse
2. Memoisation and tabulation always have the same Big-O. → **False** — usually they do, but memoisation only computes the states it actually reaches, so it can be faster when few of them are needed
3. Every recursive problem benefits from memoisation. → **False** — only when the same arguments repeat
4. A 1D DP can often be reduced to O(1) space. → **True** — when each state needs only the last few
5. The DP state is defined by the question "what must I know to finish?" → **True**
6. Greedy and DP always give the same answer. → **False** — DP considers all choices; greedy commits to one

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The two signals:** Name them, and give a problem that has one but not the other.
2. **State definition:** For LIS, why does "best over the first i" fail where "best ending at i" works?
3. **Memo keys:** What must the memo key contain? Give an example where forgetting part of the key gives a subtly wrong answer.
4. **Loop order:** In bottom-up Coin Change, why does the amount loop run forward? What would a backward loop mean?
5. **Space:** When can a DP table be reduced to O(1) variables, and when can it not?
6. **DP vs greedy:** Coin Change with {1, 3, 4} beats greedy. Explain, in terms of the two signals, why DP is needed.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Get Maximum in Generated Array](https://leetcode.com/problems/get-maximum-in-generated-array/), [Longest Unequal Adjacent Groups Subsequence I](https://leetcode.com/problems/longest-unequal-adjacent-groups-subsequence-i/), [Maximum Repeating Substring](https://leetcode.com/problems/maximum-repeating-substring/), [Maximum Score After Splitting a String](https://leetcode.com/problems/maximum-score-after-splitting-a-string/) |
| **Google**    | [Arithmetic Slices](https://leetcode.com/problems/arithmetic-slices/), [Best Time to Buy and Sell Stock with Transaction Fee](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/), [Largest Divisible Subset](https://leetcode.com/problems/largest-divisible-subset/), [Minimum Cost For Tickets](https://leetcode.com/problems/minimum-cost-for-tickets/)                                               |
| **Meta**      | [Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/), [Frog Jump](https://leetcode.com/problems/frog-jump/), [Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/), [Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)                                                             |
| **Microsoft** | [House Robber II](https://leetcode.com/problems/house-robber-ii/)                                                                                                                                                                                                                                                                                                                                                                          |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved
- [ ] All 12 Medium problems solved
- [ ] All 3 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can climb all four steps — recursion, memo, table, rolling — on a new problem
- [ ] I can write the dp definition as a sentence before writing any code

---

**← [Lecture 31 · Union-Find (Disjoint Set Union)](../Lecture31/Assignment.md)** &nbsp;·&nbsp; **[Lecture 33 · Dynamic Programming II — Grids & Strings](../Lecture33/Assignment.md) →**
