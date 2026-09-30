# ⏱️ Assignment 44 — Company Pattern Drills

> **Lecture:** 44 of 45 — Company Pattern Drills
> **Phase:** 6 — Interview Mastery
> **Estimated Time:** 8 days · **Total Problems:** 40 (10 Easy · 20 Medium · 10 Hard)
> **Goal:** Solve problems you have never seen, under a clock, naming the pattern within two minutes — and keep a log that tells you what to practise next.

---

## 🗺️ Pattern Recognition — Read Before Starting

This assignment is different: the problems are **not** grouped by topic, on purpose. Before each one, spend at most two minutes on triage, then start the timer:

| Read this first               | It tells you                  | Example                                                    |
| ----------------------------- | ----------------------------- | ---------------------------------------------------------- |
| The size limit                | The complexity you need       | n ≤ 10⁵ → O(n log n) or better; n ≤ 20 → 2ⁿ is fine        |
| The input shape               | The family of patterns        | Grid → BFS / DFS; tree → recursion; string pairs → DP      |
| The question word             | The technique                 | "minimum steps" → BFS; "how many ways" → DP; "k-th" → heap |
| Anything sorted or monotonic  | Binary search or two pointers | "Sorted array", "answer grows with x"                      |
| "Valid", "balanced", "nested" | A stack                       | Parentheses, calculators, paths                            |
| Updates between queries       | A design with two structures  | Lecture 43                                                 |

**Timing rules:** Easy 15 minutes · Medium 25 minutes · Hard 40 minutes. When the timer ends, stop, read one hint, give yourself 10 more minutes, then study the solution. Log every attempt.

---

## 🟢 Easy Tier (10 Problems)

_Warm-ups for the timed rounds. Aim for a correct first submission in under 15 minutes each._

### E1 · Length of Last Word

