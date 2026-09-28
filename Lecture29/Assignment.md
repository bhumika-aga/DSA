# 💡 Assignment 22 — Greedy Algorithms

> **Lecture:** 29 of 45 — Greedy Algorithms
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 5 days · **Total Problems:** 25 (8 Easy · 13 Medium · 4 Hard)
> **Goal:** Find the rule, try to break it, prove it with an exchange argument — then write the five lines of code.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                        | Pattern                  | Move                                    |
| -------------------------------------------- | ------------------------ | --------------------------------------- |
| "maximum number of non-overlapping"          | Sort by End              | earliest finish leaves the most room    |
| "match two sets", "fit the most"             | Sort Both + Two Pointers | spend the smallest resource that works  |
| "minimum steps to reach"                     | Track the Reach          | frontier scan — BFS with two integers   |
| "take now, may not afford later"             | Greedy with Regret       | heap: take everything, drop the worst   |
| "largest / smallest number after k changes"  | Digit or Letter Greedy   | fix the most significant position first |
| a local best that blocks a better global one | **Not** greedy           | switch to DP — Lectures 25–28           |

---

## 🟢 Easy Tier (8 Problems)

_One sort, one pass, one counter. Say the rule out loud before coding._

### E1 · Assign Cookies

**🔗 [LC 455 — Assign Cookies](https://leetcode.com/problems/assign-cookies/)** · Easy
**Pattern:** Two-Pointer Matching | **Companies:** Amazon, Google

**Hint:** Sort both arrays and walk them together, giving each child the smallest cookie that satisfies them. A cookie too small for the current child is too small for everyone left.

---

### E2 · Maximum Units on a Truck

**🔗 [LC 1710 — Maximum Units on a Truck](https://leetcode.com/problems/maximum-units-on-a-truck/)** · Easy
**Pattern:** Sort by Value Density | **Companies:** Amazon, Google

**Hint:** Sort box types by units per box, descending, and fill the truck from the top. Every truck slot should carry as many units as possible — the fractional-knapsack rule.

---

### E3 · Lemonade Change

**🔗 [LC 860 — Lemonade Change](https://leetcode.com/problems/lemonade-change/)** · Easy
**Pattern:** Spend the Least Flexible Bill | **Companies:** Amazon, Google

**Hint:** Track only fives and tens. For a $20, prefer a ten plus a five over three fives: fives are change for everything, so hold on to them.

---

### E4 · Can Place Flowers

**🔗 [LC 605 — Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)** · Easy
**Pattern:** Scan with Neighbour Checks | **Companies:** Amazon, Adobe

**Hint:** Plant at the first spot where the plot and both neighbours are empty (treat off-array as empty), then skip ahead. Planting as early as possible never blocks a later chance.

---

### E5 · Largest Perimeter Triangle

**🔗 [LC 976 — Largest Perimeter Triangle](https://leetcode.com/problems/largest-perimeter-triangle/)** · Easy
**Pattern:** Sort + Adjacent Triple | **Companies:** Amazon, Google

**Hint:** Sort descending. The first triple of adjacent values where `a < b + c` is the largest valid perimeter — non-adjacent choices only make the sum smaller.

---

### E6 · Minimum Cost of Buying Candies With Discount

**🔗 [LC 2144 — Minimum Cost of Buying Candies With Discount](https://leetcode.com/problems/minimum-cost-of-buying-candies-with-discount/)** · Easy
**Pattern:** Sort + Take Every Third | **Companies:** Amazon

**Hint:** Sort descending and buy in groups of three: pay for the two most expensive, take the third free. Free candies should always be the cheapest available.

---

### E7 · Maximise Sum Of Array After K Negations

**🔗 [LC 1005 — Maximize Sum Of Array After K Negations](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/)** · Easy
**Pattern:** Sort + Flip the Smallest | **Companies:** Amazon, Google

**Hint:** Sort ascending and flip negatives while `k` remains. If `k` is left over, spend it all on the smallest absolute value — flipping it twice is a no-op when `k` is even.

---

### E8 · Split a String in Balanced Strings

**🔗 [LC 1221 — Split a String in Balanced Strings](https://leetcode.com/problems/split-a-string-in-balanced-strings/)** · Easy
**Pattern:** Running Balance | **Companies:** Amazon, Microsoft

**Hint:** Count `+1` for one letter and `-1` for the other. Every time the balance returns to zero you can cut — splitting as early as possible maximises the number of pieces.

---

## 🟡 Medium Tier (13 Problems)

_The three shapes proper: sorting, reach, and greedy scans that need a proof._

### M1 · Jump Game II

**🔗 [LC 45 — Jump Game II](https://leetcode.com/problems/jump-game-ii/)** · Medium
**Pattern:** Frontier / Implicit BFS | **Companies:** Amazon, Google, Meta

**Hint:** Track the end of the current jump's range and the furthest index reachable with one more. Increment the jump count only when the index reaches the current end.

---

### M2 · Gas Station

**🔗 [LC 134 — Gas Station](https://leetcode.com/problems/gas-station/)** · Medium
**Pattern:** Running Total + Restart | **Companies:** Amazon, Google, Microsoft

**Hint:** If total gas is less than total cost, return −1. Otherwise restart the candidate at `i + 1` whenever the running tank dips below zero — every station in that failed stretch also fails.

---

### M3 · Wiggle Subsequence

**🔗 [LC 376 — Wiggle Subsequence](https://leetcode.com/problems/wiggle-subsequence/)** · Medium
**Pattern:** Count Direction Changes | **Companies:** Amazon, Google

**Hint:** Only the sign of each difference matters. Count how many times the direction flips; the answer is that count plus one, with equal neighbours skipped.

---

### M4 · Valid Parenthesis String

**🔗 [LC 678 — Valid Parenthesis String](https://leetcode.com/problems/valid-parenthesis-string/)** · Medium
**Pattern:** Range of Possible Open Counts | **Companies:** Amazon, Google, Meta

**Hint:** Track a lower and upper bound on the number of unmatched `(`. A `*` widens the range; the string is valid if the upper bound never goes negative and the lower bound ends at zero.

---

### M5 · Queue Reconstruction by Height

**🔗 [LC 406 — Queue Reconstruction by Height](https://leetcode.com/problems/queue-reconstruction-by-height/)** · Medium
**Pattern:** Sort by Height, Insert at k | **Companies:** Amazon, Google, Meta

**Hint:** Sort by height descending, `k` ascending, then insert each person at index `k`. Everyone already placed is at least as tall, so earlier placements stay correct.

---

### M6 · Monotone Increasing Digits

**🔗 [LC 738 — Monotone Increasing Digits](https://leetcode.com/problems/monotone-increasing-digits/)** · Medium
**Pattern:** Digit Scan + Borrow | **Companies:** Amazon, Google

**Hint:** Find the first place where a digit drops, decrement the digit before it, and set everything after to 9. Repeat leftwards while the decrement breaks monotonicity.

---

### M7 · Broken Calculator

**🔗 [LC 991 — Broken Calculator](https://leetcode.com/problems/broken-calculator/)** · Medium
**Pattern:** Work Backwards | **Companies:** Google, Amazon

**Hint:** Reverse the operations: from `target`, halve while even and add one while odd, until you reach `startValue`. Forward doubling has too many branches; backwards there is only one legal move.

---

### M8 · Most Profit Assigning Work

**🔗 [LC 826 — Most Profit Assigning Work](https://leetcode.com/problems/most-profit-assigning-work/)** · Medium
**Pattern:** Sort Both + Running Best | **Companies:** Amazon, Google

**Hint:** Sort jobs by difficulty and workers by ability, then sweep: keep the best profit among jobs the current worker can do. Both pointers only move forward.

---

### M9 · Best Time to Buy and Sell Stock II

**🔗 [LC 122 — Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)** · Medium
**Pattern:** Take Every Rise | **Companies:** Amazon, Google, Meta

**Hint:** Sum every positive difference between consecutive days. Any profitable multi-day hold equals the sum of its daily rises, so you never need to plan ahead.

---

### M10 · Boats to Save People

**🔗 [LC 881 — Boats to Save People](https://leetcode.com/problems/boats-to-save-people/)** · Medium
**Pattern:** Two Pointers from Both Ends | **Companies:** Amazon, Google, Meta

**Hint:** Sort, then pair the lightest with the heaviest. If they fit together, move both pointers; otherwise the heaviest travels alone. One boat per step either way.

---

### M11 · Non-decreasing Array

**🔗 [LC 665 — Non-decreasing Array](https://leetcode.com/problems/non-decreasing-array/)** · Medium
**Pattern:** Fix the Right Element | **Companies:** Amazon, Google

**Hint:** At the first drop, you may change one value. Lower `nums[i]` to `nums[i-1]` when that keeps the sequence valid; otherwise raise `nums[i+1]`. More than one fix means false.

---

### M12 · Hand of Straights

**🔗 [LC 846 — Hand of Straights](https://leetcode.com/problems/hand-of-straights/)** · Medium
**Pattern:** Counting Map + Smallest First | **Companies:** Amazon, Google

**Hint:** Count the cards. Repeatedly take the smallest remaining value as the start of a group and consume the next `groupSize − 1` consecutive values; a missing one means false.

---

### M13 · Smallest String With A Given Numeric Value

**🔗 [LC 1663 — Smallest String With A Given Numeric Value](https://leetcode.com/problems/smallest-string-with-a-given-numeric-value/)** · Medium
**Pattern:** Fill from the Back | **Companies:** Amazon, Google

**Hint:** Start with all `a`s, then walk from the right raising letters to `z` while the remaining budget demands it. Pushing weight to the end keeps the string smallest.

---

## 🔴 Hard Tier (4 Problems)

_Greedy with regret, and greedy that borrows from another pattern._

### H1 · Course Schedule III

**🔗 [LC 630 — Course Schedule III](https://leetcode.com/problems/course-schedule-iii/)** · Hard
**Pattern:** Sort by Deadline + Max-Heap | **Companies:** Google, Amazon, Meta

**Hint:** Process courses in deadline order, taking each one optimistically. When the total time passes the deadline, drop the longest course taken so far — the count stays, the time is reclaimed.

---

### H2 · Minimum Number of Refueling Stops

**🔗 [LC 871 — Minimum Number of Refueling Stops](https://leetcode.com/problems/minimum-number-of-refueling-stops/)** · Hard
**Pattern:** Max-Heap of Passed Stations | **Companies:** Google, Amazon

**Hint:** Drive as far as the fuel allows, pushing every station you pass into a max-heap. When you run dry, refuel at the largest station passed. Each refuel is a regret decision.

---

### H3 · Minimum Number of Taps to Open to Water a Garden

**🔗 [LC 1326 — Minimum Number of Taps to Open to Water a Garden](https://leetcode.com/problems/minimum-number-of-taps-to-open-to-water-a-garden/)** · Hard
**Pattern:** Intervals + Jump Game | **Companies:** Google, Amazon

**Hint:** Convert each tap into the interval it covers, keep the furthest reach per start position, then run the Jump Game II frontier scan. Return −1 if a gap is left uncovered.

---

### H4 · Couples Holding Hands

**🔗 [LC 765 — Couples Holding Hands](https://leetcode.com/problems/couples-holding-hands/)** · Hard
**Pattern:** Greedy Swap + Union-Find | **Companies:** Google, Amazon

**Hint:** Walk the row two seats at a time and swap whoever is sitting next to the wrong partner into place. Each swap fixes one couple, and the count is minimal — Union-Find gives the same answer as `n − components`.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — sort, then take items greedily

// Snippet 2 — Jump Game: track the furthest reachable index

// Snippet 3 — assign cookies: sort both lists, two pointers

// Snippet 4 — greedy with a heap ("regret": undo the worst choice so far)

// Snippet 5 — check a greedy by trying every choice (brute force), n ≤ 20

// Snippet 6 — gas station: one pass tracking the running tank
```

**Complexity Answers:**

1. **O(n log n)**.
2. **O(n)**.
3. **O(n log n + m log m)**.
4. **O(n log n)**.
5. **O(2ⁿ · n)** — only for testing the greedy.
6. **O(n)**.

---

## 🔍 Self-Assessment — True / False

1. A greedy algorithm always finds the best answer. → **False** — only when the problem has the greedy-choice property
2. A single counterexample is enough to prove a greedy wrong. → **True**
3. Most greedy solutions start by sorting. → **True** — the order is what makes the local choice safe
4. 0/1 knapsack can be solved greedily by value per weight. → **False** — that works only for fractional knapsack
5. An exchange argument shows swapping in the greedy choice never makes things worse. → **True** — it is the standard proof
6. If a greedy passes the sample tests, it is correct. → **False** — test it against a brute force on small inputs

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The two properties:** State the greedy choice property and optimal substructure. Which one does coin change with {1, 3, 4} violate?
2. **Exchange argument:** Give the argument for "sort by end time" in interval scheduling, in three sentences.
3. **Breaking a rule:** Build a five-element input where "always take the largest" loses. What does your counter-example suggest instead?
4. **Greedy vs DP:** Fractional knapsack is greedy, 0/1 knapsack is not. What exactly changes?
5. **Regret:** In Course Schedule III, why is dropping the longest course taken so far always safe?
6. **Feasibility:** Gas Station needs a global check before the greedy scan. Why can the scan not detect impossibility by itself?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Minimum Cost of Buying Candies With Discount](https://leetcode.com/problems/minimum-cost-of-buying-candies-with-discount/), [Couples Holding Hands](https://leetcode.com/problems/couples-holding-hands/), [Minimum Number of Refueling Stops](https://leetcode.com/problems/minimum-number-of-refueling-stops/), [Minimum Number of Taps to Open to Water a Garden](https://leetcode.com/problems/minimum-number-of-taps-to-open-to-water-a-garden/) |
| **Google**    | [Broken Calculator](https://leetcode.com/problems/broken-calculator/), [Hand of Straights](https://leetcode.com/problems/hand-of-straights/), [Monotone Increasing Digits](https://leetcode.com/problems/monotone-increasing-digits/), [Most Profit Assigning Work](https://leetcode.com/problems/most-profit-assigning-work/)                                                                                                                         |
| **Meta**      | [Course Schedule III](https://leetcode.com/problems/course-schedule-iii/), [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/), [Boats to Save People](https://leetcode.com/problems/boats-to-save-people/), [Jump Game II](https://leetcode.com/problems/jump-game-ii/)                                                                                                                           |
| **Microsoft** | [Split a String in Balanced Strings](https://leetcode.com/problems/split-a-string-in-balanced-strings/), [Gas Station](https://leetcode.com/problems/gas-station/)                                                                                                                                                                                                                                                                                     |
| **Adobe**     | [Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)                                                                                                                                                                                                                                                                                                                                                                                  |

---

## ✅ Completion Checklist

- [ ] All 8 Easy problems solved
- [ ] All 13 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can sketch an exchange argument for any greedy rule I propose
- [ ] I can name the three greedy shapes and give a problem for each

---

**← [Lecture 28 · Intervals & Sweep Line](../Lecture28/Assignment.md)** &nbsp;·&nbsp; **[Lecture 30 · Divide & Conquer](../Lecture30/Assignment.md) →**
