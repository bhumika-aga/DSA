# 🎲 Assignment 42 — Advanced Math & Game Theory

> **Lecture:** 42 of 45 — Advanced Math & Game Theory
> **Phase:** 5 — Advanced Structures & Algorithms
> **Estimated Time:** 4 days · **Total Problems:** 18 (4 Easy · 9 Medium · 5 Hard)
> **Goal:** Count without listing, compute huge terms of a recurrence quickly, reason about chance with expected values, and decide who wins a game before it is played.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                       | Pattern                     | Move                                                |
| ----------------------------------------------------------- | --------------------------- | --------------------------------------------------- |
| n up to 10⁹ (or 10¹⁸) and each term depends on the last few | Matrix exponentiation       | Write one step as a matrix, raise it to the power n |
| "How many ways", answer modulo 10⁹ + 7, choosing positions  | nCr with factorials         | Precompute factorials and inverse factorials        |
| "Divisible by a **or** b **or** c"                          | Inclusion–exclusion         | Add singles, subtract pairs (lcm), add the triple   |
| "The n-th number such that…" with huge n                    | Binary search on the answer | Count how many are ≤ x, then search x               |
| "Probability", "expected", random draws                     | Probability DP / linearity  | dp over states, or add up indicator expectations    |
| Pick uniformly from a stream of unknown length              | Reservoir sampling          | Keep the i-th item with probability 1 / i           |
| Two players, "both play optimally", "can the first win?"    | Win / lose positions        | A position wins if some move reaches a losing one   |
| Players pick items from a shared pool                       | Greedy by combined value    | Taking an item gains yours **and** denies theirs    |

---

## 🟢 Easy Tier (4 Problems)

_Small ideas that carry the whole lecture: losing positions, counting by multiplication, and inclusion–exclusion._

### E1 · Nim Game