**🔗 [LC 58 — Length of Last Word](https://leetcode.com/problems/length-of-last-word/)** · Easy
**Pattern:** Scan from the end | **Companies:** Apple, Microsoft

**Hint:** Skip trailing spaces from the right, then count characters until the next space or the start.

---

### E2 · Add Binary

**🔗 [LC 67 — Add Binary](https://leetcode.com/problems/add-binary/)** · Easy
**Pattern:** Digit-by-digit addition with carry | **Companies:** Meta, Google

**Hint:** Walk both strings from the right with a carry, exactly like column addition; append digits and reverse at the end. Do not convert to an integer — the strings can be 10⁴ digits long.

---

### E3 · Sqrt(x)

**🔗 [LC 69 — Sqrt(x)](https://leetcode.com/problems/sqrtx/)** · Easy
**Pattern:** Binary search on the answer | **Companies:** Amazon, Microsoft, Apple

**Hint:** Find the largest m with m · m ≤ x. Compute m · m in long, or compare m ≤ x / m, to avoid overflow.

---

### E4 · First Bad Version

**🔗 [LC 278 — First Bad Version](https://leetcode.com/problems/first-bad-version/)** · Easy
**Pattern:** Binary search for the first true | **Companies:** Meta, Microsoft

**Hint:** Versions go good, good, …, bad, bad. Keep lo &lt; hi; if mid is bad the answer is ≤ mid, else it is > mid. Write mid = lo + (hi − lo) / 2.

---

### E5 · Reverse Vowels of a String

**🔗 [LC 345 — Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)** · Easy
**Pattern:** Two pointers | **Companies:** Google

**Hint:** Move a left pointer and a right pointer inwards, each skipping non-vowels; swap when both sit on vowels. Remember uppercase vowels.

---

### E6 · Intersection of Two Arrays II

**🔗 [LC 350 — Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)** · Easy
**Pattern:** Frequency map | **Companies:** Meta, Amazon

**Hint:** Count the smaller array, then walk the other and take a value whenever its count is positive. Be ready for the follow-up: if both arrays are sorted, two pointers need no extra space.

---

### E7 · Degree of an Array

**🔗 [LC 697 — Degree of an Array](https://leetcode.com/problems/degree-of-an-array/)** · Easy
**Pattern:** Map of count, first and last index | **Companies:** Google

**Hint:** For each value record its count, first index and last index in one pass. Among the values with the highest count, the answer is the smallest last − first + 1.

---

### E8 · Toeplitz Matrix

**🔗 [LC 766 — Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix/)** · Easy
**Pattern:** Compare with the top-left neighbour | **Companies:** Google, Meta

**Hint:** Every cell outside the first row and column must equal the cell up and to its left. Follow-up: that check needs only the previous row, so the matrix can be streamed.

---

### E9 · Most Common Word

**🔗 [LC 819 — Most Common Word](https://leetcode.com/problems/most-common-word/)** · Easy
**Pattern:** Normalise, then count | **Companies:** Amazon

**Hint:** Replace punctuation with spaces, lower-case everything, split, and count words not in the banned set.

---

### E10 · Valid Mountain Array

**🔗 [LC 941 — Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array/)** · Easy
**Pattern:** Walk up, then walk down | **Companies:** Google

**Hint:** Climb while strictly increasing, then descend while strictly decreasing. Valid only if the peak is neither the first nor the last index and you reach the end.

---

## 🟡 Medium Tier (20 Problems)

_The heart of every interview loop. Treat each one as a 25-minute round: two minutes of triage, then say the brute force out loud before improving it._

### M1 · Simplify Path

**🔗 [LC 71 — Simplify Path](https://leetcode.com/problems/simplify-path/)** · Medium
**Pattern:** Stack of directory names | **Companies:** Meta, Microsoft

**Hint:** Split on "/". Skip empty parts and ".", pop on "..", push anything else. Join the stack with "/" and put one "/" in front.

---

### M2 · Sum Root to Leaf Numbers

**🔗 [LC 129 — Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)** · Medium
**Pattern:** DFS carrying a value down | **Companies:** Meta, Amazon

**Hint:** Pass the number built so far: child value = current · 10 + node.val. Add it to the total only at a leaf.

---

### M3 · Reverse Words in a String

**🔗 [LC 151 — Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)** · Medium
**Pattern:** Split and reverse, or reverse twice | **Companies:** Microsoft, Apple

**Hint:** Split on runs of spaces, reverse the list, join with single spaces. For the in-place follow-up: reverse the whole string, then reverse each word.

---

### M4 · Basic Calculator II

**🔗 [LC 227 — Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/)** · Medium
**Pattern:** Stack of signed terms | **Companies:** Meta, Amazon, Microsoft

**Hint:** Keep the previous operator. On + or − push ±number; on \* or / combine with the top of the stack straight away. The answer is the sum of the stack.

---

### M5 · Diagonal Traverse

**🔗 [LC 498 — Diagonal Traverse](https://leetcode.com/problems/diagonal-traverse/)** · Medium
**Pattern:** Group by r + c | **Companies:** Meta, Google

**Hint:** Every cell on one diagonal has the same r + c. Collect each diagonal top to bottom, and reverse the ones with an even index.

---

### M6 · Random Pick with Weight

**🔗 [LC 528 — Random Pick with Weight](https://leetcode.com/problems/random-pick-with-weight/)** · Medium
**Pattern:** Prefix sums + binary search | **Companies:** Meta, Google

**Hint:** Build prefix sums of the weights. Pick a random number from 1 to the total and binary-search for the first prefix sum that is at least that number.

---

### M7 · Find Duplicate Subtrees

**🔗 [LC 652 — Find Duplicate Subtrees](https://leetcode.com/problems/find-duplicate-subtrees/)** · Medium
**Pattern:** Serialise every subtree | **Companies:** Google, Amazon

**Hint:** Post-order, build a string such as "left,val,right" for each subtree, with a marker for null. Count the strings in a map; report a node the moment its string's count becomes 2.

---

### M8 · Find K Closest Elements

**🔗 [LC 658 — Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/)** · Medium
**Pattern:** Binary search for a window start | **Companies:** Meta, Amazon

**Hint:** The answer is a window of k consecutive elements. Binary-search its left end: if x − arr[mid] > arr[mid + k] − x, the window must move right.

---

### M9 · Maximum Swap

**🔗 [LC 670 — Maximum Swap](https://leetcode.com/problems/maximum-swap/)** · Medium
**Pattern:** Greedy with last positions | **Companies:** Meta

**Hint:** Record the last index of each digit 0–9. Scan from the left; for the first digit that has a bigger digit somewhere later, swap it with the last occurrence of the biggest such digit.

---

### M10 · Car Fleet

**🔗 [LC 853 — Car Fleet](https://leetcode.com/problems/car-fleet/)** · Medium
**Pattern:** Sort by position, compare arrival times | **Companies:** Google

**Hint:** Sort cars from closest to the target to furthest. A car that would arrive no later than the fleet ahead catches it; otherwise it starts a new fleet.

---

### M11 · Snakes and Ladders

**🔗 [LC 909 — Snakes and Ladders](https://leetcode.com/problems/snakes-and-ladders/)** · Medium
**Pattern:** BFS on squares | **Companies:** Amazon, Meta

**Hint:** BFS from square 1; each roll reaches the next six squares, following a snake or ladder if there is one. The tricky part is converting a square number to (row, column) on the boustrophedon board.

---

### M12 · Validate Stack Sequences

**🔗 [LC 946 — Validate Stack Sequences](https://leetcode.com/problems/validate-stack-sequences/)** · Medium
**Pattern:** Simulate the stack | **Companies:** Amazon, Google

**Hint:** Push each element; then, while the top equals the next value to pop, pop it. The sequences are valid if the stack ends empty.

---

### M13 · Number of Enclaves

**🔗 [LC 1020 — Number of Enclaves](https://leetcode.com/problems/number-of-enclaves/)** · Medium
**Pattern:** Flood fill from the border | **Companies:** Google, Amazon

**Hint:** Sink every land cell reachable from the border first. Whatever land is left cannot walk off the grid — count it.

---

### M14 · Two City Scheduling

**🔗 [LC 1029 — Two City Scheduling](https://leetcode.com/problems/two-city-scheduling/)** · Medium
**Pattern:** Greedy by the difference | **Companies:** Bloomberg, Google

**Hint:** Sort people by costA − costB. Send the first half (who save most by going to A) to A and the rest to B.

---

### M15 · Longest String Chain

**🔗 [LC 1048 — Longest String Chain](https://leetcode.com/problems/longest-string-chain/)** · Medium
**Pattern:** DP over words sorted by length | **Companies:** Google

**Hint:** Process words from shortest to longest. For each word, try deleting each character; dp[word] = 1 + the best dp of any predecessor found in the map.

---

### M16 · Minimum Remove to Make Valid Parentheses

**🔗 [LC 1249 — Minimum Remove to Make Valid Parentheses](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/)** · Medium
**Pattern:** Stack of unmatched indices | **Companies:** Meta, Amazon

**Hint:** Push the index of every "("; pop it when a ")" matches. A ")" with nothing to match is removed, and so is every "(" still on the stack at the end.

---

### M17 · Jump Game III

**🔗 [LC 1306 — Jump Game III](https://leetcode.com/problems/jump-game-iii/)** · Medium
**Pattern:** BFS / DFS on indices | **Companies:** Microsoft, Amazon

**Hint:** From i you may go to i + arr[i] or i − arr[i]. Search from start with a visited set; succeed on reaching any index holding 0.

---

### M18 · Time Needed to Inform All Employees

**🔗 [LC 1376 — Time Needed to Inform All Employees](https://leetcode.com/problems/time-needed-to-inform-all-employees/)** · Medium
**Pattern:** Longest root-to-leaf path | **Companies:** Google, Amazon

**Hint:** Build children lists from the manager array. The answer is the maximum, over all paths from the head, of the sum of informTime along the path.

---

### M19 · Minimum Deletions to Make Character Frequencies Unique

**🔗 [LC 1647 — Minimum Deletions to Make Character Frequencies Unique](https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique/)** · Medium
**Pattern:** Greedy with a used set | **Companies:** Microsoft

**Hint:** For each letter's count, while that count is already taken by another letter and above 0, delete one more. Record the final count as taken.

---

### M20 · Amount of Time for Binary Tree to Be Infected

**🔗 [LC 2385 — Amount of Time for Binary Tree to Be Infected](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/)** · Medium
**Pattern:** Tree → graph, then BFS | **Companies:** Amazon, Google

**Hint:** Record each node's parent (or build an adjacency list), then BFS from the start node in all three directions. The number of BFS levels minus one is the answer.

---

## 🔴 Hard Tier (10 Problems)

_Forty-minute rounds. A brute force that you can explain earns credit; aim to reach the optimal idea, even if the code is not finished._

### H1 · Longest Valid Parentheses

**🔗 [LC 32 — Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)** · Hard
**Pattern:** Stack of indices with a base | **Companies:** Amazon, Meta

**Hint:** Start the stack with −1 as a base. Push the index of "("; on ")", pop; if the stack is now empty, push this index as the new base, else the valid length is i − stack.top.

---

### H2 · Wildcard Matching

**🔗 [LC 44 — Wildcard Matching](https://leetcode.com/problems/wildcard-matching/)** · Hard
**Pattern:** 2-D string DP | **Companies:** Google, Meta

**Hint:** dp`[i][j]`: does s[0..i) match p[0..j)? A "\*" matches empty (dp`[i][j − 1]`) or one more character (dp`[i − 1][j]`); "?" or an equal letter moves both.

---

### H3 · Best Time to Buy and Sell Stock III

**🔗 [LC 123 — Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)** · Hard
**Pattern:** Four-state DP | **Companies:** Amazon, Google

**Hint:** Track the best money after buy1, sell1, buy2 and sell2, updating all four from each price. sell2 is the answer.

---

### H4 · Integer to English Words

**🔗 [LC 273 — Integer to English Words](https://leetcode.com/problems/integer-to-english-words/)** · Hard
**Pattern:** Chunks of three digits | **Companies:** Meta, Amazon, Microsoft

**Hint:** Write a helper for 1–999, then apply it to each group of three digits with "Thousand", "Million" or "Billion" after it. Handle 0 separately and never emit double spaces.

---

### H5 · Remove Invalid Parentheses

**🔗 [LC 301 — Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/)** · Hard
**Pattern:** BFS by number of removals | **Companies:** Meta

**Hint:** BFS where each level removes one more parenthesis. The first level that contains a valid string is the minimum; collect every valid string on it, with a set to skip duplicates.

---

### H6 · Sliding Puzzle

**🔗 [LC 773 — Sliding Puzzle](https://leetcode.com/problems/sliding-puzzle/)** · Hard
**Pattern:** BFS over board states | **Companies:** Google, Amazon

**Hint:** Encode the 2 × 3 board as a six-character string. BFS by swapping 0 with its neighbours; there are only 720 states.

---

### H7 · Making A Large Island

**🔗 [LC 827 — Making A Large Island](https://leetcode.com/problems/making-a-large-island/)** · Hard
**Pattern:** Label islands, then try each water cell | **Companies:** Google, Meta

**Hint:** Give each island an id and record its size. For every water cell, add 1 to the sizes of the _distinct_ islands around it.

---

### H8 · Minimum Cost to Hire K Workers

**🔗 [LC 857 — Minimum Cost to Hire K Workers](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/)** · Hard
**Pattern:** Sort by ratio + max-heap of quality | **Companies:** Google

**Hint:** A group is paid at its highest wage/quality ratio times its total quality. Sort by ratio; for each worker as the "captain", keep the k smallest qualities seen so far in a max-heap.

---

### H9 · Minimum Difficulty of a Job Schedule

**🔗 [LC 1335 — Minimum Difficulty of a Job Schedule](https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/)** · Hard
**Pattern:** Partition DP | **Companies:** Amazon

**Hint:** dp`[k][i]`ß: the best difficulty for the first i jobs in k days. The last day takes jobs j..i − 1; walk j backwards keeping the running maximum.

---

### H10 · Jump Game IV

**🔗 [LC 1345 — Jump Game IV](https://leetcode.com/problems/jump-game-iv/)** · Hard
**Pattern:** BFS with value groups cleared after use | **Companies:** Amazon, Google

**Hint:** BFS over indices; neighbours are i ± 1 and every index with the same value. After visiting a value's group once, clear its list — otherwise the same group is scanned again and again.

---

## 📊 Complexity Analysis Exercises

For each size limit, write the fastest growth rate that will pass in about one second (roughly 10⁸ simple steps) before checking the answers.

```pseudocode
// Snippet 1 — n ≤ 12

// Snippet 2 — n ≤ 20

// Snippet 3 — n ≤ 500

// Snippet 4 — n ≤ 5000

// Snippet 5 — n ≤ 2 · 10⁵

// Snippet 6 — n ≤ 10⁹ (or 10¹⁸)
```

**Complexity Answers:**

1. **O(n!)** — permutations are affordable.
2. **O(2ⁿ · n)** — subsets / bitmask DP.
3. **O(n³)** — interval DP, Floyd-Warshall.
4. **O(n²)** — pairwise DP.
5. **O(n log n)** — sorting, heaps, binary search, or O(n).
6. **O(log n)** or **O(1)** — binary search on the answer, fast power, a formula.

---

## 🔍 Self-Assessment — True / False

1. Reading the constraints before the examples can tell you the intended complexity. → **True**
2. If you cannot see the optimal solution, it is best to stay silent until you do. → **False** — state and code the brute force; it earns credit and often reveals the waste
3. Re-solving a problem you failed is worth more than reading three new solutions. → **True**
4. Solving 300 problems once beats solving 150 twice with spaced repetition. → **False** — recall, not exposure, is what interviews test
5. A problem log only needs the problems you failed. → **False** — slow solves and solves that needed a hint matter too
6. Every company asks the same mix of topics. → **False** — tendencies differ, which is why you drill company sets

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Triage**: Walk through your two-minute triage for "Snakes and Ladders" using only its constraints and question.
2. **Timing**: How would you split a 45-minute interview between clarifying, planning, coding and testing?
3. **Stuck**: What do you do and say when you have been stuck for five minutes?
4. **Log**: What columns does your problem log have, and which one decides what you practise next week?
5. **Spacing**: Why re-solve after 1, 7 and 30 days rather than three times on the same day?
6. **Cheat sheet**: Which five templates on your one-page sheet would you most hate to forget?

---

## 🏢 Company Focus

Use these as the timed sets for Days 2–5 of the lecture. Each row is one company's set: do them as two rounds of four, 90 minutes per round, no hints.

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | [Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix/), [Car Fleet](https://leetcode.com/problems/car-fleet/), [Longest String Chain](https://leetcode.com/problems/longest-string-chain/), [Find Duplicate Subtrees](https://leetcode.com/problems/find-duplicate-subtrees/), [Number of Enclaves](https://leetcode.com/problems/number-of-enclaves/), [Wildcard Matching](https://leetcode.com/problems/wildcard-matching/), [Sliding Puzzle](https://leetcode.com/problems/sliding-puzzle/), [Minimum Cost to Hire K Workers](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/)                                                                                                                                                       |
| **Amazon**    | [Most Common Word](https://leetcode.com/problems/most-common-word/), [Snakes and Ladders](https://leetcode.com/problems/snakes-and-ladders/), [Validate Stack Sequences](https://leetcode.com/problems/validate-stack-sequences/), [Amount of Time for Binary Tree to Be Infected](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/), [Time Needed to Inform All Employees](https://leetcode.com/problems/time-needed-to-inform-all-employees/), [Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/), [Minimum Difficulty of a Job Schedule](https://leetcode.com/problems/minimum-difficulty-of-a-job-schedule/), [Jump Game IV](https://leetcode.com/problems/jump-game-iv/) |
| **Meta**      | [Add Binary](https://leetcode.com/problems/add-binary/), [Simplify Path](https://leetcode.com/problems/simplify-path/), [Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/), [Minimum Remove to Make Valid Parentheses](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/), [Random Pick with Weight](https://leetcode.com/problems/random-pick-with-weight/), [Maximum Swap](https://leetcode.com/problems/maximum-swap/), [Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/), [Making A Large Island](https://leetcode.com/problems/making-a-large-island/)                                                                                                                   |
| **Microsoft** | [Sqrt(x)](https://leetcode.com/problems/sqrtx/), [First Bad Version](https://leetcode.com/problems/first-bad-version/), [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/), [Jump Game III](https://leetcode.com/problems/jump-game-iii/), [Minimum Deletions to Make Character Frequencies Unique](https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique/), [Integer to English Words](https://leetcode.com/problems/integer-to-english-words/)                                                                                                                                                                                                                                               |
| **Apple**     | [Length of Last Word](https://leetcode.com/problems/length-of-last-word/), [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/), [Sqrt(x)](https://leetcode.com/problems/sqrtx/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **Bloomberg** | [Two City Scheduling](https://leetcode.com/problems/two-city-scheduling/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

---

## ✅ Completion Checklist

- [ ] All 10 Easy problems solved, each in under 15 minutes
- [ ] All 20 Medium problems attempted under the 25-minute timer
- [ ] All 10 Hard problems attempted under the 40-minute timer
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] Every attempt is in my problem log, with pattern, time and outcome
- [ ] My one-page cheat sheet is written and fits on one page

---

**← [Lecture 43 · Design Data Structures](../Lecture43/Assignment.md)** &nbsp;·&nbsp; **[Lecture 45 · Mock Interviews & System Thinking](../Lecture45/Assignment.md) →**
