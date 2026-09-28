# 🧭 Assignment 2 — Attacking an Unseen Problem

> **Lecture:** 2 of 45 — Attacking an Unseen Problem
> **Phase:** 1 — Foundations
> **Estimated Time:** 3 days · **Total Problems:** 15 (4 Easy · 11 Medium · 0 Hard)
> **Goal:** Get from a blank page to a correct solution with a repeatable routine, then improve it by finding the work it repeats.
> **No Java yet:** work every problem on paper through Steps 1–4. Code them after Lecture 4.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                                   | Pattern                    | Move                                 |
| ------------------------------------------------------- | -------------------------- | ------------------------------------ |
| The examples are small and you can do them in your head | Solve by hand first        | Watch what your hand does            |
| The answer is a single number with a clean pattern      | Look at the answer's shape | Suspect a formula                    |
| n is small (≤ 100)                                      | Brute force is fine        | Say so, and write it                 |
| Building the full object explodes in size               | Work backwards             | Ask where the answer came from       |
| A choice looks locally obvious                          | Greedy, found by hand      | Try to break it with a small example |
| Many rules, ties and special cases                      | Understand carefully       | Write the tricky examples first      |
| A picture makes it obvious                              | Draw it                    | Boxes, arrows, grids                 |

---

## 🟢 Easy Tier (4 Problems)

_Warm-ups for the routine. Even when the answer is obvious, write all six steps down — the habit matters more than these problems._

### E1 · Maximum Nesting Depth of the Parentheses

**🔗 [LC 1614 — Maximum Nesting Depth of the Parentheses](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)** · Easy
**Pattern:** Running counter | **Companies:** Amazon, Google

**Hint:** Solve the example by hand first, and notice what you kept track of. That tracker is the whole algorithm.

---

### E2 · Count Equal and Divisible Pairs in an Array