**🔗 [LC 292 — Nim Game](https://leetcode.com/problems/nim-game/)** · Easy
**Pattern:** Losing positions | **Companies:** Adobe, Amazon

**Hint:** Work out who wins for 1 to 8 stones by hand. Every multiple of 4 is a losing position: whatever you take, your opponent restores a multiple of 4.

---

### E2 · Prime Arrangements

**🔗 [LC 1175 — Prime Arrangements](https://leetcode.com/problems/prime-arrangements/)** · Easy
**Pattern:** Multiply independent choices | **Companies:** Amazon

**Hint:** Primes must sit at prime positions and the others elsewhere. The two groups are arranged independently, so the answer is p! · (n − p)! mod 10⁹ + 7, where p counts the primes up to n.

---

### E3 · Find the Winning Player in Coin Game

**🔗 [LC 3222 — Find the Winning Player in Coin Game](https://leetcode.com/problems/find-the-winning-player-in-coin-game/)** · Easy
**Pattern:** A forced game | **Companies:** Amazon

**Hint:** Making 115 needs exactly one 75-coin and four 10-coins, so nobody has a choice. The number of turns is min(x, y / 4); Alice wins when it is odd.

---

### E4 · Sum Multiples

**🔗 [LC 2652 — Sum Multiples](https://leetcode.com/problems/sum-multiples/)** · Easy
**Pattern:** Inclusion–exclusion | **Companies:** Amazon

**Hint:** A loop to n passes, but try it with formulas: the multiples of k up to n add up to k · m(m + 1)/2 with m = n / k. Add k = 3, 5, 7, subtract 15, 21, 35, add back 105.

---

## 🟡 Medium Tier (9 Problems)

_Recurrences, nCr, inclusion–exclusion, probability and two-player games at interview strength._

### M1 · Domino and Tromino Tiling

**🔗 [LC 790 — Domino and Tromino Tiling](https://leetcode.com/problems/domino-and-tromino-tiling/)** · Medium
**Pattern:** Linear recurrence | **Companies:** Google, Amazon

**Hint:** Count small boards by hand to find dp[n] = 2 · dp[n − 1] + dp[n − 3]. A linear recurrence like this is exactly what a matrix power computes for huge n.

---

### M2 · Number of Ways to Reach a Position After Exactly k Steps

**🔗 [LC 2400 — Number of Ways to Reach a Position After Exactly k Steps](https://leetcode.com/problems/number-of-ways-to-reach-a-position-after-exactly-k-steps/)** · Medium
**Pattern:** nCr mod p | **Companies:** Google, Amazon

**Hint:** If r steps go towards the target and k − r away, then r − (k − r) = distance. Solve for r; the answer is C(k, r), or 0 when r is not a whole number or the target is too far.

---

### M3 · Linked List Random Node

**🔗 [LC 382 — Linked List Random Node](https://leetcode.com/problems/linked-list-random-node/)** · Medium
**Pattern:** Reservoir sampling | **Companies:** Google, Meta

**Hint:** Walk the list once. Replace your current pick with the i-th node with probability 1 / i; every node ends up chosen with probability 1 / n.

---

### M4 · Implement Rand10() Using Rand7()

**🔗 [LC 470 — Implement Rand10() Using Rand7()](https://leetcode.com/problems/implement-rand10-using-rand7/)** · Medium
**Pattern:** Rejection sampling | **Companies:** Google, Microsoft

**Hint:** Two calls give a uniform number from 1 to 49: (rand7() − 1) · 7 + rand7(). Keep 1–40 (four copies of 1–10) and throw away 41–49 by trying again.

---

### M5 · Soup Servings

**🔗 [LC 808 — Soup Servings](https://leetcode.com/problems/soup-servings/)** · Medium
**Pattern:** Probability DP | **Companies:** Google

**Hint:** Measure in units of 25 ml and recurse on (a, b) with memoisation, averaging the four outcomes. Soup A runs out faster on average, so for large n the answer is within 10⁻⁵ of 1 — return 1 once n passes about 4800.

---

### M6 · New 21 Game

**🔗 [LC 837 — New 21 Game](https://leetcode.com/problems/new-21-game/)** · Medium
**Pattern:** Probability DP with a sliding window | **Companies:** Google, Amazon

**Hint:** dp[i] is the chance of ever holding exactly i points. It is the sum of dp[j] over the previous maxPts scores that were still drawing (j &lt; k), divided by maxPts — keep that sum as a running window.

---

### M7 · Ugly Number III

**🔗 [LC 1201 — Ugly Number III](https://leetcode.com/problems/ugly-number-iii/)** · Medium
**Pattern:** Inclusion–exclusion + binary search | **Companies:** Amazon, Google

**Hint:** The count of numbers ≤ x divisible by a, b or c is x/a + x/b + x/c − x/lcm(a,b) − x/lcm(b,c) − x/lcm(a,c) + x/lcm(a,b,c). Binary search for the smallest x with count ≥ n.

---

### M8 · Stone Game VI

**🔗 [LC 1686 — Stone Game VI](https://leetcode.com/problems/stone-game-vi/)** · Medium
**Pattern:** Greedy by combined value | **Companies:** Google, Amazon

**Hint:** Taking stone i gains you your value and denies your opponent theirs, so its real worth is aliceValues[i] + bobValues[i]. Both players take stones in decreasing order of that sum.

---

### M9 · Remove Colored Pieces if Both Neighbors are the Same Color

**🔗 [LC 2038 — Remove Colored Pieces if Both Neighbors are the Same Color](https://leetcode.com/problems/remove-colored-pieces-if-both-neighbors-are-the-same-color/)** · Medium
**Pattern:** Count moves; players do not interact | **Companies:** Google, Amazon

**Hint:** Removing an A never creates or destroys a B move, and vice versa. Count each player's moves (the middle of every AAA and every BBB); Alice wins only with strictly more.

---

## 🔴 Hard Tier (5 Problems)

_Matrix powers on real transition tables, counting with products, and a game solved by DP over positions._

### H1 · Count Vowels Permutation

**🔗 [LC 1220 — Count Vowels Permutation](https://leetcode.com/problems/count-vowels-permutation/)** · Hard
**Pattern:** Transition matrix | **Companies:** Amazon, Google

**Hint:** Five states, one per last vowel, and a fixed table of which vowel may follow which. One step is a 5 × 5 matrix; n − 1 steps is its (n − 1)-th power.

---

### H2 · Student Attendance Record II

**🔗 [LC 552 — Student Attendance Record II](https://leetcode.com/problems/student-attendance-record-ii/)** · Hard
**Pattern:** DP over a small state | **Companies:** Google

**Hint:** The state is (absences so far: 0 or 1, current run of lates: 0, 1 or 2) — six states. Each day moves between them; an O(n) DP passes, and a 6 × 6 matrix power would handle any n.

---

### H3 · Total Characters in String After Transformations II

**🔗 [LC 3337 — Total Characters in String After Transformations II](https://leetcode.com/problems/total-characters-in-string-after-transformations-ii/)** · Hard
**Pattern:** 26 × 26 matrix exponentiation | **Companies:** Google, Amazon

**Hint:** Keep a count per letter. One transformation is a fixed linear map on those 26 counts; with t up to 10⁹, raise its matrix to the t-th power and apply it to the starting counts.

---

### H4 · Count All Valid Pickup and Delivery Options

**🔗 [LC 1359 — Count All Valid Pickup and Delivery Options](https://leetcode.com/problems/count-all-valid-pickup-and-delivery-options/)** · Hard
**Pattern:** Count by insertion | **Companies:** Amazon, DoorDash

**Hint:** Add orders one at a time. With i − 1 orders placed there are 2i − 1 gaps; choosing two of them for the new pickup and delivery, in that order, gives i · (2i − 1) ways. Multiply for i = 1 to n.

---

### H5 · Stone Game IV

**🔗 [LC 1510 — Stone Game IV](https://leetcode.com/problems/stone-game-iv/)** · Hard
**Pattern:** Win / lose positions | **Companies:** Amazon, Google

**Hint:** win[i] is true if some square j² ≤ i leaves the opponent in a losing position, win[i − j²] = false. Fill it for i from 0 to n.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — raise a k × k matrix to the power n by repeated squaring

// Snippet 2 — precompute factorials and inverse factorials up to n, then answer q nCr queries

// Snippet 3 — inclusion–exclusion over m divisors (every subset of them)

// Snippet 4 — reservoir sampling over a stream of n items

// Snippet 5 — win/lose DP for Stone Game IV up to n

// Snippet 6 — minimax over every subset of n items (bitmask memo)
```

**Complexity Answers:**

1. **O(k³ log n)** time, O(k²) space.
2. **O(n + q)** — O(n) to precompute (one modular inverse, then work backwards), O(1) per query.
3. **O(2ᵐ)** terms, each needing an lcm.
4. **O(n)** time, **O(1)** space.
5. **O(n √n)**.
6. **O(2ⁿ · n)**.

---

## 🔍 Self-Assessment — True / False

1. Matrix exponentiation computes the n-th Fibonacci number in O(log n) matrix multiplications. → **True**
2. Modulo a prime p, dividing by a is the same as multiplying by a^(p − 2). → **True** — Fermat's little theorem, for a not divisible by p
3. Linearity of expectation needs the random events to be independent. → **False** — it holds for any events, which is why it is so useful
4. In a game with no draws, a position is losing if every move from it leads to a winning position. → **True**
5. The Nim position with piles 3, 5 and 6 is a win for the player to move. → **False** — 3 XOR 5 XOR 6 = 0, a losing position
6. Reservoir sampling needs to know the length of the stream in advance. → **False** — that is the whole point of it

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Matrices**: Write the Fibonacci step as a 2 × 2 matrix. Why does squaring the matrix skip ahead by two steps at a time?
2. **nCr**: Why do you precompute inverse factorials backwards from n! instead of calling a modular inverse for each one?
3. **Inclusion–exclusion**: For "divisible by 4 or 6", why do you subtract numbers divisible by 12 and not by 24?
4. **Expectation**: Explain linearity of expectation with the question "how many people get their own hat back?"
5. **Games**: Define winning and losing positions. Why is 0 stones a losing position in most games?
6. **Nim**: Why does XOR-ing the pile sizes decide the winner, and what is a Grundy number for?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                           |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Google**    | [New 21 Game](https://leetcode.com/problems/new-21-game/), [Soup Servings](https://leetcode.com/problems/soup-servings/), [Student Attendance Record II](https://leetcode.com/problems/student-attendance-record-ii/), [Implement Rand10() Using Rand7()](https://leetcode.com/problems/implement-rand10-using-rand7/)                           |
| **Amazon**    | [Count Vowels Permutation](https://leetcode.com/problems/count-vowels-permutation/), [Count All Valid Pickup and Delivery Options](https://leetcode.com/problems/count-all-valid-pickup-and-delivery-options/), [Ugly Number III](https://leetcode.com/problems/ugly-number-iii/), [Stone Game IV](https://leetcode.com/problems/stone-game-iv/) |
| **Meta**      | [Linked List Random Node](https://leetcode.com/problems/linked-list-random-node/)                                                                                                                                                                                                                                                                |
| **Microsoft** | [Implement Rand10() Using Rand7()](https://leetcode.com/problems/implement-rand10-using-rand7/)                                                                                                                                                                                                                                                  |
| **Adobe**     | [Nim Game](https://leetcode.com/problems/nim-game/)                                                                                                                                                                                                                                                                                              |
| **DoorDash**  | [Count All Valid Pickup and Delivery Options](https://leetcode.com/problems/count-all-valid-pickup-and-delivery-options/)                                                                                                                                                                                                                        |

---

## ✅ Completion Checklist

- [ ] All 4 Easy problems solved
- [ ] All 9 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I wrote matrix fast power and nCr mod p from memory
- [ ] I can label small game positions as winning or losing by hand

---

**← [Lecture 41 · Balanced BSTs & Ordered Structures](../Lecture41/Assignment.md)** &nbsp;·&nbsp; **[Lecture 43 · Design Data Structures](../Lecture43/Assignment.md) →**