**🔗 [LC 2176 — Count Equal and Divisible Pairs in an Array](https://leetcode.com/problems/count-equal-and-divisible-pairs-in-an-array/)** · Easy
**Pattern:** Brute force is the answer | **Companies:** Amazon

**Hint:** n ≤ 100, so every pair is at most 4,950 checks. State that, then write the brute force with confidence.

---

### E3 · Largest Odd Number in String

**🔗 [LC 1903 — Largest Odd Number in String](https://leetcode.com/problems/largest-odd-number-in-string/)** · Easy
**Pattern:** Look at the answer's shape | **Companies:** Amazon, Google

**Hint:** An odd number ends in an odd digit. The largest odd prefix-substring must end at the rightmost odd digit — find it and stop.

---

### E4 · Maximum 69 Number

**🔗 [LC 1323 — Maximum 69 Number](https://leetcode.com/problems/maximum-69-number/)** · Easy
**Pattern:** Solve it by hand | **Companies:** Amazon

**Hint:** Try every single change on 9669 by hand. Which change always makes the number biggest?

---

## 🟡 Medium Tier (11 Problems)

_Each of these is cracked by one of the moves in this lecture rather than by a data structure: solving by hand, drawing, working backwards, or making the problem easier. Name the move that worked._

### M1 · Partitioning Into Minimum Number Of Deci-Binary Numbers

**🔗 [LC 1689 — Partitioning Into Minimum Number Of Deci-Binary Numbers](https://leetcode.com/problems/partitioning-into-minimum-number-of-deci-binary-numbers/)** · Medium
**Pattern:** Answer from the digits | **Companies:** Amazon, Google

**Hint:** Break 32 and 82734 into deci-binary numbers by hand. What limits how few you need?

---

### M2 · Maximum Number of Coins You Can Get

**🔗 [LC 1561 — Maximum Number of Coins You Can Get](https://leetcode.com/problems/maximum-number-of-coins-you-can-get/)** · Medium
**Pattern:** Small examples → greedy | **Companies:** Amazon, Google

**Hint:** Try all groupings of six piles by hand. Who should always get the smallest piles?

---

### M3 · Number of Laser Beams in a Bank

**🔗 [LC 2125 — Number of Laser Beams in a Bank](https://leetcode.com/problems/number-of-laser-beams-in-a-bank/)** · Medium
**Pattern:** Draw it | **Companies:** Amazon

**Hint:** Draw the grid and the beams. Only consecutive non-empty rows connect, and each pair contributes a × b.

---

### M4 · Partition Array Such That Maximum Difference Is K

**🔗 [LC 2294 — Partition Array Such That Maximum Difference Is K](https://leetcode.com/problems/partition-array-such-that-maximum-difference-is-k/)** · Medium
**Pattern:** Sort, then look for the rule | **Companies:** Amazon, Google

**Hint:** After sorting, can a group ever usefully skip a number? Start a new group only when the gap from the group's smallest exceeds k.

---

### M5 · Construct K Palindrome Strings

**🔗 [LC 1400 — Construct K Palindrome Strings](https://leetcode.com/problems/construct-k-palindrome-strings/)** · Medium
**Pattern:** Make the problem easier | **Companies:** Google, Amazon

**Hint:** Forget k at first: what stops a string being rearranged into ONE palindrome? Count letters with an odd count.

---

### M6 · Maximum Length of Subarray With Positive Product

**🔗 [LC 1567 — Maximum Length of Subarray With Positive Product](https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/)** · Medium
**Pattern:** Brute force, then track signs | **Companies:** Amazon, Google

**Hint:** Brute force every subarray: O(n²). A product's sign only depends on how many negatives — and a zero resets everything.

---

### M7 · Find Valid Matrix Given Row and Column Sums

**🔗 [LC 1605 — Find Valid Matrix Given Row and Column Sums](https://leetcode.com/problems/find-valid-matrix-given-row-and-column-sums/)** · Medium
**Pattern:** Greedy found by hand | **Companies:** Google, Amazon

**Hint:** Fill cell (0,0) with the most it can hold: min(row sum, column sum). Subtract and repeat. Why can that never go wrong?

---

### M8 · Reward Top K Students

**🔗 [LC 2512 — Reward Top K Students](https://leetcode.com/problems/reward-top-k-students/)** · Medium
**Pattern:** Understand the spec | **Companies:** Amazon, Google

**Hint:** This is mostly Step 1: careful scoring, ties broken by ID. Write two tricky tie examples before you design anything.

---

### M9 · Find Kth Bit in Nth Binary String

**🔗 [LC 1545 — Find Kth Bit in Nth Binary String](https://leetcode.com/problems/find-kth-bit-in-nth-binary-string/)** · Medium
**Pattern:** Work backwards | **Companies:** Google, Amazon

**Hint:** Building the whole string doubles its length each step — up to 2²⁰. Instead ask: which half is bit k in, and what was it before the flip?

---

### M10 · Minimum Lines to Represent a Line Chart

**🔗 [LC 2280 — Minimum Lines to Represent a Line Chart](https://leetcode.com/problems/minimum-lines-to-represent-a-line-chart/)** · Medium
**Pattern:** Edge cases decide it | **Companies:** Amazon

**Hint:** Sort by day, then compare slopes — but slopes as fractions, never as decimals, or precision loss will fool you.

---

### M11 · Make Number of Distinct Characters Equal

**🔗 [LC 2531 — Make Number of Distinct Characters Equal](https://leetcode.com/problems/make-number-of-distinct-characters-equal/)** · Medium
**Pattern:** Size it up first | **Companies:** Google, Amazon

**Hint:** Only 26 letters. Trying every pair of letters to swap is 26 × 26 — tiny, whatever the string length.

---

## 🔴 Hard Tier (0 Problems)

_No Hard problems here — the goal is the routine itself, and it is best learned on problems where the thinking, not the technique, is the hard part._

## 📊 Complexity Analysis Exercises

These are not code snippets — they are situations. For each, give the brute force's Big-O and decide whether it fits the constraint.

```pseudocode
// For each problem below, write the brute force in one sentence,
// then its Big-O, then say whether it fits the constraint.

// Snippet 1 — count pairs with a property, n ≤ 100
// Snippet 2 — count pairs with a property, n ≤ 100,000
// Snippet 3 — try every subset of the input, n ≤ 20
// Snippet 4 — try every subset of the input, n ≤ 60
// Snippet 5 — for each item, scan the whole list for a partner, n ≤ 10,000
// Snippet 6 — sort, then one pass, n ≤ 1,000,000
// Snippet 7 — build a string that doubles in length 20 times
```

**Complexity Answers:**

1. **O(n²)** — about 5,000 checks. Fits easily; brute force is the answer.
2. **O(n²)** — 5 × 10⁹ checks. Too slow; look for O(n log n) or O(n).
3. **O(2ⁿ)** — about a million subsets. Fits.
4. **O(2ⁿ)** — 10¹⁸ subsets. Hopeless; the problem must have more structure.
5. **O(n²)** — 10⁸ steps. Borderline; about a second. Worth improving if you can.
6. **O(n log n)** — about 2 × 10⁷ steps. Comfortable.
7. **O(2²⁰)** characters — a million. Survivable here, but it is a warning: work backwards instead of building it.

---

## 🔍 Self-Assessment — True / False

1. A brute force is a waste of time in an interview if you know it is too slow. → **False** — it proves you understood the problem and gives a baseline to improve
2. Restating the problem in your own words is mostly for the interviewer's benefit. → **False** — it is how you catch the misunderstandings that cause wrong answers
3. If n ≤ 100, an O(n²) solution is fine. → **True** — 10,000 steps is instant
4. The examples in a problem statement cover the tricky cases. → **False** — they are usually friendly; you must invent the awkward ones
5. Staying silent while you think looks more confident in an interview. → **False** — the interviewer grades your reasoning, and cannot hear it
6. The bottleneck is usually the part of the brute force that repeats work. → **True** — finding it is Step 4
7. Every Medium problem needs a data structure you have not learned yet. → **False** — several in this assignment are solved by reasoning alone

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **The six steps**: List them in order and say, for each, what goes wrong if you skip it.
2. **Brute force first**: Give three reasons to state a brute force even when you know it is too slow.
3. **Bottleneck**: For the pair-sum brute force, state the bottleneck in one sentence and say what would remove it.
4. **Stuck moves**: Name four things you can do when you cannot see how to start, and give an example of each from this lecture.
5. **Clarifying questions**: List five questions to ask about an input before designing anything.
6. **Talking**: What should you say out loud in the first two minutes of an interview problem?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company    | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon** | [Minimum Lines to Represent a Line Chart](https://leetcode.com/problems/minimum-lines-to-represent-a-line-chart/), [Number of Laser Beams in a Bank](https://leetcode.com/problems/number-of-laser-beams-in-a-bank/), [Count Equal and Divisible Pairs in an Array](https://leetcode.com/problems/count-equal-and-divisible-pairs-in-an-array/), [Maximum 69 Number](https://leetcode.com/problems/maximum-69-number/)                                 |
| **Google** | [Construct K Palindrome Strings](https://leetcode.com/problems/construct-k-palindrome-strings/), [Find Kth Bit in Nth Binary String](https://leetcode.com/problems/find-kth-bit-in-nth-binary-string/), [Find Valid Matrix Given Row and Column Sums](https://leetcode.com/problems/find-valid-matrix-given-row-and-column-sums/), [Make Number of Distinct Characters Equal](https://leetcode.com/problems/make-number-of-distinct-characters-equal/) |

---

## ✅ Completion Checklist

- [ ] All 4 Easy problems solved
- [ ] All 11 Medium problems solved
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I worked every problem through Steps 1–4 on paper before looking at the hints
- [ ] I can name which "stuck" move cracked each of the Medium problems
- [ ] I have come back after Lecture 4 and coded at least five of these

---

**← [Lecture 1 · How Fast Is It? — Complexity Analysis](../Lecture1/Assignment.md)** &nbsp;·&nbsp; **[Lecture 3 · Testing & Debugging Your Own Code](../Lecture3/Assignment.md) →**
